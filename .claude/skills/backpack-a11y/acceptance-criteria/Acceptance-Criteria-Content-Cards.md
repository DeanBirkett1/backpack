---
title: "Acceptance Criteria: Content Cards"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

Content cards display rich content including images, headings, and actions. Each card must have a meaningful heading, and interactive cards must use the stretched link pattern to avoid nested interactivity.

**Backpack guidance:** skyscanner.design/latest/components/content-cards/accessibility-Lfpk5mrH

---

## Semantic markup

- Each card has a meaningful heading that distinguishes it from other cards.
  - **WCAG 2.4.6** Headings and Labels
- Card images have descriptive `alt` text if informative, or `alt=""` if decorative.
  - **WCAG 1.1.1** Non-text Content
- Interactive cards use the stretched pseudo-element pattern — not an interactive wrapper around all content.
  - **WCAG 4.1.2** Name, Role, Value (see booking-flow-patterns.md for implementation)
- Secondary interactive elements within a card (e.g. Save, Share) are reachable independently.
  - **WCAG 2.1.1** Keyboard

---

## Keyboard

- Interactive cards are reachable via keyboard.
  - **WCAG 2.1.1** Keyboard
- Tab order follows the logical reading order through the card collection.
  - **WCAG 2.4.3** Focus Order
- All interactive elements have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)

---

## Adaptive UI

- Cards can be viewed at 320px, stacking to a single column as needed.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text
