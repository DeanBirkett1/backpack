---
title: "Acceptance Criteria: Pagination"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Skyscanner pagination audit, WCAG 2.2
---

The pagination component allows users to navigate through pages of content. It typically consists of previous/next chevron buttons and individual page number buttons, wrapped in a `<nav>` landmark.

---

## Labels and messaging

- The pagination component is wrapped in a `<nav>` element with a descriptive `aria-label` (e.g. "Pagination").
  - **WCAG 1.3.1** Info and Relationships
- Each page number button has a descriptive accessible name (e.g. "Page 1", "Page 2").
  - **WCAG 2.4.6** Headings and Labels
- The current page button communicates its current state.
  - **WCAG 4.1.2** Name, Role, Value
- The previous button has an accessible name (e.g. "Previous").
  - **WCAG 4.1.2** Name, Role, Value
- The next button has an accessible name (e.g. "Next").
  - **WCAG 4.1.2** Name, Role, Value
- When the previous button is disabled (first page), its disabled state is programmatically indicated.
  - **WCAG 4.1.2** Name, Role, Value

---

## Semantic markup

- All pagination controls use `<button>` elements.
  - **WCAG 4.1.2** Name, Role, Value
- The current page button uses `aria-current="page"`.
  - **WCAG 4.1.2** Name, Role, Value
- Disabled buttons use the HTML `disabled` attribute or `aria-disabled="true"`.
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- All pagination buttons are reachable using the Tab key in logical order.
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- Pressing Enter or Space on a page number button navigates to that page.
  - **WCAG 2.1.1** Keyboard
- Pressing Enter or Space on the previous/next chevrons navigates accordingly.
  - **WCAG 2.1.1** Keyboard
- When the first page is reached, the previous button becomes disabled and focus moves to the first page button.
  - **WCAG 2.4.3** Focus Order
- All buttons have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible
- No button is completely obscured by other content when focused.
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)

---

## Visual design

- All text meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- The current page is visually distinct from other page buttons.
  - **WCAG 1.4.1** Use of Color — must not rely on colour alone
- Focus indicators meet a 3:1 contrast ratio against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The pagination component can be viewed at 320px viewport width without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation or content loss.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Skyscanner audit)

- **NVDA + Chrome**: Previous chevron announced as "Previous, button". Page numbers announced as "Page X, button". Current page announced as "Page X, button, current" (or equivalent). Disabled previous button announced as unavailable or dimmed.
- **VoiceOver + Safari / iOS**: Equivalent announcements via Tab or swipe navigation. `aria-current="page"` announced as current.
- **TalkBack Android**: Equivalent announcements via swipe navigation.
