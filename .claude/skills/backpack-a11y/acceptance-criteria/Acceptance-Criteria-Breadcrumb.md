---
title: "Acceptance Criteria: Breadcrumb"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

Breadcrumbs give users context of the currently open page and provide an easy way to navigate back.

**Backpack guidance:** skyscanner.design/latest/components/breadcrumb/accessibility-AH8HlNsw

---

## Semantic markup

- The breadcrumb is wrapped in a `<nav>` element with `aria-label="Breadcrumb"` (or equivalent).
  - **WCAG 1.3.1** Info and Relationships
- Each breadcrumb item is a link (`<a>`) except the current page.
  - **WCAG 4.1.2** Name, Role, Value
- The current page item is not a link — it is either plain text or marked with `aria-current="page"`.
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- Each breadcrumb link is reachable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- The current page is NOT in the tab order.
  - **WCAG 2.4.3** Focus Order
- Pressing Enter on a breadcrumb link navigates to the correct page.
  - **WCAG 2.1.1** Keyboard
- All links have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- Link text meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Focus indicators meet 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- Breadcrumb can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: First breadcrumb announced as link with name and role — e.g. "Skyscanner, link". Current page not announced as a link. Navigating with K key moves through breadcrumb links.
- **VoiceOver + Safari**: Same as NVDA. Current page announced as text or with "current page" context if `aria-current="page"` is present.
- **VoiceOver iOS / TalkBack Android**: Breadcrumb links announced via swipe navigation. Current page not interactive.
