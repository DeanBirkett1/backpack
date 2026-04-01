# Accessibility

## Commitment

Skyscanner targets **WCAG 2.2 Level AA** as the minimum conformance standard
across all digital products. This applies to web, iOS, and Android surfaces.

Relevant legislation: EN 301 549 (EAA), WCAG 2.2 (W3C).

---

## Assistive technology coverage

| Platform | AT | Browser |
|---|---|---|
| Web | NVDA | Chrome |
| Web | VoiceOver | Safari (macOS) |
| Web | JAWS | Chrome |
| iOS | VoiceOver | Safari |
| Android | TalkBack | Chrome |
| Cross-platform | Keyboard-only | Any |
| Cross-platform | Speech input (Dragon) | Any |

---

## Automated guardrails

Automated accessibility checking is part of the AI Validation Framework.
The accessibility sub-agent runs on PRs and feature launches and produces
per-finding output mapped to Jira custom fields.

Rules, thresholds, and Skyscanner-specific component rules are maintained
in `.claude/skills/skyscanner-a11y/rules.yaml` — editable by the accessibility
team without engineering support.

Automated tools cover approximately 30–40% of WCAG 2.2 criteria.
Manual AT testing is always required before sign-off on Tier Critical
and Tier High launches.

---

## Definition of Done (accessibility)

Before any component or feature is considered done:

- [ ] No WCAG 2.2 AA violations detected by automated scan
- [ ] Keyboard navigation tested — all interactive elements reachable and operable
- [ ] Visible focus indicator present on all interactive elements
- [ ] Tested with NVDA + Chrome and VoiceOver + Safari
- [ ] Touch targets meet 44×44pt minimum (iOS — Apple HIG) and 48×48dp minimum (Android — Material Design)
- [ ] Touch targets meet 24×24px minimum (WCAG 2.5.8)
- [ ] No colour-only information conveyance
- [ ] All images have appropriate alt text or are marked decorative
- [ ] Dynamic content changes announced via live regions where appropriate
- [ ] Animations respect reduced motion preference (`prefers-reduced-motion` on web; system setting on iOS/Android)
- [ ] Manual AT testing completed for any interaction-based pattern

**iOS and Android additional checks:**
- [ ] Dynamic Type tested on iOS — content readable and not truncated at larger text sizes
- [ ] TalkBack tested on Android for any native surface changes
- [ ] Non-text elements have content descriptions on native surfaces (`contentDescription` on Android, `accessibilityLabel` on iOS)

---

## Native platforms (iOS and Android)

Native iOS and Android surfaces follow WCAG 2.2 AA as the baseline,
interpreted through platform-specific implementation:

- **iOS:** [Apple Human Interface Guidelines — Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility)
- **Android:** [Material Design — Accessibility](https://m3.material.io/foundations/overview/principles)

Where HIG or Material intentionally diverge from WCAG, the platform
guideline takes precedence for native surfaces. Known examples are
documented in `.claude/skills/skyscanner-a11y/knowledge/native-platforms.md`.

Manual testing tools: Accessibility Inspector (iOS/Xcode), Accessibility Scanner (Android).
Automated native coverage is limited — Abra is used for additional native testing.

---

## AI agent skills

Skills live in `.claude/skills/` at the repo root.

| Task | Load skill |
|---|---|
| General accessibility question or code review | `.claude/skills/skyscanner-a11y/SKILL.md` |
| Backpack component review | `.claude/skills/backpack-a11y/SKILL.md` |
| Filing an accessibility bug report | `.claude/skills/skyscanner-a11y/skills/bug-reporting/SKILL.md` |

---

## Known gaps

- Mobile native (iOS/Android) automated coverage is limited — Abra and
  Accessibility Inspector are used for manual native testing
- Colour contrast is validated separately via the Backpack contrast script
  and is suppressed in automated scan output to avoid duplication

---

## Contacts

| Role | Owner |
|---|---|
| Accessibility lead | Heather Hepburn |
| Backpack design system | Gert-Jan Vercauteren |

---

*Last reviewed: April 2026 · Standard: WCAG 2.2 AA · Framework: EN 301 549*