---
title: "Acceptance Criteria Index"
author: Skyscanner Accessibility
version: "2.0"
date: 2026-03-25
---

# Skyscanner Accessibility — Acceptance Criteria Index

Maps Backpack components to their acceptance criteria files. Before reviewing or building any component, locate its file below and read it first.

All paths are relative to `.claude/skills/a11y-review/acceptance-criteria/`.

All components with a Backpack accessibility tab on skyscanner.design have been incorporated. Last verified: 2026-03-25.

---

## Component index

| Component | File | Backpack tab |
|---|---|---|
| Accordion | `Acceptance-Criteria-Accordion.md` | ✅ |
| Breadcrumb | `Acceptance-Criteria-Breadcrumb.md` | ✅ |
| Button | `Acceptance-Criteria-Button.md` | ✅ |
| Calendar | `Acceptance-Criteria-Calendar.md` | ✅ |
| Card Button | `Acceptance-Criteria-Card-Button.md` | ✅ |
| Card List | `Acceptance-Criteria-Card-List.md` | ✅ |
| Carousel | `Acceptance-Criteria-Carousel.md` | ✅ (page empty — WCAG/APG used) |
| Checkbox | `Acceptance-Criteria-Checkbox.md` | ✅ |
| Chip | `Acceptance-Criteria-Chip.md` | ✅ |
| Content Cards | `Acceptance-Criteria-Content-Cards.md` | ✅ |
| Date Picker | `Acceptance-Criteria-Date-Picker.md` | ✅ |
| Dialog | `Acceptance-Criteria-Dialog.md` | ✅ |
| Field Set | `Acceptance-Criteria-Field-Set.md` | ✅ |
| Graphic Promotion | `Acceptance-Criteria-Graphic-Promotion.md` | ✅ |
| Info Banner | `Acceptance-Criteria-Info-Banner.md` | ✅ |
| Inset Banner | `Acceptance-Criteria-Inset-Banner.md` | ✅ |
| Link | `Acceptance-Criteria-Link.md` | ✅ |
| List | `Acceptance-Criteria-List.md` | ✅ |
| Modal Dialog | `Acceptance-Criteria-Modal-Dialog.md` | — (maps to Dialog) |
| Nudger | `Acceptance-Criteria-Nudger.md` | ✅ |
| Page Indicator | `Acceptance-Criteria-Page-Indicator.md` | ✅ |
| Pagination | `Acceptance-Criteria-Pagination.md` | ✅ |
| Phone Input | `Acceptance-Criteria-Phone-Input.md` | ✅ |
| Price | `Acceptance-Criteria-Price.md` | ✅ |
| Radio Button | `Acceptance-Criteria-Radio-Button.md` | ✅ |
| Select | `Acceptance-Criteria-Select.md` | ✅ |
| Skip Link | `Acceptance-Criteria-Skip-Link.md` | ✅ |
| Swap Button | `Acceptance-Criteria-Swap-Button.md` | ✅ |
| Switch | `Acceptance-Criteria-Switch.md` | ✅ |
| Tabs | `Acceptance-Criteria-Tabs.md` | — (no Backpack tab) |
| Toggletip | `Acceptance-Criteria-Toggletip.md` | — (no Backpack tab) |
| Tooltip | `Acceptance-Criteria-Tooltip.md` | ✅ |

---

## Components not yet covered

The following Backpack components do not yet have criteria files. Apply general WCAG 2.2 principles and flag the gap when reviewing these:

- Autosuggest
- Banner Alert
- Bottom Sheet / Drawer
- Horizontal Navigation / Navigation Tab Group
- Popover
- Progress Bar
- Segmented Control
- Skeleton
- Spinner
- Star Rating / Rating
- Text Input
- Toast

When a component is not listed, say: *"No acceptance criteria file found for [component]. I will apply general WCAG 2.2 principles — this component should be added to the index."*

---

## How to use this index

1. Identify the component being reviewed or built.
2. Open the matching criteria file.
3. Work through each section: Backpack design notes (where present), Labels and messaging, Semantic markup, Keyboard, Visual design, Adaptive UI.
4. For components not listed, apply `knowledge-notes/wcag-quick-ref.md` and flag the gap.
