---
title: "Acceptance Criteria: Inset Banner"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Skyscanner inset banner audit, WCAG 2.2
---

An inset banner is an inline informational component. It may be static (text only) or interactive (containing a button that opens a dialog/popover with additional information).

**Backpack guidance:** skyscanner.design/latest/components/inset-banner/accessibility-69ZM2R6M

---

## Labels and messaging

- If the banner contains an interactive element, the button has a descriptive accessible name (e.g. "More info").
  - **WCAG 4.1.2** Name, Role, Value
- The banner's informational content is available to assistive technology users, not just visual users.
  - **WCAG 1.3.1** Info and Relationships

---

## Semantic markup

- Static banners use an appropriate landmark or ARIA role to convey their nature (e.g. `role="note"` or `role="status"` if appropriate).
  - **Best practice**
- Interactive trigger buttons use `<button>` with a descriptive accessible name.
  - **WCAG 4.1.2** Name, Role, Value
- If the button opens a dialog, the dialog has `role="dialog"` (or uses the native `<dialog>` element), `aria-modal="true"`, and an accessible name via `aria-label` or `aria-labelledby`.
  - **WCAG 4.1.2** Name, Role, Value
- The dialog has a close button with a descriptive accessible name (e.g. "Close").
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- If the banner contains an interactive button, it is reachable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- Pressing Enter or Space on the trigger button opens the dialog.
  - **WCAG 2.1.1** Keyboard
- When the dialog opens, focus moves to the first focusable element inside it.
  - **WCAG 2.4.3** Focus Order
- Tab cycles through all interactive elements within the dialog only (focus trap).
  - **WCAG 2.1.2** No Keyboard Trap — intentional, escapable modal trap
- Pressing Escape or activating the close button closes the dialog and returns focus to the trigger button.
  - **WCAG 2.1.1** Keyboard / **WCAG 2.4.3** Focus Order
- All interactive elements have a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- All text meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- Status or type of banner (e.g. info, warning) is not conveyed by colour alone.
  - **WCAG 1.4.1** Use of Color
- Focus indicators meet a 3:1 contrast ratio against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- The banner can be viewed at 320px viewport width without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be increased to 200% without truncation or content loss.
  - **WCAG 1.4.4** Resize Text

---

## Screen reader expectations (Skyscanner audit)

- **NVDA + Chrome**: Trigger button announced as "More info, button". Dialog announced on open — e.g. "Info, dialog". Focus confirmed within dialog. Close button announced as "Close, button". Focus returns to trigger on close.
- **VoiceOver + Safari**: Trigger announced as "More info, button". Dialog announced as "Info, web dialog". Close button announced as "Close, button". Focus returns to trigger on close.
- **VoiceOver iOS / TalkBack Android**: Trigger announced via swipe. Dialog content navigable by swipe. Only dialog content reachable while open. Close button announced as "Close, button".
