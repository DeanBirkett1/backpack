---
title: "Acceptance Criteria: Carousel"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: WCAG 2.2, APG carousel pattern
note: The Backpack accessibility tab for Carousel currently contains no content.
---

A carousel presents a series of content items that cycle horizontally. Carousels must be keyboard operable, controllable by AT users, and must respect motion preferences.

**Backpack guidance:** skyscanner.design/latest/components/carousel/accessibility-tb89dUDp
*(Note: this page currently has no content — criteria below are based on WCAG 2.2 and APG.)*

---

## Labels and messaging

- The carousel has an accessible name — e.g. `aria-label="Featured destinations"` or `aria-labelledby` pointing to a visible heading.
  - **WCAG 4.1.2** Name, Role, Value
- Previous/next buttons have descriptive accessible names — e.g. "Previous slide", "Next slide".
  - **WCAG 4.1.2** Name, Role, Value
- The current slide position is communicated — e.g. "Slide 2 of 5".
  - **WCAG 4.1.2** Name, Role, Value

---

## Semantic markup

- The carousel container has `role="region"` and an accessible name.
  - **WCAG 1.3.1** Info and Relationships
- Individual slides are identifiable by AT — each has a meaningful heading or label.
  - **WCAG 4.1.2** Name, Role, Value
- Auto-rotating carousels include a pause control that is keyboard accessible.
  - **WCAG 2.2.2** Pause, Stop, Hide

---

## Keyboard

- Previous and next controls are reachable via Tab.
  - **WCAG 2.1.1** Keyboard
- Pressing Enter or Space on previous/next advances or retreats the carousel.
  - **WCAG 2.1.1** Keyboard
- Interactive content within each slide is reachable by keyboard.
  - **WCAG 2.1.1** Keyboard
- All controls have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible
- Auto-rotation pauses when any element within the carousel receives keyboard focus.
  - **WCAG 2.2.2** Pause, Stop, Hide

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Controls meet 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The carousel can be viewed at 320px without horizontal scrolling of the page.
  - **WCAG 1.4.10** Reflow
- Animation respects `prefers-reduced-motion` — auto-rotation and transitions are reduced or removed.
  - Best practice
