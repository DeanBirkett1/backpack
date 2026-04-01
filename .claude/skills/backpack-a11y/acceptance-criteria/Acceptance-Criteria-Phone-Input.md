---
title: "Acceptance Criteria: Phone Input"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Skyscanner phone input audit (250902), WCAG 2.2
---

The phone input component consists of two fields: a country code dropdown and a telephone number input, grouped together under a shared fieldset legend (e.g. "Phone number").

---

## Labels and messaging

- The component has a visible group label (e.g. "Phone number") that describes the purpose of both fields.
  - **WCAG 1.3.1** Info and Relationships
- The country code dropdown has a visible label (e.g. "Dialling code").
  - **WCAG 3.3.2** Labels or Instructions
- The telephone number input has a visible label (e.g. "Telephone number").
  - **WCAG 3.3.2** Labels or Instructions
- If the telephone number field is required, this is indicated visually and programmatically.
  - **WCAG 3.3.2** Labels or Instructions
- Error messages include the field name and describe how to fix the issue (e.g. "Please enter a valid phone number").
  - **WCAG 3.3.1** Error Identification / **WCAG 3.3.3** Error Suggestion

---

## Semantic markup

- Both fields are wrapped in a `<fieldset>` with a `<legend>` that provides the group label.
  - **WCAG 1.3.1** Info and Relationships
- The country code control has an accessible name that matches its visible label.
  - **WCAG 4.1.2** Name, Role, Value
- The telephone number input has an accessible name that matches its visible label.
  - **WCAG 4.1.2** Name, Role, Value
- The telephone number input uses `type="tel"` and `autocomplete="tel"`.
  - **WCAG 1.3.5** Identify Input Purpose
- Error messages are programmatically associated with their field via `aria-describedby`.
  - **WCAG 1.3.1** Info and Relationships
- Invalid fields use `aria-invalid="true"`.
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- Both fields are reachable using the Tab key in logical order.
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- The Space key opens the country code dropdown.
  - **WCAG 2.1.1** Keyboard
- Arrow keys navigate between country options within the dropdown.
  - **WCAG 2.1.1** Keyboard
- Pressing Escape closes the dropdown and returns focus to the dropdown trigger.
  - **WCAG 2.1.1** Keyboard
- Tab moves from the country code dropdown to the telephone number input.
  - **WCAG 2.1.1** Keyboard
- Both fields have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- All text meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Field borders have a minimum contrast ratio of 3:1 against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Focus indicators have a minimum contrast ratio of 3:1 against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- Both fields can be viewed at 320px viewport width without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation or content loss.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Skyscanner audit)

- **NVDA + Chrome**: On focus, fieldset legend announced with field details — e.g. "Phone number, Dialling code, combo box, United Kingdom +44" and "Phone number, Telephone number, edit, required". Error announced on invalid input: "Please enter a valid phone number".
- **VoiceOver + Safari**: Fieldset legend announced when entering the group — e.g. "Phone number, group". Each field's purpose, state, and relationship clearly communicated. Error announced on invalid input.
- **VoiceOver iOS / TalkBack Android**: Fieldset legend announced on entering the group — e.g. "Phone number, group". Each field's purpose communicated via swipe navigation. Error announced on invalid input.
