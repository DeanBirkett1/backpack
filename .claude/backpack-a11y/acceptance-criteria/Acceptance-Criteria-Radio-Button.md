---
title: "Acceptance Criteria: Radio Button"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

A radio button allows a traveller to select a single value from a set of options. Radio buttons must always be grouped with a visible legend and support keyboard navigation within the group.

**Backpack guidance:** skyscanner.design/latest/components/radio-button/accessibility-v3WoGRe9

---

## Backpack design notes

- **Visible group label:** A visible group title (legend) clarifies the available options. Even when a visible label is not present, the group must still be programmatically labelled for AT users.
- **Announcing changes in context:** When selecting a radio button triggers a page refresh or dynamic content update, this change must be announced to AT users via a live region (`aria-live`). Best practice is to warn users in advance that a selection will cause a page update.

---

## Labels and messaging

- Each radio button has a visible label describing the option.
  - **WCAG 3.3.2** Labels or Instructions
- The group has a visible legend that communicates the purpose of the group.
  - **WCAG 1.3.1** Info and Relationships

---

## Semantic markup

- Radio buttons use `<input type="radio">` elements grouped inside `<fieldset>` with `<legend>`.
  - **WCAG 1.3.1** Info and Relationships
- Each radio button's selected/unselected state is present in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value
- If selecting a radio triggers a page or content update, the change is announced via a live region.
  - **WCAG 4.1.3** Status Messages

---

## Keyboard

- Tab moves focus to the selected radio button in the group (or first if none selected).
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- Arrow keys (Up/Down or Left/Right) move between radio options within the group.
  - **WCAG 2.1.1** Keyboard
- All radio buttons have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- Selected/unselected state is not conveyed by colour alone.
  - **WCAG 1.4.1** Use of Color
- Radio control meets 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Label text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)

---

## Adaptive UI

- The component can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Group legend announced when entering the fieldset. Each radio announced with name, role, state — e.g. "Economy, radio button, not checked, 1 of 3". Arrow keys cycle through options.
- **VoiceOver + Safari**: Group announced on entry. Each radio announced with name and state.
- **VoiceOver iOS / TalkBack Android**: Group legend announced. Options navigable by swipe. Double-tap to select.
