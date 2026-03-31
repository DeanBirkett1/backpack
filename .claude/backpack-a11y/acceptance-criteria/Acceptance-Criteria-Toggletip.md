---
title: "Acceptance Criteria: Toggletip"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: WCAG 2.2, Backpack component audit history
---

A toggletip is a small pop-up activated by pressing a button (typically an info icon). Unlike a tooltip, toggletip content is announced to screen readers as it is inserted into the DOM, and it requires an explicit action to open — not just hover or focus.

---

## Labels and messaging

- The toggletip button has a descriptive accessible name (e.g. "More information" or descriptive `aria-label` on an icon button).
  - **WCAG 4.1.2** Name, Role, Value / **WCAG 2.4.6** Headings and Labels

---

## Semantic markup

- The toggletip trigger is a `<button>` element.
  - **WCAG 4.1.2** Name, Role, Value
- The button has `aria-expanded="true"` when the panel is open, `aria-expanded="false"` when closed.
  - **WCAG 4.1.2** Name, Role, Value
- The button has `aria-controls` set to the `id` of the toggletip panel.
  - Best practice / **WCAG 1.3.1** Info and Relationships
- When the panel opens, its content is inserted into the DOM and announced by screen readers.
  - **WCAG 4.1.3** Status Messages — use a live region or ensure announcement via focus management
- The content in the panel comes directly after the button in the DOM/accessibility tree.
  - **WCAG 1.3.2** Meaningful Sequence

---

## Keyboard

- The toggletip button is focusable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- Pressing Space or Enter on the button opens the toggletip panel.
  - **WCAG 2.1.1** Keyboard
- Pressing Space or Enter again closes the panel.
  - **WCAG 2.1.1** Keyboard
- Pressing Escape closes the panel and returns focus to the button.
  - **WCAG 1.4.13** Content on Hover or Focus
- Moving keyboard focus away from the button closes the panel.
  - **WCAG 1.4.13** Content on Hover or Focus
- If the panel contains interactive content, Tab moves focus into it.
  - **WCAG 2.4.3** Focus Order
- The button has a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- All text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- The button icon meets 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Focus indicators meet 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- Content can be viewed at 320px viewport width without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text
- Text spacing can be increased without overlap or truncation.
  - **WCAG 1.4.12** Text Spacing
