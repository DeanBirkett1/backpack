---
title: "Acceptance Criteria: Swap Button"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

The swap button exchanges the values of two input fields (e.g. "From" and "To" destinations) with a 180-degree rotation animation. The result of the swap must be communicated to AT users.

**Backpack guidance:** skyscanner.design/latest/components/swap-button/accessibility-1o4QCZmS

---

## Labels and messaging

- The swap button has a descriptive accessible name — e.g. "Swap departure and destination".
  - **WCAG 4.1.2** Name, Role, Value
- After activation, the result of the swap (the new field values) is communicated to AT users — either via live region or by AT reading the updated field values on next focus.
  - **WCAG 4.1.3** Status Messages

---

## Semantic markup

- The swap button uses a native `<button>` element.
  - **WCAG 4.1.2** Name, Role, Value
- If the button uses an icon only, it has a descriptive `aria-label`.
  - **WCAG 4.1.2** Name, Role, Value
- The animation respects `prefers-reduced-motion`.
  - Best practice / **WCAG 2.3.3** (AAA — Animation from Interactions)

---

## Keyboard

- The swap button is reachable via Tab from the adjacent input fields.
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- Pressing Enter or Space activates the swap.
  - **WCAG 2.1.1** Keyboard
- After activation, pressing Enter/Space again restores the original values.
  - **WCAG 2.1.1** Keyboard
- The button has a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- The button icon meets 3:1 contrast against its background.
  - **WCAG 1.4.11** Non-text Contrast
- Touch target meets minimum 24×24px — recommended 44×44pt (iOS).
  - **WCAG 2.5.8** Target Size (Minimum)

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Button announced with name and role — e.g. "Swap departure and destination, button". After activation, updated field values readable by AT.
- **VoiceOver + Safari / iOS**: Same pattern.
- **TalkBack Android**: Same pattern via swipe navigation.
