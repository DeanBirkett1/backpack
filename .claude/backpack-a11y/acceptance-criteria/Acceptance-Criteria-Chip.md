---
title: "Acceptance Criteria: Chip"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: WCAG 2.2, Backpack component audit history
---

Chips are compact interactive elements used for filtering, selecting options, or triggering actions. They appear as individual toggle buttons or as part of a group.

**Backpack guidance:** skyscanner.design/latest/components/chip/accessibility-ZZ80gAW3

---

## Backpack design notes

- **Communicate purpose:** Chips can show a dropdown list, open a modal, or show a bottom sheet. Annotate the design so the action/purpose is clear for development.
- **Dynamic changes:** When a dismissible chip is removed, or a chip filters content, the change must be announced to AT users. Announce the updated total via a live region. Show the updated total visually where possible to reduce cognitive effort.
- **Disabled chips:** Although disabled chips are exempt from minimum contrast requirements, they remain difficult to read. Consider whether missing the information creates a barrier and whether an alternative is needed.

---

## Labels and messaging

- Each chip has a visible label that clearly describes its purpose or the filter it represents.
  - **WCAG 2.4.6** Headings and Labels

---

## Semantic markup

- Chips use `<button>` elements.
  - **WCAG 4.1.2** Name, Role, Value
- The chip's accessible name matches its visible label.
  - **WCAG 2.5.3** Label in Name
- If the chip acts as a toggle (selected/unselected), it uses `aria-pressed="true"` or `aria-pressed="false"`.
  - **WCAG 4.1.2** Name, Role, Value
- If chips are part of a group where only one can be selected, the group uses `role="group"` with a descriptive label, and the selected chip uses `aria-pressed="true"`.
  - **WCAG 1.3.1** Info and Relationships

---

## Keyboard

- Each chip is focusable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- Pressing Space or Enter activates the chip.
  - **WCAG 2.1.1** Keyboard
- All chips have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible
- Focused chips are not completely obscured by other content.
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)

---

## Visual design

- Chip label text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Selected/unselected state is not conveyed by colour alone.
  - **WCAG 1.4.1** Use of Color
- Focus indicators meet 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Touch target size meets a minimum of 24×24px — recommended 44×44pt on iOS.
  - **WCAG 2.5.8** Target Size (Minimum)

---

## Adaptive UI

- Chips can be viewed at 320px viewport width without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text
