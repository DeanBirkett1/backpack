---
title: "Acceptance Criteria: List"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

The list component creates ordered or unordered lists. Lists must use correct semantic markup so screen readers can announce the list type, item count, and navigation shortcuts.

**Backpack guidance:** skyscanner.design/latest/components/list/accessibility-wWmax5eQ

**Note:** In Safari/VoiceOver, applying `list-style: none` via CSS removes list semantics. Add `role="list"` explicitly to restore them.

---

## Semantic markup

- Unordered lists use `<ul>` with `<li>` items.
  - **WCAG 1.3.1** Info and Relationships
- Ordered lists use `<ol>` with `<li>` items.
  - **WCAG 1.3.1** Info and Relationships
- If `list-style: none` is applied in CSS, add `role="list"` to restore semantics in Safari/VoiceOver.
  - **WCAG 1.3.1** Info and Relationships
- Nested lists are correctly structured.
  - **WCAG 1.3.1** Info and Relationships

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)

---

## Adaptive UI

- Lists can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text
- Text spacing can be increased without overlap or truncation.
  - **WCAG 1.4.12** Text Spacing

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: L key moves to next list. Type and count announced — e.g. "List with 3 items, Flight availability". Items announced on Down arrow. Exiting the list announced.
- **VoiceOver + Safari**: Group announced as "List, 6 items" or "Ordered list, 6 items". CTRL+OPT+right arrow moves through items. List end announced. `role="list"` required if `list-style: none` is used.
- **VoiceOver iOS / TalkBack Android**: List announced with count. Items navigable by swipe.
