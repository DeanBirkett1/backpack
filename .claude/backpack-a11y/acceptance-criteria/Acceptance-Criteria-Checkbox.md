---
title: "Acceptance Criteria: Checkbox"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

Checkboxes allow the user to select one or more items from a set. Each checkbox must have a visible label, communicate its state to AT, and be keyboard operable.

**Backpack guidance:** skyscanner.design/latest/components/checkbox/accessibility-YXTO7x4E

---

## Labels and messaging

- Each checkbox has a visible label that clearly describes the option.
  - **WCAG 3.3.2** Labels or Instructions
- Required checkboxes that are not checked on submission show a clear error message identifying the field.
  - **WCAG 3.3.1** Error Identification

---

## Semantic markup

- Checkboxes use the native `<input type="checkbox">` element with an associated `<label>`.
  - **WCAG 4.1.2** Name, Role, Value
- The checkbox's checked, unchecked, and (where applicable) indeterminate states are communicated in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value
- For grouped checkboxes, the group is wrapped in `<fieldset>` with a `<legend>`.
  - **WCAG 1.3.1** Info and Relationships
- Parent checkboxes that control child checkboxes use the `indeterminate` state when some (but not all) children are selected.
  - **WCAG 4.1.2** Name, Role, Value
- Error messages are programmatically associated with the checkbox via `aria-describedby`.
  - **WCAG 1.3.1** Info and Relationships

---

## Keyboard

- The checkbox is reachable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- Pressing Space toggles the checkbox state (checked/unchecked).
  - **WCAG 2.1.1** Keyboard
- Each checkbox in a group can be selected independently.
  - **WCAG 2.1.1** Keyboard
- The checkbox has a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- There is clear visual feedback for checked, unchecked, and indeterminate states.
  - **WCAG 1.4.1** Use of Color — state must not rely on colour alone
- The checkbox control meets 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Label text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Focus indicators meet 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The component can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Checkbox name, role, and state announced — e.g. "Include nearby airports, checkbox, not checked". Space toggles state, change confirmed. Error announced if required and unchecked on submit.
- **VoiceOver + Safari**: Equivalent announcements. Group legend announced when entering a fieldset group.
- **VoiceOver iOS / TalkBack Android**: Announced via swipe. Double-tap to toggle. State change confirmed.
