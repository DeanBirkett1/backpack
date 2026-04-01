---
title: "Acceptance Criteria: Link"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Skyscanner link audit, WCAG 2.2
---

A link is an interactive element that navigates users to another resource, location, page, or state. Links should use descriptive text that communicates the destination without relying on surrounding context.

**Backpack guidance:** skyscanner.design/latest/components/link/accessibility-Kygb7tVd

---

## Backpack design notes

- **Descriptive text:** Links must describe their destination. Avoid "Read more…", "Click here", or similar. Where a short visible label is unavoidable, provide context in a visually hidden span or via `aria-label` (which must still contain the visible label text).
- **External links:** Opening a link in a new tab (`target="_blank"`) disrupts the browsing experience for screen reader users who may not be aware of the context change. Only open new tabs when it benefits the traveller. When a link opens in a new window, use an external link icon and include visually hidden text "opens in new window" for AT users.
- **Predictable navigation:** Links should open in the same tab wherever possible.

---

## Labels and messaging

- The link text describes where the link goes — not generic text such as "Read more" or "Click here".
  - **WCAG 2.4.4** Link Purpose (In Context)
- Where a non-descriptive visible label is unavoidable, additional context is provided in a visually hidden span or via `aria-label` (which must contain the visible label text).
  - **WCAG 2.4.4** Link Purpose (In Context) / **WCAG 2.5.3** Label in Name
- Links that open in a new tab communicate this in advance — e.g. via a visually hidden "opens in new window" text and an external link icon.
  - **WCAG 3.2.2** On Input / Best practice

---

## Semantic markup

- Links use the `<a>` element with a valid `href` attribute.
  - **WCAG 4.1.2** Name, Role, Value
- The link's accessible name matches its visible label exactly, or at minimum starts with the visible label text.
  - **WCAG 2.5.3** Label in Name
- The link's accessible name and role are present in the accessibility tree.
  - **WCAG 4.1.2** Name, Role, Value
- If the link represents the current page or step, this is communicated programmatically (e.g. `aria-current="page"`).
  - **WCAG 4.1.2** Name, Role, Value

---

## Keyboard

- The link is focusable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- The link is activated by pressing the Enter key.
  - **WCAG 2.1.1** Keyboard
- The link has a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible
- When the link receives keyboard focus it is not completely obscured by other content.
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)

---

## Visual design

- The link is visually distinguishable from surrounding plain text (e.g. underline, icon, or other non-colour indicator).
  - **WCAG 1.4.1** Use of Color — must not rely on colour alone
- Link text meets a minimum contrast ratio of 4.5:1 against its background (3:1 for large text).
  - **WCAG 1.4.3** Contrast (Minimum)
- If the link uses a custom focus style, the focus indicator meets a 3:1 contrast ratio against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast

---

## Adaptive UI

- Link text can be increased to 200% without truncation or content loss.
  - **WCAG 1.4.4** Resize Text
- Text spacing can be increased without text overlapping, truncating, or being cut off.
  - **WCAG 1.4.12** Text Spacing
- The link can be viewed at 320px viewport width without requiring horizontal scrolling.
  - **WCAG 1.4.10** Reflow
