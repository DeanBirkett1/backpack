---
title: "Acceptance Criteria: Calendar"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2, APG date picker pattern
---

The calendar is used for date selection within a defined time period. It uses a grid pattern for keyboard navigation. See also: Date Picker (Acceptance-Criteria-Date-Picker.md), which embeds the calendar in a popover.

**Backpack guidance:** skyscanner.design/latest/components/calendar/accessibility-w5rTX2ad

**Skyscanner note:** Date cells use `aria-selected`, not `aria-pressed`. Dates are selected from a collection — not toggle buttons.

---

## Labels and messaging

- The calendar has an accessible name communicating the current month/year.
  - **WCAG 4.1.2** Name, Role, Value
- Month navigation buttons have descriptive accessible names — e.g. "Previous month", "Next month".
  - **WCAG 4.1.2** Name, Role, Value
- Disabled/past dates are programmatically marked and announced as unavailable.
  - **WCAG 4.1.2** Name, Role, Value
- The currently selected date communicates its selected state.
  - **WCAG 4.1.2** Name, Role, Value

---

## Semantic markup

- The calendar grid uses `role="grid"`.
  - **WCAG 4.1.2** Name, Role, Value
- Each date cell uses `aria-selected="true"` for the selected date and `aria-selected="false"` for others — not `aria-pressed`.
  - **WCAG 4.1.2** Name, Role, Value
- Disabled dates use `aria-disabled="true"`.
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- Tab focuses the calendar. Focus order matches visual layout: back arrow → month dropdown → forward arrow → calendar grid.
  - **WCAG 2.4.3** Focus Order
- Arrow keys navigate between dates in the grid. Past dates cannot be reached.
  - **WCAG 2.1.1** Keyboard
- Space or Enter selects the focused date.
  - **WCAG 2.1.1** Keyboard
- Page Up / Page Down moves to the previous/next month (Fn + Up/Down on Mac).
  - **WCAG 2.1.1** Keyboard — APG calendar pattern
- Shift + Page Up / Page Down moves to the previous/next year.
  - **WCAG 2.1.1** Keyboard — APG calendar pattern
- Home moves to the first day of the current month (Fn + Left on Mac).
  - **WCAG 2.1.1** Keyboard — APG calendar pattern
- End moves to the last day of the current month (Fn + Right on Mac).
  - **WCAG 2.1.1** Keyboard — APG calendar pattern
- All interactive elements have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Selected date is visually distinct from unselected dates — not by colour alone.
  - **WCAG 1.4.1** Use of Color
- Disabled dates are visually distinct — not by colour alone.
  - **WCAG 1.4.1** Use of Color
- Focus indicators meet 3:1 contrast.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The calendar can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Month and year announced when entering calendar. Each date announced with full date string and selected/unselected state. Disabled dates announced as "unavailable".
- **VoiceOver + Safari**: Calendar entry announced with month, year, and grid dimensions — e.g. "Entering September 2025 table. Friday, 19th September 2025, selected, toggle button, 7 columns, 6 rows". Disabled dates announced as "dimmed".
- **VoiceOver iOS**: Dates navigable by swipe. Disabled dates announced as "dimmed" or "unavailable".
- **TalkBack Android**: Dates navigable by swipe. Disabled dates announced as "not available".
