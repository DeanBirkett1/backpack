---
title: "Acceptance Criteria: Switch"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

A switch toggles the selection of an item on or off instantly. Visually it appears different to a checkbox, but it is announced as a checkbox by screen readers.

**Backpack guidance:** skyscanner.design/latest/components/switch/accessibility-Z3G4wmO9

---

## Backpack design notes

- Switches appear visually different to checkboxes but are announced as "checkboxes" by screen readers. This is expected behaviour — do not attempt to override it with ARIA.
- Example announcement: "Checkbox, checked price alerts".

---

## Labels and messaging

- The switch has a visible label that describes what it controls.
  - **WCAG 3.3.2** Labels or Instructions

---

## Semantic markup

- The switch uses a native `<input type="checkbox">` or `role="switch"` with an associated label.
  - **WCAG 4.1.2** Name, Role, Value
- The on/off state is present in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- The switch is reachable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- Pressing Space toggles the switch state (on/off).
  - **WCAG 2.1.1** Keyboard
- The switch has a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- On/off state is not conveyed by colour alone.
  - **WCAG 1.4.1** Use of Color
- The switch control meets 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Label text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)

---

## Adaptive UI

- The component can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Touch target meets minimum 24×24px — recommended 44×44pt (iOS) / 48×48dp (Android).
  - **WCAG 2.5.8** Target Size (Minimum)

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Name, role, and state announced as checkbox — e.g. "Checkbox, checked price alerts". Space toggles, change confirmed.
- **VoiceOver + Safari**: Same pattern. State change announced on toggle.
- **VoiceOver iOS / TalkBack Android**: Announced via swipe. Double-tap to toggle. State change confirmed.
