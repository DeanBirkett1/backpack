# Native Platform Accessibility — iOS and Android

Reference for accessibility work on Skyscanner's native iOS and Android
surfaces. Covers where platform guidelines and WCAG differ, and
platform-specific implementation requirements.

---

## Authoritative sources

- **Apple HIG — Accessibility:** https://developer.apple.com/design/human-interface-guidelines/accessibility
- **Android Material — Accessibility:** https://m3.material.io/foundations/overview/principles
- **Android developer guide:** https://developer.android.com/guide/topics/ui/accessibility

WCAG 2.2 AA is the baseline for both platforms. Where platform guidelines
go further or differ, the platform guideline takes precedence for native
surfaces.

---

## iOS — key accessibility requirements

### Dynamic Type
Supporting Dynamic Type is mandatory for accessible iOS applications.
Text must scale when the user increases their system text size.

- Never hardcode font sizes — use Dynamic Type text styles
- Test at the largest accessibility text size (235% is the recommended
  test size — the nearest available to WCAG's 200% normative threshold)
- Layouts must reflow gracefully — content must not truncate or overlap
- Known Skyscanner issue: Dynamic Type caused metric regression when
  enabled app-wide due to unresolved layout failures at 235%

### Touch targets
- Minimum: 44×44pt (Apple HIG) — larger than WCAG's 24×24px minimum
- Apple's research shows targets below 44pt result in 25%+ tap error rates

### VoiceOver
- Use `accessibilityLabel` for non-text elements
- Use `accessibilityHint` for supplementary context
- Use `accessibilityTraits` for roles and states
- Test swipe navigation — VoiceOver navigates linearly through the
  accessibility tree, not via Tab key

### Where iOS intentionally diverges from WCAG
- **Card List grouping:** iOS Card List components intentionally omit
  container grouping — this follows Apple HIG and is expected behaviour.
  Do not flag as a defect. (Web Card List must use `<ul>` or `<ol>`.)
- **Switch role:** Native iOS switch controls are announced differently
  from web — this is platform-correct behaviour.

### Testing tools
- Accessibility Inspector (built into Xcode)
- VoiceOver on device (Settings → Accessibility → VoiceOver)
- Abra — used for Skyscanner native app testing

---

## Android — key accessibility requirements

### Touch targets
- Minimum: 48×48dp (Material Design / Android developer guidance)
- Material components (Checkbox, Switch) automatically add padding to
  meet this requirement in Jetpack Compose

### TalkBack
- Use `contentDescription` for non-text elements (icons, images)
- Set `contentDescription = null` for decorative elements
- Use `LiveRegion` properties to announce dynamic UI changes
- Test with Explore by Touch and linear swipe navigation

### Text scaling
- Use `sp` units for text (scales with user font size preferences)
- Use `dp` for dimensions
- Test at large system font size settings

### Where Android intentionally diverges from WCAG
- Navigation patterns follow Material conventions — bottom tab bars,
  navigation drawers — which differ from web navigation patterns
- Focus order follows visual layout top-to-bottom rather than DOM order

### Testing tools
- Accessibility Scanner (downloadable from Google Play)
- TalkBack on device (Settings → Accessibility → TalkBack)
- Abra — used for Skyscanner native app testing

---

## Platform comparison — key differences from web

| Concern | Web | iOS | Android |
|---|---|---|---|
| Touch target minimum | 24×24px (WCAG) | 44×44pt (HIG) | 48×48dp (Material) |
| Text scaling | `prefers-reduced-motion`, 200% resize | Dynamic Type | `sp` units, font scale |
| Screen reader | NVDA, VoiceOver, JAWS | VoiceOver | TalkBack |
| Non-text labelling | `alt`, `aria-label` | `accessibilityLabel` | `contentDescription` |
| Reduced motion | `prefers-reduced-motion` | Reduce Motion system setting | Remove animations system setting |
| List semantics | `<ul>/<ol>` with `role="list"` | Platform handles grouping | Platform handles grouping |