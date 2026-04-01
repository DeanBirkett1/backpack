# Anti-Patterns & Known Defect Patterns — Skyscanner Accessibility

Reference for `a11y-review`. Check every review against this list.

Last reviewed: 2026-03-25 | Applies to: Backpack web components

---

## ARIA Prohibited Patterns

Never do the following:

| Prohibited | Why |
|---|---|
| `role="button"` on `<button>` | Redundant — native role already exists |
| `role="link"` on `<a>` | Redundant — native role already exists |
| `role="heading"` on `<h1>`–`<h6>` | Redundant — native role already exists |
| `role="navigation"` on `<nav>` | Redundant — native role already exists |
| `role="main"` on `<main>` | Redundant — native role already exists |
| `role="banner"` on `<header>` | Redundant — native role already exists |
| `role="contentinfo"` on `<footer>` | Redundant — native role already exists |
| `aria-label` on `<p>`, `<div>`, `<span>`, `<li>` | Invalid on non-interactive, non-landmark elements |
| `role="menu"` on site navigation | Menu pattern is for application menus, not site nav |
| `<section>` without an accessible name | Use `aria-label` or `aria-labelledby` on `<section>` |
| `title` attribute on HTML elements (except `<iframe>`) | Use `aria-label` or visible text instead |
| ARIA reference IDs that don't exist in the output | Broken references are worse than no ARIA |
| `aria-hidden="true"` on a focusable element | Hidden content must not be focusable |

---

## When ARIA Is Appropriate

- `aria-label` on icon-only buttons (no visible text), only if visually-hidden, alt or aria-labelledby has been ruled out
- `aria-label` on landmark regions needing disambiguation (`<nav aria-label="Primary">`)
- `aria-labelledby` to reference visible text as a region or widget label
- `aria-describedby` for hints, errors, supplementary context
- `aria-hidden="true"` on decorative icons and SVGs
- `aria-live` / `role="status"` / `role="alert"` for dynamic content updates
- `aria-expanded` on trigger buttons for disclosed content
- `aria-selected` on selected items in a collection (tabs, date cells, listbox options)
- `aria-pressed` on toggle buttons (persistent on/off state — not for selections)

## aria-label anti-patterns — common misuses

These are frequently seen in reviews. Flag each one.

| Misuse | Problem | Correct approach |
|---|---|---|
| `aria-label` replaces visible text | Breaks WCAG 2.5.3 — speech input users speak what they see; the name won't match | Keep visible text; append `<span class="bpk-visually-hidden">` for context |
| `aria-label` added to augment context on a labelled input | Overrides the `<label>` association entirely | Use `aria-describedby` for supplementary context |
| Two identical `aria-label` values on sibling controls | Non-unique labels — screen reader users can't distinguish them | Make labels unique; add contextual visually-hidden text |
| `aria-label` on a `<div>` or `<span>` with no role | `aria-label` only works on interactive elements and landmarks | Add a role or use a semantic element |
| Dynamic `aria-label` not updated when visible value changes | Accessible name diverges from visible state | Update `aria-label` in JS when the visible value changes |
- `aria-invalid` + `aria-describedby` for form validation errors
- `aria-required="true"` on required form fields
- `aria-busy="true"` on regions being updated
- `role="dialog"` + `aria-modal="true"` + `aria-labelledby` when native `<dialog>` is not used
- `role="grid"` with `aria-selected` for interactive calendar/date grids

---

## `aria-pressed` vs `aria-selected` — Important Distinction

| Attribute | Use for | Example |
|---|---|---|
| `aria-pressed` | Toggle buttons — persistent on/off features | "Bold" button in a text editor, "Mute" button |
| `aria-selected` | Selection within a collection | Tabs, date cells, listbox options, tree items |

**Common Skyscanner mistake:** Using `aria-pressed` on calendar date cells. Date selection is `aria-selected` — dates are selected from a collection, not toggled on/off.

---

## Known Skyscanner Backpack Defect Patterns

Recurring issues found during Skyscanner Backpack audits. Check every review.

| # | Issue | Correct approach |
|---|---|---|
| 1 | Tab interfaces using `role="checkbox"` on tab elements | Use `role="tab"`, `role="tablist"`, `role="tabpanel"` |
| 2 | `aria-pressed` on calendar date cells | Use `aria-selected` — date cells are selections, not toggles |
| 3 | Focus not managed after date selection | Move focus to next logical step (e.g. return date input) |
| 4 | `role="menu"` on site navigation | Use `<nav>` + `<button aria-expanded>` for expandable nav |
| 5 | Redundant landmark roles on native elements | Remove — `<nav>`, `<main>`, `<header>`, `<footer>` carry implicit roles |
| 6 | Static tables rendered with unnecessary JS framework | Use native `<table>` with `<th scope>` for static data |
| 7 | Toggle buttons triggering navigation | Toggle buttons change state only — they must not redirect |
| 8 | Icon buttons with no accessible name | Add `aria-label` that matches the visual intent |
| 9 | Regional settings button with generic announcement | Accessible name must communicate all current values and their labels (e.g. "Regional settings: Language English (UK), Country/region United Kingdom, Currency £ GBP") |
| 10 | Placeholder text used as a label substitute | Placeholder must not replace a visible label — use `<label>` |
| 11 | `list-style: none` on navigation lists | Add `role="list"` to restore semantics in Safari/VoiceOver |
| 12 | Error messages without field name | Always include the field name: "Enter your email address" not "This field is required" |

---

## Placeholder Text — Extended Issues

Placeholder issues extend beyond contrast failures:

- Screen readers handle placeholder inconsistently — some do not announce it
- Voice control users cannot target a field by its placeholder if it differs from the accessible name
- Placeholder disappears on input — creates cognitive load and confusion
- Users may confuse placeholder with pre-filled data
- The HTML Living Standard states placeholders should not substitute for labels
- WCAG 2.2 has no explicit prohibition on redundant placeholders (where both label and placeholder exist), but the label must be present and visible

---

## Composite Widget Focus Management

For components that use arrow-key navigation internally (tabs, listbox, date picker, menu):

**Option 1 — Roving tabindex:**
- Exactly one child has `tabindex="0"`; all others have `tabindex="-1"`
- Arrow keys move focus by updating tabindex values and calling `.focus()`

**Option 2 — `aria-activedescendant`:**
- Container has `tabindex="0"` and `aria-activedescendant="[id of active child]"`
- Arrow keys update `aria-activedescendant`; container retains focus

Both are valid. Roving tabindex is more broadly supported. Choose one and apply consistently within a component.
