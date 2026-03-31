---
title: "Acceptance Criteria: Date Picker"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Skyscanner date picker audit (250919), WCAG 2.2, APG date picker pattern
---

A date picker allows users to select a date from a calendar grid. It consists of a text input that opens a calendar dialog. The calendar uses a grid pattern to enable keyboard navigation between dates.

**Skyscanner note:** Date cells use `aria-selected`, not `aria-pressed`. Dates are selected from a collection — they are not toggle buttons.

---

## Labels and messaging

- The date input has a visible label that clearly describes its purpose (e.g. "Departure date").
  - **WCAG 2.4.6** Headings and Labels
- The current selected date is communicated to assistive technology.
  - **WCAG 4.1.2** Name, Role, Value
- Disabled/unavailable dates are programmatically marked and announced as unavailable or dimmed.
  - **WCAG 4.1.2** Name, Role, Value

---

## Semantic markup

- The date input has an accessible name in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value
- The calendar grid uses `role="grid"`.
  - **WCAG 4.1.2** Name, Role, Value
- Each date cell uses `aria-selected="true"` for the selected date and `aria-selected="false"` for others.
  - **WCAG 4.1.2** Name, Role, Value — do not use `aria-pressed` on date cells
- Month and year navigation buttons have descriptive accessible names (e.g. "Previous month", "Next month").
  - **WCAG 4.1.2** Name, Role, Value
- The calendar dialog has an accessible name (e.g. via `aria-label` or `aria-labelledby`).
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- The date input is reachable using the Tab key and shows a visible focus indicator.
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.7** Focus Visible
- Pressing Space or Enter on the input opens the calendar.
  - **WCAG 2.1.1** Keyboard
- When the calendar opens, focus moves to the month selector or the first focusable element within the calendar.
  - **WCAG 2.4.3** Focus Order
- Arrow keys navigate between dates within the calendar grid.
  - **WCAG 2.1.1** Keyboard
- Page Up / Page Down navigate to the previous/next month.
  - **Best practice** — APG date picker pattern
- Pressing Space or Enter on a date selects it, closes the calendar, and moves focus to the next logical step (e.g. return date input or passenger selector).
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- Pressing Escape closes the calendar without selection and returns focus to the input that opened it.
  - **WCAG 2.1.1** Keyboard
- Disabled dates and controls cannot be activated.
  - **WCAG 2.1.1** Keyboard
- Tab and Shift+Tab cycle through all interactive elements within the calendar (navigation buttons, grid, close button).
  - **WCAG 2.1.1** Keyboard

---

## Visual design

- All text within the date picker meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- The selected date is visually distinct from unselected dates.
  - **WCAG 1.4.1** Use of Color — must not rely on colour alone
- Disabled dates are visually distinct and do not rely on colour alone.
  - **WCAG 1.4.1** Use of Color
- Focus indicators meet a 3:1 contrast ratio against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The date picker can be viewed at 320px viewport width without requiring horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation or content loss.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Skyscanner audit)

- **NVDA + Chrome**: Input label and role announced on focus. Calendar announces current month, year, and date on navigation. Disabled dates announced as "unavailable". Selected date confirmed on selection.
- **VoiceOver + Safari**: Input label and role announced. Calendar entry announced with month, year, grid dimensions — e.g. "Entering September 2025 table. Friday, 19th September 2025, selected, toggle button, 7 columns, 6 rows". Disabled dates announced as "dimmed".
- **VoiceOver iOS / TalkBack Android**: Input label and role announced on swipe. Dates navigable by swipe. Disabled dates announced as "dimmed" (iOS) or "not available" (Android).
