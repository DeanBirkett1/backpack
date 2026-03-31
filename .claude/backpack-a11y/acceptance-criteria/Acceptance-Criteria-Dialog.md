---
title: "Acceptance Criteria: Dialog"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2, APG dialog pattern
---

Dialogs inform users about a specific task and may contain critical information or require decisions. While open, focus must be trapped inside the dialog and background content must be inert.

**Backpack guidance:** skyscanner.design/latest/components/dialog/accessibility-kR5btbRR

---

## Labels and messaging

- The dialog has a visible title that communicates its purpose.
  - **WCAG 2.4.6** Headings and Labels
- The close button (if present) has a descriptive accessible name — e.g. "Close".
  - **WCAG 4.1.2** Name, Role, Value
- Non-dismissible dialogs require an explicit action to close — this must be keyboard operable.
  - **WCAG 2.1.1** Keyboard

---

## Semantic markup

- Use the native `<dialog>` element or apply `role="dialog"` with `aria-modal="true"`.
  - **WCAG 4.1.2** Name, Role, Value
- The dialog has an accessible name via `aria-labelledby` (pointing to the dialog title) or `aria-label`.
  - **WCAG 4.1.2** Name, Role, Value
- Background content is made inert while the dialog is open.
  - **WCAG 2.1.2** No Keyboard Trap

---

## Keyboard

- When the dialog opens, focus moves to the first focusable element inside it.
  - **WCAG 2.4.3** Focus Order
- Tab cycles through all focusable elements within the dialog only — focus does not escape to background content.
  - **WCAG 2.1.2** No Keyboard Trap
- Each element within the dialog has a visible focus state.
  - **WCAG 2.4.7** Focus Visible
- Pressing Escape dismisses the dialog (for dismissible dialogs) and returns focus to the trigger element.
  - **WCAG 2.1.1** Keyboard
- For non-dismissible dialogs, Escape does not close it — a specific action is required.
  - **WCAG 2.1.1** Keyboard
- When the dialog closes, focus returns to the element that opened it.
  - **WCAG 2.4.3** Focus Order

---

## Visual design

- Text meets 4.5:1 contrast (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Focus indicators meet 3:1 contrast.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The dialog can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Backpack)

- **NVDA + Chrome**: Dialog role and name announced on open — e.g. "Confirm booking, dialog". Focus confirmed on first focusable element. Background content not reachable. Close button announced as "Close, button". Focus returns to trigger on close.
- **VoiceOver + Safari**: Same. Announced as "web dialog".
- **VoiceOver iOS / TalkBack Android**: Dialog content navigable by swipe. Only dialog content reachable while open. Close button announced. Focus returns to trigger on close.
