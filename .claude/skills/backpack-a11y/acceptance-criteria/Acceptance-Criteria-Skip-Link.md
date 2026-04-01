---
title: "Acceptance Criteria: Skip Link"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

A skip link allows keyboard users to bypass repeated navigation and jump directly to the main content. It must be the first focusable element on the page.

**Backpack guidance:** skyscanner.design/latest/components/skip-link/accessibility-OIPkctHL

---

## Semantic markup

- The skip link is the first focusable element on the page.
  - **WCAG 2.4.1** Bypass Blocks
- The skip link uses an `<a>` element with an `href` pointing to the `id` of the main content region (e.g. `href="#maincontent"`).
  - **WCAG 2.4.1** Bypass Blocks
- The main content target (`<main id="maincontent">`) has `tabindex="-1"` to allow programmatic focus.
  - **WCAG 2.4.1** Bypass Blocks
- The skip link has a descriptive label — e.g. "Skip to main content".
  - **WCAG 2.4.4** Link Purpose

---

## Keyboard

- The skip link becomes visible on first Tab press (it may be visually hidden until focused).
  - **WCAG 2.4.1** Bypass Blocks
- Pressing Enter on the skip link moves focus to the main content area.
  - **WCAG 2.4.1** Bypass Blocks
- The skip link has a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- When visible, skip link text meets 4.5:1 contrast against its background.
  - **WCAG 1.4.3** Contrast (Minimum)
- Focus indicator meets 3:1 contrast.
  - **WCAG 1.4.11** Non-text Contrast
