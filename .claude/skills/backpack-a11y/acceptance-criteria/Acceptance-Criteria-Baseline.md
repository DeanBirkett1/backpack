# Baseline Acceptance Criteria — All Backpack Components

These criteria apply to every Backpack component. They are not repeated
in individual component files — load this file alongside the component
file for a complete picture.

---

## Visual design

- Text meets a minimum contrast ratio of 4.5:1 against its background
  (3:1 for large text, 18pt+ or 14pt+ bold).
  - **WCAG 1.4.3** Contrast (Minimum)
- UI component boundaries and focus indicators meet 3:1 contrast against
  adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- Information is not conveyed by colour alone — always pair colour with
  text, icon, or pattern.
  - **WCAG 1.4.1** Use of Color
- Colour contrast is validated using the Backpack contrast script
  (`scripts/check-colour-contrast.js`) — do not assess manually.

---

## Adaptive UI

- Content is visible and operable at 320px viewport width without
  horizontal scrolling.
  - **WCAG 1.4.10** Reflow
- Text can be resized to 200% without truncation or content loss.
  - **WCAG 1.4.4** Resize Text
- Text spacing can be increased (line height 1.5×, letter spacing 0.12em,
  word spacing 0.16em) without text overlapping, truncating, or being cut
  off.
  - **WCAG 1.4.12** Text Spacing
- Touch targets meet a minimum of 24×24px (WCAG minimum). Recommended
  44×44pt on iOS.
  - **WCAG 2.5.8** Target Size (Minimum)

---

## Focus

- Every interactive element has a visible focus indicator when focused
  via keyboard.
  - **WCAG 2.4.7** Focus Visible
- The focus indicator meets 3:1 contrast against adjacent colours.
  - **WCAG 1.4.11** Non-text Contrast
- When an element receives keyboard focus it is not completely obscured
  by other content (e.g. sticky headers or overlays).
  - **WCAG 2.4.11** Focus Not Obscured (Minimum)

---

## Accessible naming

When a component element needs an accessible name, apply this hierarchy
in order — do not skip to a lower option if a higher one is available:

1. Native `<label for>` association — always first for form inputs
2. Visible text content already within the element
3. Visually hidden `<span class="bpk-visually-hidden">` appended inside
   the label — adds context without replacing visible text
4. `aria-labelledby` referencing visible text elsewhere on the page
5. `aria-label` — only when there is genuinely no visible text
   (e.g. icon-only buttons, landmark disambiguation)

Never use `aria-label` to replace or override visible text. This breaks
WCAG 2.5.3 for speech input users who speak what they see.

---

## Motion

- Animations and transitions are wrapped in
  `@media (prefers-reduced-motion: no-preference)` so they are opt-out
  by default.
  - **WCAG 2.3.3** Animation from Interactions (AAA — Skyscanner best
    practice)
- Auto-playing content has pause/stop controls.
  - **WCAG 2.2.2** Pause, Stop, Hide

---

## Notes for component file authors

Individual component acceptance criteria files should:

- Reference this file at the top: *"Baseline criteria apply — see
  `Acceptance-Criteria-Baseline.md`"*
- Include only what is **component-specific** — keyboard contracts,
  ARIA attributes, screen reader expectations, known quirks
- Not repeat the sections above unless the component has a specific
  variation that overrides or extends the baseline
