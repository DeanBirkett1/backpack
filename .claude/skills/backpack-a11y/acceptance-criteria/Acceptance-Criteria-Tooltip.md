---
title: "Acceptance Criteria: Tooltip"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Skyscanner tooltip audit (250902), WCAG 2.2, APG tooltip pattern
---

A tooltip is a short description that appears when a user hovers over or focuses on an element. It provides supplementary context without cluttering the main interface. Tooltips must be reachable by pointer, keyboard, and touch device users.

**Backpack guidance:** skyscanner.design/latest/components/tooltip/accessibility-XKCjDrBc

---

## Backpack design notes

- Tooltips need to be reachable by pointer, keyboard, and touch device users — not just mouse hover.
- A common solution is to add an extra tab stop for the tooltip trigger, or ensure the tooltip opens when interacting with the surrounding component.
- When using a tooltip in a design, annotate how it should be accessible to keyboard and touch users.

---

## Labels and messaging

- The tooltip trigger has a visible label (icon or text) that clearly describes its purpose.
  - **WCAG 2.4.6** Headings and Labels

---

## Semantic markup

- The tooltip content has `role="tooltip"` in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value
- The tooltip content is associated with its trigger via `aria-describedby`.
  - **WCAG 1.3.1** Info and Relationships
- The tooltip trigger has an accessible name in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value
- The tooltip trigger has an appropriate role (e.g. button) in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value
- The tooltip content is programmatically hidden when not active and becomes visible when triggered.
  - **WCAG 1.4.13** Content on Hover or Focus

---

## Keyboard

- The tooltip trigger is focusable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- The tooltip content appears when the trigger receives keyboard focus.
  - **WCAG 1.4.13** Content on Hover or Focus
- The tooltip can be dismissed by pressing Escape without moving focus.
  - **WCAG 1.4.13** Content on Hover or Focus
- The tooltip disappears when keyboard focus moves away from the trigger.
  - **WCAG 1.4.13** Content on Hover or Focus
- The trigger has a visible focus indicator when focused via keyboard.
  - **WCAG 2.4.7** Focus Visible
- When the trigger receives keyboard focus it is not completely obscured by other content.
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)

---

## Visual design

- The tooltip content remains visible when the mouse cursor moves from the trigger onto the tooltip itself.
  - **WCAG 1.4.13** Content on Hover or Focus
- All text within the tooltip meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text — 24px regular or 18.66px bold and above).
  - **WCAG 1.4.3** Contrast (Minimum)
- The tooltip trigger icon has a minimum contrast ratio of 3:1 against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- If the trigger uses a custom focus style, the focus indicator has a contrast ratio of 3:1 against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- Tooltip text can be increased to 200% without truncation, overlap, or content loss.
  - **WCAG 1.4.4** Resize Text
- The tooltip can be viewed at 320px viewport width without requiring horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text spacing within the tooltip can be increased without text overlapping, truncating, or being cut off.
  - **WCAG 1.4.12** Text Spacing

---

## Screen reader expectations (Skyscanner audit)

- **NVDA + Chrome / VoiceOver + Safari**: Tooltip content is announced when the trigger receives focus. Example: "YUL, Montréal–Trudeau International Airport".
- **VoiceOver iOS**: Tooltip content is announced when the element receives focus via swipe navigation.
- **TalkBack Android**: Tooltip content is announced when the element receives focus via swipe navigation.
