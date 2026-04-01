---
name: backpack-a11y
description: >
  Load this skill when working on any Backpack component — reviewing code,
  writing acceptance criteria, assessing a PR, or checking a Storybook story.
  Always load the general skyscanner-a11y skill first, then load this skill
  on top. This skill adds Backpack component contracts, design system patterns,
  and Storybook guidance to the general accessibility foundation.
owner: Gert-Jan Vercauteren
version: "1.0.0"
last_reviewed: 2026-04-01
---

# Backpack Accessibility Skill

## How to use this skill

This skill extends `skyscanner-a11y/SKILL.md`. Load the general skill
first — this skill adds Backpack-specific component contracts on top.

---

## Component acceptance criteria

Load the relevant acceptance criteria file for the component you are
working on. These files contain:

- Keyboard interaction contracts
- Expected screen reader announcements
- ARIA attributes required
- Known AT quirks for this component
- Backpack-specific design notes

**Index of components with acceptance criteria:**

| Component | File |
|---|---|
| Accordion | `acceptance-criteria/Acceptance-Criteria-Accordion.md` |
| Breadcrumb | `acceptance-criteria/Acceptance-Criteria-Breadcrumb.md` |
| Button | `acceptance-criteria/Acceptance-Criteria-Button.md` |
| Calendar | `acceptance-criteria/Acceptance-Criteria-Calendar.md` |
| Card Button | `acceptance-criteria/Acceptance-Criteria-Card-Button.md` |
| Card List | `acceptance-criteria/Acceptance-Criteria-Card-List.md` |
| Carousel | `acceptance-criteria/Acceptance-Criteria-Carousel.md` |
| Checkbox | `acceptance-criteria/Acceptance-Criteria-Checkbox.md` |
| Chip | `acceptance-criteria/Acceptance-Criteria-Chip.md` |
| Content Cards | `acceptance-criteria/Acceptance-Criteria-Content-Cards.md` |
| Date Picker | `acceptance-criteria/Acceptance-Criteria-Date-Picker.md` |
| Dialog | `acceptance-criteria/Acceptance-Criteria-Dialog.md` |
| Field Set | `acceptance-criteria/Acceptance-Criteria-Field-Set.md` |
| Graphic Promotion | `acceptance-criteria/Acceptance-Criteria-Graphic-Promotion.md` |
| Info Banner | `acceptance-criteria/Acceptance-Criteria-Info-Banner.md` |
| Inset Banner | `acceptance-criteria/Acceptance-Criteria-Inset-Banner.md` |
| Link | `acceptance-criteria/Acceptance-Criteria-Link.md` |
| List | `acceptance-criteria/Acceptance-Criteria-List.md` |
| Modal Dialog | `acceptance-criteria/Acceptance-Criteria-Modal-Dialog.md` |
| Nudger | `acceptance-criteria/Acceptance-Criteria-Nudger.md` |
| Page Indicator | `acceptance-criteria/Acceptance-Criteria-Page-Indicator.md` |
| Pagination | `acceptance-criteria/Acceptance-Criteria-Pagination.md` |
| Phone Input | `acceptance-criteria/Acceptance-Criteria-Phone-Input.md` |
| Price | `acceptance-criteria/Acceptance-Criteria-Price.md` |
| Radio Button | `acceptance-criteria/Acceptance-Criteria-Radio-Button.md` |
| Select | `acceptance-criteria/Acceptance-Criteria-Select.md` |
| Skip Link | `acceptance-criteria/Acceptance-Criteria-Skip-Link.md` |
| Swap Button | `acceptance-criteria/Acceptance-Criteria-Swap-Button.md` |
| Switch | `acceptance-criteria/Acceptance-Criteria-Switch.md` |
| Tabs | `acceptance-criteria/Acceptance-Criteria-Tabs.md` |
| Toggletip | `acceptance-criteria/Acceptance-Criteria-Toggletip.md` |
| Tooltip | `acceptance-criteria/Acceptance-Criteria-Tooltip.md` |

If the component is not listed, apply the general accessibility skill
and note the gap.

---

## Backpack design system rules

These apply to all Backpack component work and extend the Skyscanner
general rules.

### Component patterns

**BpkButton**
- Primary, secondary, destructive, and link variants all need accessible names
- Icon-only buttons must have `aria-label` — never rely on the icon alone
- Loading state must announce "loading" to AT — use visually hidden text
  or `aria-label` update, not just a spinner

**BpkCheckbox / BpkCheckboxV2**
- BpkSwitch announces as "checkbox" — expected, do not flag
- Explicit `aria-labelledby` overrides native `<label for>` — only use
  when the native association produces an incorrect computed name
- Strikethrough price text (e.g. "from £21") is not announced — always
  ensure visually hidden text conveys the full label including price context

**BpkCalendar / BpkDatepicker**
- Date cells must use `aria-selected`, not `aria-pressed`
- Focus must be managed between calendar steps
- Month/year navigation must announce the new month heading

**BpkNudger**
- Value changes must be announced on each increment/decrement
- Accessible name must describe what is being counted (e.g. "Adults")
- Min/max boundary should be communicated when reached

**BpkInfoBanner**
- Icon conveys type (information/warning/error/success)
- Icon must be `aria-hidden="true"`
- Type must be communicated via visually hidden text alongside the message

**BpkCardList**
- Web: wrap cards in `<ul>` or `<ol>`; add `role="list"` if
  `list-style: none` is applied
- iOS: no container grouping — this is intentional per Apple HIG, do not flag

**BpkTabs**
- Must use `role="tablist"`, `role="tab"`, `role="tabpanel"`
- Arrow key navigation within the tab list
- `aria-selected="true"` on active tab
- `aria-controls` linking tab to panel

**BpkDialog / BpkModal**
- Focus moves into dialog on open
- Focus is trapped within dialog while open
- Escape closes the dialog
- Focus returns to the trigger element on close
- `aria-labelledby` pointing to the dialog heading

### Colour contrast

Colour contrast is validated separately by the Backpack contrast script:
```bash
node scripts/check-colour-contrast.js
```

Do not manually assess contrast — run the script. It is suppressed in
the automated sub-agent scan to avoid duplication.

### Visually hidden pattern

Use the `BpkVisuallyHidden` component or the `.bpk-visually-hidden`
utility class — not inline styles. Inline visually-hidden styles are
a Low severity finding (engineering quality issue, no direct WCAG
failure, but prevents consistent auditing at scale).

---

## Storybook

When reviewing or writing Storybook stories for Backpack components,
load `knowledge/storybook-format.md` for structure and conventions.

Every Backpack component story should include:
- A default story showing the standard accessible state
- A state story showing disabled, error, and loading variants where applicable
- An `a11y` parameter block identifying any known AT quirks

---

## Definition of Done (Backpack component)

Before a new or modified Backpack component is merged:

- [ ] Acceptance criteria file exists in `.claude/backpack-a11y/acceptance-criteria/`
- [ ] Keyboard contract documented and tested
- [ ] Screen reader announcements verified (NVDA+Chrome, VoiceOver+Safari)
- [ ] Contrast script passes
- [ ] Storybook story includes accessible default state
- [ ] No WCAG 2.2 AA violations in automated scan

---

## Contacts

- Design system: Gert-Jan Vercauteren
- Accessibility: Heather Hepburn
