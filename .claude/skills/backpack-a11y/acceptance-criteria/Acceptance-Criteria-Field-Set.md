---
title: "Acceptance Criteria: Field Set"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

A fieldset groups related form controls together. It ensures that screen reader users understand the relationship between controls and the purpose of the group.

**Backpack guidance:** skyscanner.design/latest/components/field-set/accessibility-l4Ex1jcz

---

## Backpack design notes

- Use fieldsets to group related controls — checkboxes, radio buttons, or logically related inputs.
- The legend must be clear and descriptive. Example: "Travellers".
- Every individual control within the fieldset must still have its own appropriate label — the legend does not replace individual labels.

---

## Semantic markup

- Related form controls are wrapped in `<fieldset>` with a `<legend>`.
  - **WCAG 1.3.1** Info and Relationships
- The legend clearly describes the purpose of the group — e.g. "Travellers", "Passenger details".
  - **WCAG 2.4.6** Headings and Labels
- Each individual control within the fieldset has its own visible label.
  - **WCAG 3.3.2** Labels or Instructions

---

## Keyboard

- Tab moves to the first focusable control within the fieldset.
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- All controls within the fieldset are keyboard operable.
  - **WCAG 2.1.1** Keyboard
- All controls have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Adaptive UI

- The fieldset can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Legend announced when entering the group — e.g. "Travellers, group". Each control then announced with its own label, role, and state.
- **VoiceOver + Safari**: Group legend announced on entry. Each control announced individually.
- **VoiceOver iOS / TalkBack Android**: Group context announced. Each control navigable by swipe with its own label and state.
