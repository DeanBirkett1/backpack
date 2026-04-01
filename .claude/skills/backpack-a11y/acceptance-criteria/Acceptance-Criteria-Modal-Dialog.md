---
title: "Acceptance Criteria: Modal Dialog"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: WCAG 2.2, APG dialog pattern, Backpack component audit history
---

A modal dialog interrupts the user's workflow to present critical information or require a decision. While open, background content must be inert — not reachable by keyboard or assistive technology.

---

## Labels and messaging

- The dialog has a visible title that communicates its purpose.
  - **WCAG 2.4.6** Headings and Labels
- The close button has a descriptive accessible name (e.g. "Close").
  - **WCAG 4.1.2** Name, Role, Value

---

## Semantic markup

- Use the native `<dialog>` element where possible, or apply `role="dialog"` to a `<div>`.
  - **WCAG 4.1.2** Name, Role, Value
- The dialog has `aria-modal="true"` to signal that background content is inert.
  - **WCAG 4.1.2** Name, Role, Value
- The dialog has an accessible name via `aria-labelledby` pointing to the dialog title, or `aria-label`.
  - **WCAG 4.1.2** Name, Role, Value
- Background content is made inert (e.g. using `inert` attribute or equivalent) while the dialog is open.
  - **WCAG 2.1.2** No Keyboard Trap

---

## Keyboard

- When the dialog opens, focus moves to the first focusable element inside it, or to the dialog container with `tabindex="-1"`.
  - **WCAG 2.4.3** Focus Order
- Tab cycles through focusable elements within the dialog only — focus does not reach background content.
  - **WCAG 2.1.2** No Keyboard Trap
- Shift+Tab cycles in reverse through focusable elements within the dialog only.
  - **WCAG 2.1.2** No Keyboard Trap
- Pressing Escape closes the dialog and returns focus to the element that triggered it.
  - **WCAG 2.1.1** Keyboard
- Activating the close button closes the dialog and returns focus to the trigger element.
  - **WCAG 2.4.3** Focus Order
- All interactive elements within the dialog have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- All text within the dialog meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Focus indicators meet a 3:1 contrast ratio against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The dialog can be viewed at 320px viewport width without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation or content loss.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations

- **NVDA + Chrome / VoiceOver + Safari**: On open, dialog role and accessible name announced — e.g. "Info, dialog". Focus confirmed within dialog. Background content not reachable. Close button announced as "Close, button". Focus returns to trigger on close.
