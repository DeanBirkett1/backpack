---
title: "Acceptance Criteria: Price"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

The price component shows the cost of flights, hotels, and hire cars in a range of global currencies. Strikethrough pricing must include visually hidden text for screen reader users.

**Backpack guidance:** skyscanner.design/latest/components/price/accessibility-zI8MD37n

---

## Backpack design notes (critical)

- **Strikethrough text is not announced by screen readers.** When a price has `text-decoration: line-through` (original/crossed-out price), it must be accompanied by visually hidden text to communicate meaning — e.g. "Original price £120" before the current price. Annotate designs to tell developers what should be announced.

---

## Semantic markup

- Prices are in a logical reading order that makes sense when read sequentially.
  - **WCAG 1.3.2** Meaningful Sequence
- Strikethrough prices include visually hidden text that communicates the original price context to AT users.
  - **WCAG 1.1.1** Non-text Content / **WCAG 1.3.1** Info and Relationships
- Currency symbols and values are announced in a meaningful order.
  - **WCAG 1.3.1** Info and Relationships

---

## Visual design

- Price text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Price information is not conveyed by colour alone (e.g. discounted price in green only).
  - **WCAG 1.4.1** Use of Color

---

## Adaptive UI

- Price text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text
- Text spacing can be increased without overlap or truncation.
  - **WCAG 1.4.12** Text Spacing

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome / VoiceOver + Safari**: Current price announced clearly. Where a strikethrough original price exists, the visually hidden text is also announced — e.g. "Original price £120" then "Now £89".
- **VoiceOver iOS / TalkBack Android**: Same pattern via swipe navigation.
