---
title: "Acceptance Criteria: Card Button"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

The card button lets travellers share flights or save them for later. It appears as a compact button within or alongside a card.

**Backpack guidance:** skyscanner.design/latest/components/card-button/accessibility-thmQqVyX

---

## Backpack design notes

- **Style over images:** The "default" and "on dark" styles are transparent by design and should not be placed over images — they become difficult to see for people with low vision. Use the contained style over images.
- **Accessible labels:** For AT users, card buttons must have descriptive labels that convey meaning. Where multiple cards are on the page, annotate designs with what should be announced to distinguish between card buttons — e.g. "Save flight, London to Edinburgh, £89" rather than just "Save".
- **Target sizes:** Targets must be large enough for users with dexterity limitations. Follow Apple HIG (44×44pt) and Android Material Design (48×48dp) recommendations.

---

## Semantic markup

- Card buttons use the native `<button>` element.
  - **WCAG 4.1.2** Name, Role, Value
- The accessible name is descriptive and unique in context — not just "Save" when multiple cards are present.
  - **WCAG 2.4.6** Headings and Labels
- If the button uses an icon only, it has an `aria-label` that communicates its action in context.
  - **WCAG 4.1.2** Name, Role, Value
- The icon is hidden from the accessibility tree (`aria-hidden="true"`).
  - **WCAG 1.1.1** Non-text Content

---

## Keyboard

- The card button is reachable using the Tab key.
  - **WCAG 2.1.1** Keyboard
- Pressing Space or Enter activates the button.
  - **WCAG 2.1.1** Keyboard
- The button has a visible focus indicator.
  - **WCAG 2.4.7** Focus Visible

---

## Visual design

- The button meets a minimum contrast ratio of 3:1 against its background (accounting for placement over images or solid backgrounds).
  - **WCAG 1.4.11** Non-text Contrast
- Touch target meets a minimum of 24×24px — recommended 44×44pt (iOS) / 48×48dp (Android).
  - **WCAG 2.5.8** Target Size (Minimum)
