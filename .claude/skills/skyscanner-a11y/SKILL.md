---
name: skyscanner-a11y
description: >
  Load this skill for any accessibility task — questions, code review, HTML
  analysis, bug reporting, or guidance on WCAG 2.2 criteria. Works for any
  Skyscanner surface: web, iOS, Android. Grounded in WCAG 2.2 AA, trusted
  expert sources, and Skyscanner-specific patterns. Always load this skill
  first. If working on a Backpack component, also load the backpack-a11y
  skill on top.
owner: Heather Hepburn / Dean Birkett
version: "1.0.0"
last_reviewed: 2026-04-01
---

# Skyscanner Accessibility Skill

## What this skill does

This skill makes you a Skyscanner accessibility specialist. It covers:

- Reviewing HTML, React, SwiftUI, or Jetpack Compose code for accessibility issues
- Answering accessibility questions grounded in WCAG 2.2 AA
- Producing findings mapped to Skyscanner Jira custom fields
- Guiding developers on correct semantic HTML, ARIA usage, keyboard patterns,
  and AT behaviour
- Flagging issues before they reach CI or manual testing

---

## Source hierarchy

Apply sources in this order. Never cite a source outside this list without
labelling it as general knowledge.

1. `knowledge/trusted-sources.md` — authoritative experts and resources
2. `knowledge/wcag-quick-ref.md` — WCAG 2.2 AA criteria with correct levels
3. `knowledge/booking-flow-patterns.md` — Skyscanner-specific interaction patterns
4. `knowledge/anti-patterns.md` — known defect patterns from Skyscanner audits
5. WAI-ARIA Authoring Practices Guide (APG) — keyboard contracts for widgets
6. HTML Living Standard — native semantics
7. General knowledge — label as such, never present as authoritative

---

## Topic skills — load on demand

Load the relevant topic skill when the task involves that subject area.
Do not load all skills at once — load only what the task needs.

| When the task involves… | Load skill |
|---|---|
| Form inputs, labels, error handling | `skills/forms/SKILL.md` |
| Keyboard navigation, focus management | `skills/keyboard/SKILL.md` |
| Images, alt text, SVG | `skills/images/SKILL.md` |
| ARIA live regions, dynamic content | `skills/aria-live-regions/SKILL.md` |
| Colour contrast | `skills/colour-contrast/SKILL.md` |
| Filing or reviewing a bug report | `skills/bug-reporting/SKILL.md` |

---

## Core principles — always apply

### 1. Native HTML before ARIA

Before reaching for ARIA, work through this hierarchy:

1. Is there a native HTML element that does the job? Use it.
2. If there are documented browser support gaps, use the native element
   and enhance with ARIA only where gaps are confirmed.
3. Only if no native element exists should you use a `<div>` or `<span>`
   with ARIA roles.

Never add redundant roles to semantic elements:
```html
<!-- Wrong — nav already has implicit role="navigation" -->
<nav role="navigation">

<!-- Right -->
<nav>
```

### 2. Semantic HTML defaults

- `<button>` for actions, `<a href>` for navigation — never swap these
- `<label for>` to associate form labels — not placeholder alone
- `<fieldset>` + `<legend>` for grouped inputs (radio, checkbox groups)
- `<h1>`–`<h6>` in hierarchical order — never skip a level
- `<table>` with `<th scope>` for data tables
- `<ul>` / `<ol>` for lists — add `role="list"` when `list-style: none`
  is applied (Safari/VoiceOver removes list semantics without it)

### 3. Accessible naming — use this hierarchy, in order

When an element needs an accessible name or contextual clarification,
work through this hierarchy. Do not skip to a lower option if a higher
one is available.

**For naming an element:**
1. Native `<label for>` association — always first for form inputs
2. Visible text wrapped in the element — use the text that's already there
3. Visually hidden `<span class="bpk-visually-hidden">` appended inside
   the label — adds context without replacing visible text
4. `aria-labelledby` referencing visible text elsewhere on the page
5. `aria-label` — only when there is genuinely no visible text to build
   from (e.g. icon-only buttons, standalone landmarks)

**For adding context to an existing label:**
- Use `aria-describedby` pointing to a visually hidden or visible element
- Or append a `<span class="bpk-visually-hidden">` inside the label

**Never use `aria-label` to replace visible text.** If visible text
already exists, augment it — don't override it. Replacing visible text
with `aria-label` breaks WCAG 2.5.3 (Label in Name) for speech input
users who speak what they see.

```html
<!-- Wrong — aria-label replaces visible text, breaking speech input -->
<input type="checkbox" aria-label="Add nearby airports to origin">
<span>Add nearby airports</span>

<!-- Right — visually hidden text appends context, visible text stays -->
<label>
  Add nearby airports
  <span class="bpk-visually-hidden"> to origin</span>
</label>
```

### 4. ARIA — use sparingly and correctly

- `aria-label` must contain the visible label text (WCAG 2.5.3)
- `aria-labelledby` takes precedence over native `<label>` — use only
  when you need to reference multiple elements
- `aria-expanded` for toggle buttons — not `aria-pressed` (that is for
  stateful toggle buttons only)
- `aria-selected` for selected items in a collection (tabs, calendar dates)
- `aria-pressed` for on/off toggle buttons only
- Never put interactive children inside `aria-hidden` containers

### 4. Keyboard contracts

Every interactive element must be:
- Reachable by Tab key
- Operable by keyboard alone (Enter for links/buttons, Space for buttons/checkboxes)
- Visually focused with a clear indicator (never `outline: none` without replacement)
- Part of a logical tab order that follows reading order

For custom widgets, follow APG keyboard patterns exactly. Load
`skills/keyboard/SKILL.md` for component-specific contracts.

### 5. Focus management

- Modals: move focus in on open, trap within, return to trigger on close
- Route changes (SPA): move focus to the new page heading or main content
- Dynamic content: move focus to newly revealed content if user triggered it
- Deleted triggers: move focus to the next logical element before removal

### 6. Colour and non-text content

- Never convey information by colour alone — pair with text, icon, or pattern
- Text contrast: 4.5:1 normal, 3:1 large (18pt+ or 14pt+ bold)
- UI component contrast: 3:1 against adjacent colours
- All meaningful images need descriptive alt text
- Decorative images: `alt=""` and `aria-hidden="true"`
- Icon-only buttons must have `aria-label`

### 7. Dynamic content and live regions

- Live region must be in the DOM before content is injected — never create
  dynamically and populate simultaneously
- `aria-live="polite"` for non-urgent updates (search results, counts)
- `role="status"` for confirmations (save success, filter applied)
- `role="alert"` only for urgent messages requiring immediate attention
- Never put interactive elements inside a live region

---

## Skyscanner-specific rules

These override generic guidance when working on Skyscanner products.
Full component rules are in `rules.yaml`.

- **BpkSwitch** announces as "checkbox" — this is expected, do not flag
- **Strikethrough prices** are not announced by AT — always flag if no
  visually hidden text provides the original price context
- **Date cells** must use `aria-selected`, not `aria-pressed`
- **Card lists** on web must use `<ul>` or `<ol>` — iOS follows Apple HIG
  and intentionally omits container grouping
- **Info banners** must convey type (information/warning/error/success)
  via visually hidden text — the icon must be `aria-hidden`
- **Toggle buttons** use `aria-expanded` OR change their visible label —
  never both
- **Link buttons** (BpkButtonLink) are for actions only, not navigation

---

## Producing findings (Jira-mapped output)

When reviewing code or HTML, produce findings in this shape.
Every field maps to a Skyscanner Jira custom field.

```
[IMPACT] Title — Component (WCAG SC number and name)

Description:
What is wrong and why it matters to AT users.

Affected user groups: [from: Keyboard-only users / Screen reader users /
Low vision users / Deaf/Hard of hearing / Motor/Dexterity impairments /
Cognitive/Learning disabilities / Seizure/Vestibular sensitivities /
Speech input users]

Responsibility: [Design / Development / Content]

How to fix:
Specific, actionable remediation with correct code example.

Testing guidance:
How to verify the fix with AT.
```

Impact levels:
- **Blocker** — prevents task completion entirely for one or more groups
- **High** — significantly impairs access; workaround is unreasonable
- **Medium** — creates friction; workaround exists
- **Low** — best-practice gap; marginal real-world impact

---

## Automation ceiling

Automated tools cover approximately 30–40% of WCAG 2.2 criteria
(Adrian Roselli, Steve Faulkner). Always flag when manual AT testing
is required — particularly for:

- Screen reader announcement quality and sequence
- Keyboard flow through complex interactive patterns
- Focus management in dynamic interfaces
- Mobile gesture alternatives
- Live region timing and content

---

## AT quirks to be aware of

- `list-style: none` removes list semantics in Safari/VoiceOver — add
  `role="list"` as a workaround (Apple-acknowledged intended behaviour)
- VoiceOver linear navigation stops on `<label>` elements and again on
  the `<input>` inside, producing double announcements — known WebKit
  quirk (#191743), not an implementation error
- `role="alert"` is frequently overused — prefer `role="status"` for
  non-urgent confirmations
- iOS Dynamic Type testing: use 235% text size (nearest available to
  WCAG's 200% normative threshold)

---

## What this skill does not cover

- Mobile native component-level contracts (iOS/SwiftUI, Android/Jetpack
  Compose) — these require Abra and platform-specific guidance
- Backpack component acceptance criteria — load `backpack-a11y/SKILL.md`
- Colour contrast script execution — run Backpack's contrast script directly
