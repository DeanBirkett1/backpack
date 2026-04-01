---
title: "Acceptance Criteria: Select"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

The select component allows users to pick a single option from a dropdown menu. Where possible, use the native `<select>` element — the browser handles all keyboard behaviour.

**Backpack guidance:** skyscanner.design/latest/components/select/accessibility-rP3SxlU0

---

## Labels and messaging

- The select has a visible label.
  - **WCAG 3.3.2** Labels or Instructions
- If disabled, the disabled state is communicated to AT.
  - **WCAG 4.1.2** Name, Role, Value

---

## Semantic markup

- Use the native `<select>` element where possible — do not recreate with custom ARIA.
  - **WCAG 4.1.2** Name, Role, Value
- The select has a programmatic label via `<label for>`.
  - **WCAG 1.3.1** Info and Relationships
- The selected option's value is present in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- Tab moves focus to the select.
  - **WCAG 2.1.1** Keyboard
- Space or Enter opens the dropdown.
  - **WCAG 2.1.1** Keyboard
- Up/Down arrow keys navigate options.
  - **WCAG 2.1.1** Keyboard
- Enter selects the focused option and closes the dropdown.
  - **WCAG 2.1.1** Keyboard
- Escape closes the dropdown without changing the selection.
  - **WCAG 2.1.1** Keyboard
- Typing the first letter of an option jumps to the first matching option.
  - Best practice
- Focusing an option does not trigger an unexpected context change.
  - **WCAG 3.2.1** On Focus
- Choosing an option does not trigger an unexpected context change.
  - **WCAG 3.2.2** On Input
- The select has a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible
- When focused, the select is not completely obscured by other content.
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)
- If disabled, the select cannot be reached or interacted with via keyboard.
  - **WCAG 2.1.1** Keyboard

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- The select border meets 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Focus indicators meet 3:1 contrast.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The component can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Select name, role, and current value announced on focus. Options announced as navigated. Selection confirmed on Enter.
- **VoiceOver + Safari**: Equivalent. Options announced individually. Selection confirmed.
- **VoiceOver iOS / TalkBack Android**: Announced on swipe. Picker opened on double-tap. Options announced as scrolled.
