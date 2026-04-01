---
title: "Acceptance Criteria: Graphic Promotion"
author: Skyscanner Accessibility
version: "1.0"
date: 2026-03-25
sources: Backpack accessibility tab, WCAG 2.2
---

The graphic promotion component creates narrative in the product, typically combining an image with overlaid text. Text placed over images must be readable at all zoom levels, viewport sizes, and text spacing settings.

**Backpack guidance:** skyscanner.design/latest/components/graphic-promotion/accessibility-Vtfnh0X0

---

## Backpack design notes

- **Reducing image complexity or adding a scrim** increases readability for users with colour vision impairments.
- **Text over images** must be tested at zoom (200%), narrow viewports, and with increased text spacing — the placement of text will change as the window reflows.
- **Consider the smallest size** before finalising designs — text must remain readable at the smallest supported viewport.
- Check live code, not just static designs, as font size changes and viewport changes affect the placement of overlaid text.

---

## Semantic markup

- Informative images have descriptive `alt` text.
  - **WCAG 1.1.1** Non-text Content
- Decorative images have empty `alt=""` and are hidden from the accessibility tree.
  - **WCAG 1.1.1** Non-text Content
- Heading hierarchy is maintained within the component.
  - **WCAG 1.3.1** Info and Relationships

---

## Visual design

- Text overlaid on images meets 4.5:1 contrast against the background (including image content beneath it).
  - **WCAG 1.4.3** Contrast (Minimum)
- Information is not conveyed by colour alone.
  - **WCAG 1.4.1** Use of Color

---

## Adaptive UI

- Text remains readable and accessible at 200% zoom without truncation or overlap.
  - **WCAG 1.4.4** Resize Text
- The component can be viewed at 320px without horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text spacing can be increased without text overlapping the image or other content.
  - **WCAG 1.4.12** Text Spacing
