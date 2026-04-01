---
title: "Acceptance Criteria: Nudger"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

The nudger allows users to quickly specify a value within a given range. Used in Skyscanner as the passenger counter and similar steppers.

**Backpack guidance:** skyscanner.design/latest/components/nudger/accessibility-N3PnGpzB

---

## Labels and messaging

- Each nudger is clearly associated with its label (e.g. "Adults 18+", "Children 2–17").
  - **WCAG 1.3.1** Info and Relationships
- The current value is communicated to AT on every change.
  - **WCAG 4.1.3** Status Messages
- When the minimum value is reached, the decrement button is disabled or the AT user is informed the minimum has been reached.
  - **WCAG 4.1.2** Name, Role, Value
- When the maximum value is reached, the increment button is disabled or the AT user is informed the maximum has been reached.
  - **WCAG 4.1.2** Name, Role, Value
- Related nudgers (e.g. Adults, Children, Infants) are grouped with `<fieldset>` + `<legend>`.
  - **WCAG 1.3.1** Info and Relationships

---

## Semantic markup

- Decrement and increment controls use `<button>` elements with descriptive accessible names.
  - **WCAG 4.1.2** Name, Role, Value
- The current value display is announced on change — via live region (`role="status"`) or accessible name update.
  - **WCAG 4.1.3** Status Messages

---

## Keyboard

- Tab moves to the first focusable element — either the decrement button or the value display (if focusable).
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- Enter or Space activates the decrement/increment buttons.
  - **WCAG 2.1.1** Keyboard
- When focus is on the value display, Up/Down arrow keys increase/decrease the value.
  - **WCAG 2.1.1** Keyboard
- All interactive elements have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Button borders/icons meet 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Touch target meets minimum 24×24px — recommended 44×44pt (iOS) / 48×48dp (Android).
  - **WCAG 2.5.8** Target Size (Minimum)

---

## Adaptive UI

- The component can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Decrement button announced with name and role. Value announced on change. Increment announced. At minimum: "minus, button, dimmed" or equivalent.
- **VoiceOver + Safari**: Equivalent. Value change announced.
- **VoiceOver iOS / TalkBack Android**: Group legend announced. Each button announced with name. Value announced on change. At minimum/maximum, button announced as dimmed/unavailable.
