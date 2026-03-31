---
title: "Acceptance Criteria: Card List"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

A flexible layout pattern for displaying an array of cards. Grouping and list semantics differ by platform — follow the platform-specific guidance below.

**Backpack guidance:** skyscanner.design/latest/components/card-list/accessibility-lC3EUvDb

---

## Backpack design notes (platform-specific grouping)

- **Web:** Use `<ul>` or `<ol>` to wrap the collection of cards. This allows screen reader users to hear the total count, use list shortcuts, and skip past the entire list.
- **Android:** The Card List component announces correctly as a group out of the box — no additional markup needed.
- **iOS:** Per Apple's Human Interface Guidelines, card collections should **not** be artificially grouped at the container level. VoiceOver users navigate through cards sequentially without container-level list announcements.

---

## Semantic markup (web)

- The card list uses `<ul>` or `<ol>` with each card as an `<li>`.
  - **WCAG 1.3.1** Info and Relationships
- Each card within the list has a meaningful heading or accessible name that distinguishes it from other cards.
  - **WCAG 2.4.6** Headings and Labels
- If `list-style: none` is applied, add `role="list"` to restore semantics in Safari/VoiceOver.
  - **WCAG 1.3.1** Info and Relationships

---

## Keyboard

- Each interactive card is reachable by keyboard.
  - **WCAG 2.1.1** Keyboard
- Tab order follows the visual reading order.
  - **WCAG 2.4.3** Focus Order
- All interactive elements have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)

---

## Adaptive UI

- The list can be viewed at 320px, stacking to a single column if needed.
  - **WCAG 1.4.10** Reflow

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome / VoiceOver + Safari (web):** List type and count announced on entry — e.g. "List, 6 items". Each card navigable with list shortcuts.
- **TalkBack Android:** Collection announced as group with item counts out of the box.
- **VoiceOver iOS:** Cards navigated sequentially without container-level list announcements — this is correct per Apple HIG.
