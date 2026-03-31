---
title: "Acceptance Criteria: Info Banner"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

The info banner highlights important information for travellers. It uses an icon to communicate severity or type (information, success, warning, error), which must be conveyed to screen reader users via visually hidden text.

**Backpack guidance:** skyscanner.design/latest/components/info-banner/accessibility-9eQm8599

---

## Backpack design notes

- The icon communicates the type of banner visually (information, success, warning, error). This meaning must be conveyed to AT users via visually hidden text preceding the banner message — e.g. "Information", "Warning", "Error".
- The icon itself should be hidden from the accessibility tree (`aria-hidden="true"`); the visually hidden text carries the meaning.

---

## Semantic markup

- The banner's type/severity is communicated via visually hidden text (e.g. "Warning") before the visible message.
  - **WCAG 1.1.1** Non-text Content / **WCAG 1.3.1** Info and Relationships
- The icon is hidden from the accessibility tree (`aria-hidden="true"`).
  - **WCAG 1.1.1** Non-text Content
- Banner type is not conveyed by colour alone.
  - **WCAG 1.4.1** Use of Color

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- The banner border/background meets 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The banner can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome / VoiceOver + Safari**: Banner announced with type then text — e.g. "Information, Your booking is confirmed" or "Warning, Your session is about to expire".
- **VoiceOver iOS / TalkBack Android**: Same pattern via swipe navigation.
