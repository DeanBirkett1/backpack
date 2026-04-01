# WCAG 2.2 Quick Reference — Skyscanner

Last reviewed: 2026-03-25

Skyscanner-relevant success criteria. Covers Level A and AA — the baseline for conformance. Level AAA criteria are noted separately where relevant to Skyscanner work. Use this as a quick lookup when identifying which criterion applies to a defect.

---

## Perceivable

| SC | Level | Name | What it means in practice |
|---|---|---|---|
| 1.1.1 | A | Non-text Content | All images, icons, and SVGs need alt text or `aria-hidden` |
| 1.3.1 | A | Info and Relationships | Semantic HTML — headings, lists, tables, labels, landmarks |
| 1.3.2 | A | Meaningful Sequence | Reading/DOM order matches visual order |
| 1.3.3 | A | Sensory Characteristics | Don't reference things by shape, colour, or position alone |
| 1.3.4 | AA | Orientation | Don't lock to portrait or landscape |
| 1.3.5 | AA | Identify Input Purpose | Use `autocomplete` attributes on personal data fields |
| 1.4.1 | A | Use of Colour | Don't use colour as the only way to convey information |
| 1.4.3 | AA | Contrast (Minimum) | 4.5:1 for normal text, 3:1 for large text (24px / 18.66px bold) |
| 1.4.4 | AA | Resize Text | Text must be resizable to 200% without loss of content |
| 1.4.10 | AA | Reflow | Content must work at 320px width without two-dimensional scrolling |
| 1.4.11 | AA | Non-text Contrast | UI components and focus indicators: 3:1 against adjacent colours |
| 1.4.12 | AA | Text Spacing | Content must not be lost when letter/word/line spacing is increased |
| 1.4.13 | AA | Content on Hover or Focus | Tooltips must be dismissible, hoverable, and persistent |

---

## Operable

| SC | Level | Name | What it means in practice |
|---|---|---|---|
| 2.1.1 | A | Keyboard | All functionality available by keyboard |
| 2.1.2 | A | No Keyboard Trap | Focus must never be trapped unexpectedly |
| 2.3.1 | A | Three Flashes | No content flashes more than 3 times per second |
| 2.4.1 | A | Bypass Blocks | Skip link to main content |
| 2.4.2 | A | Page Titled | Descriptive `<title>` on every page |
| 2.4.3 | A | Focus Order | Tab order follows logical reading order |
| 2.4.4 | A | Link Purpose | Link text describes its destination — no "click here" |
| 2.4.6 | AA | Headings and Labels | Headings and labels are descriptive |
| 2.4.7 | AA | Focus Visible | Keyboard focus indicator is always visible |
| 2.4.11 | AA | Focus Not Obscured (Min) | Focused element not fully hidden by sticky headers etc. |
| 2.5.3 | A | Label in Name | Accessible name must contain visible label text |
| 2.5.8 | AA | Target Size (Minimum) | Touch targets minimum 24×24px with adequate spacing |

**Note — 2.5.5 Target Size (Enhanced):** This criterion (44×44px) is **Level AAA**, not AA. It is not required for WCAG 2.2 AA conformance. However, 44×44pt remains the recommended minimum for iOS touch targets per Apple HIG, and 44×44px is a Skyscanner best practice for mobile.

---

## Understandable

| SC | Level | Name | What it means in practice |
|---|---|---|---|
| 3.1.1 | A | Language of Page | `<html lang>` set correctly |
| 3.1.2 | AA | Language of Parts | Lang attribute on content in a different language |
| 3.2.1 | A | On Focus | Focus doesn't trigger unexpected context changes |
| 3.2.2 | A | On Input | Input doesn't trigger unexpected context changes |
| 3.3.1 | A | Error Identification | Errors described in text, not just colour |
| 3.3.2 | A | Labels or Instructions | Form inputs have visible labels |
| 3.3.3 | AA | Error Suggestion | Error messages explain how to fix the issue |
| 3.3.4 | AA | Error Prevention | Important submissions are reversible or confirmable |

---

## Robust

| SC | Level | Name | What it means in practice |
|---|---|---|---|
| 4.1.2 | A | Name, Role, Value | All UI components have accessible name, role, states, and properties |
| 4.1.3 | AA | Status Messages | Status updates announced without receiving focus |

---

## Skyscanner-Specific Notes

- **1.4.10 Reflow** — test at 320px viewport width; flex/grid layouts must stack; no two-dimensional scrolling for text
- **1.4.13 Content on Hover or Focus** — directly relevant to tooltips; content must not disappear when the user moves the mouse over it
- **2.5.3 Label in Name** — `aria-label` must contain the visible label text; relevant to regional settings button, icon buttons
- **2.4.7 Focus Visible** — use `:focus-visible` not `:focus`; 3:1 contrast minimum for focus indicator
- **2.5.8 Target Size (Minimum)** — AA in WCAG 2.2 (24×24px minimum). For mobile, Skyscanner recommends 44×44pt (iOS) / 48×48dp (Android) as best practice, exceeding the WCAG minimum
- **4.1.3 Status Messages** — price updates, search results, loading states, filter results all require live regions
