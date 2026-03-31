---
title: "Acceptance Criteria: Tabs"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: WCAG 2.2, APG tabs pattern, Backpack audit history
---

A tab component consists of a tab list and associated tab panels. Activating a tab displays its panel and hides the others. Backpack uses manual activation — arrow keys move focus between tabs, Enter/Space activates.

**Known Skyscanner defect:** Tab interfaces have previously used `role="checkbox"` on tab elements. This is incorrect — use `role="tab"`, `role="tablist"`, `role="tabpanel"`.

---

## Labels and messaging

- Each tab has a visible label that clearly describes the content of its associated panel.
  - **WCAG 2.4.6** Headings and Labels

---

## Semantic markup

- The tab list container has `role="tablist"`.
  - **WCAG 4.1.2** Name, Role, Value
- Each tab element has `role="tab"`.
  - **WCAG 4.1.2** Name, Role, Value
- Each tab panel has `role="tabpanel"`.
  - **WCAG 4.1.2** Name, Role, Value
- The active tab has `aria-selected="true"`; inactive tabs have `aria-selected="false"`.
  - **WCAG 4.1.2** Name, Role, Value
- Each tab panel has an accessible name — typically via `aria-labelledby` pointing to its controlling tab.
  - **WCAG 4.1.2** Name, Role, Value
- Only the active tab panel is visible and present in the accessibility tree.
  - **WCAG 1.3.2** Meaningful Sequence
- Inactive tabs use `tabindex="-1"` (roving tabindex pattern); active tab uses `tabindex="0"`.
  - Best practice

---

## Keyboard

- Tab moves focus to the tab list; one tab receives focus.
  - **WCAG 2.1.1** Keyboard
- Arrow Left / Arrow Right (horizontal tabs) moves focus between tab elements without activating them.
  - Best practice — APG manual activation
- Pressing Enter or Space on a focused tab activates it and shows its panel.
  - **WCAG 2.1.1** Keyboard
- Focus remains on the activated tab after activation.
  - **WCAG 2.4.3** Focus Order
- Tab from the tab list moves focus into the active tab panel.
  - **WCAG 2.4.3** Focus Order
- Tab elements have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible
- Focused tab elements are not completely obscured by other content.
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)

---

## Visual design

- The active tab is visually distinct from inactive tabs — not by colour alone.
  - **WCAG 1.4.1** Use of Color
- All text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
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
