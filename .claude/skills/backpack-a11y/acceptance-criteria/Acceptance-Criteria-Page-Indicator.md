---
title: "Acceptance Criteria: Page Indicator"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Skyscanner page indicator audit (250718), WCAG 2.2
---

The page indicator component shows the current position within a carousel or set of slides. It consists of a series of buttons — one per slide — that allow users to navigate directly to a specific slide.

---

## Labels and messaging

- Each indicator button has a descriptive accessible name that communicates its purpose, state, and position (e.g. "Go to slide 2").
  - **WCAG 4.1.2** Name, Role, Value
- The current indicator communicates its selected/active state.
  - **WCAG 4.1.2** Name, Role, Value

---

## Semantic markup

- Each page indicator is a `<button>` element.
  - **WCAG 4.1.2** Name, Role, Value
- The current slide's indicator uses `aria-current="true"` or `aria-pressed="true"` consistently.
  - **WCAG 4.1.2** Name, Role, Value
- The group of indicators is wrapped in a landmark or has a group label if appropriate.
  - **Best practice**

---

## Keyboard

- All indicator buttons are reachable using the Tab key in logical order.
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- Pressing Space or Enter on an indicator button navigates to the corresponding slide.
  - **WCAG 2.1.1** Keyboard
- All buttons have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible
- No button is completely obscured by other content when focused.
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)

---

## Visual design

- The active/current indicator is visually distinct from inactive indicators.
  - **WCAG 1.4.1** Use of Color — must not rely on colour alone
- Focus indicators meet a 3:1 contrast ratio against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Indicator buttons meet a minimum touch target size of 24×24px (WCAG minimum) — recommended 44×44px for iOS.
  - **WCAG 2.5.8** Target Size (Minimum)

---

## Adaptive UI

- The component can be viewed at 320px viewport width without horizontal scrolling.
  - **WCAG 1.4.10** Reflow

---

## Screen reader expectations (Skyscanner audit)

- **NVDA + Chrome**: Each indicator announced with its purpose, state, and position — e.g. "Go to slide 2, button, current". Tab between indicators announces each correctly.
- **VoiceOver + Safari / iOS**: Equivalent announcements via Tab or swipe navigation. Current state communicated.
- **TalkBack Android**: Equivalent announcements via swipe navigation.
