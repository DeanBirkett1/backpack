---
title: "Acceptance Criteria: Button"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: WCAG 2.2, APG button pattern, Backpack component audit history
---

A button is an interactive element that triggers an action or event. Buttons must be clearly labelled, keyboard operable, and communicate their state to assistive technology.

**Backpack guidance:** skyscanner.design/latest/components/button/accessibility-A6FBXJ3V

> Baseline criteria apply to this component — see `Acceptance-Criteria-Baseline.md` for Visual design, Adaptive UI, Focus, Accessible naming, and Motion.

---

## Backpack design notes

- **Icon-only buttons:** Use universally recognised icons. If the design allows, labels alongside icons are preferable. Always annotate designs with the accessible name for development.
- **Repeated labels:** Where multiple buttons share the same visible label (e.g. multiple "Select" buttons), annotate designs with what should be announced to screen reader users. Include enough context for the user to decide — consider what is helpful given the action and what can be discovered elsewhere on the page.
- **Link button vs link:** Use a link button (`<button>`) to trigger actions — opening a menu, triggering a modal, showing more results, playing media. Use a link (`<a>`) to navigate to a new page, in-page anchor, or external document. Link buttons must not open new pages.
- **Toggle buttons:** Choose one method only — either change the button label (e.g. "Show more" / "Show less") OR use `aria-expanded`. Do not combine both methods.

---

## Labels and messaging

- The button has a visible label that describes the action it performs.
  - **WCAG 2.4.6** Headings and Labels

---

## Semantic markup

- Buttons use the native `<button>` element wherever possible.
  - **WCAG 4.1.2** Name, Role, Value
- The button's accessible name matches its visible label exactly, or at minimum starts with the visible label text.
  - **WCAG 2.5.3** Label in Name
- The button's accessible name and role are present in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value
- If the button is disabled, the disabled state is present in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value

### Icon-only buttons

- Icon-only buttons have an `aria-label` that communicates the action — e.g. `aria-label="Close"`.
  - **WCAG 4.1.2** Name, Role, Value
- The icon is hidden from the accessibility tree (`aria-hidden="true"`).
  - **WCAG 1.1.1** Non-text Content
- If the icon is not widely recognised, a tooltip appears on hover and focus to reinforce the label.
  - Best practice

### Toggle buttons

- Toggle buttons use `aria-pressed="true"` (on) and `aria-pressed="false"` (off).
  - **WCAG 4.1.2** Name, Role, Value
- The button's visible label does not change when its state changes — only `aria-pressed` updates.
  - Best practice / **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- The button is activated by pressing Space or Enter.
  - **WCAG 2.1.1** Keyboard
- The button has a visible focus indicator when focused via keyboard.
  - **WCAG 2.4.7** Focus Visible
- When the button is activated, focus remains on the button (unless the action navigates away or opens a dialog).
  - **WCAG 2.4.3** Focus Order
- When the button receives keyboard focus it is not completely obscured by other content.
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)

---
