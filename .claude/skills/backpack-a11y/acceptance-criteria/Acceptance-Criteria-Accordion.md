---
title: "Acceptance Criteria: Accordion"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: WCAG 2.2, APG accordion pattern
---

An accordion is a set of vertically stacked sections. Each section has a header button that expands or collapses its associated content panel.

---

## Labels and messaging

- Each accordion header has a visible label that describes the content of its panel.
  - **WCAG 2.4.6** Headings and Labels

---

## Semantic markup

- Each accordion header uses a `<button>` element with `aria-expanded="true"` (open) or `aria-expanded="false"` (closed).
  - **WCAG 4.1.2** Name, Role, Value
- The button's accessible name matches its visible label.
  - **WCAG 2.5.3** Label in Name
- Each content panel is associated with its header button via `aria-controls` pointing to the panel's `id`.
  - Best practice
- Closed panels are hidden from the accessibility tree (e.g. `hidden` attribute or `display: none`).
  - **WCAG 1.3.2** Meaningful Sequence

---

## Keyboard

- Each accordion header button is reachable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- Pressing Space or Enter on the header button toggles the panel open/closed.
  - **WCAG 2.1.1** Keyboard
- Tab moves into the content of an open panel.
  - **WCAG 2.4.3** Focus Order
- All header buttons have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- Text meets a minimum contrast ratio of 4.5:1 (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Open/closed state is not conveyed by colour alone.
  - **WCAG 1.4.1** Use of Color
- Focus indicators meet 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- Content can be viewed at 320px viewport width without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text
