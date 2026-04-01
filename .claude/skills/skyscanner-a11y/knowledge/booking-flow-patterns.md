# Booking Flow & Skyscanner-Specific Patterns

Reference for `a11y-review`. Patterns specific to Skyscanner travel booking interfaces and Backpack components.

Last reviewed: 2026-03-25 | Applies to: Backpack web components

---

## Date Picker

- Use `role="grid"` for the calendar grid
- Use `aria-selected` on selected dates — not `aria-pressed`
- Disabled dates must be announced as unavailable/dimmed
- Arrow keys navigate between dates within the grid
- After date selection, focus must move to the next logical step (e.g. return date input or passenger selector)
- Escape closes the calendar without selection and returns focus to the input
- Month/year navigation buttons must have descriptive accessible names

---

## Passenger Counters / Number Steppers

- Announce the current value on every change
- Use a live region (`role="status"`) or update the accessible name of the counter
- Decrement button must be disabled (not just visually inactive) when at minimum value, or announce that the minimum has been reached
- Each stepper must be clearly associated with its label (e.g. "Adults 18+", "Children 2–17")
- Use `<fieldset>` + `<legend>` to group related steppers

---

## Flight Card Results

- Each flight card must have a meaningful heading — not just a price
- Price must be announced in context (route + price together), not as a standalone number
- Multi-segment journeys: each leg should be in a distinct labelled group
- Interactive cards: use the stretched pseudo-element pattern (see below)
- Do not rely on colour alone to distinguish fare tiers or availability

---

## Interactive Cards — Stretched Link / Pseudo-Element Pattern

When a card surface is interactive (the whole card is clickable) but also contains secondary interactive elements:

**The correct pattern (Heydon Pickering):**
- The primary action is a heading link (`<a>`) or primary button
- Apply `::after { content: ""; position: absolute; inset: 0; }` to the primary link/button
- The card container has `position: relative`
- Secondary interactive elements (e.g. "Save", "Share") use `position: relative` to sit above the pseudo-element

```html
<article style="position: relative;">
  <h3>
    <a href="/flight/123" class="card-primary-link">
      London to Edinburgh — £89
    </a>
  </h3>
  <button style="position: relative;">Save flight</button>
</article>
```

```css
.card-primary-link::after {
  content: "";
  position: absolute;
  inset: 0;
}
```

This pattern works identically whether the heading is visible or visually hidden. Do not make the card wrapper itself an interactive element — this creates nested interactivity problems.

---

## Fare Comparison Tables

- Use native `<table>` with `<th scope="col">` for column headers and `<th scope="row">` for row headers
- Never rely on colour alone to distinguish fare tiers (Economy, Business, First)
- Provide text labels for each tier in addition to any colour coding
- `<caption>` should describe the table purpose

---

## Multi-Segment Journeys

- Each flight leg should be in a distinct, labelled group
- Use `<section aria-label="Outbound flight">` or `<fieldset><legend>Outbound flight</legend>`
- Screen reader users must be able to understand which information belongs to which leg without visual context

---

## Search Results and Filters

- When search results update, announce the result count via a polite live region
- When a filter is applied, announce the updated result count
- Loading states: use `aria-busy="true"` on the updating region, or `role="status"` with a "Loading" message
- Sort controls: the current sort order should be communicated to AT

---

## Regional Settings / Currency / Language Controls

- The accessible name must communicate all current values and their labels
- Example: "Regional settings: Language English (UK), Country/region United Kingdom, Currency £ GBP"
- A generic name like "English (UK) - United Kingdom - £ GBP" fails 2.4.6 Headings and Labels and 4.1.2 Name, Role, Value
- This is a recurring defect in Skyscanner — check every instance

---

## Skip Link Pattern

Every full page must include a skip link as the first focusable element:

```html
<header>
  <a href="#maincontent" class="sr-only">Skip to main content</a>
  <!-- header content -->
</header>
<main id="maincontent" tabindex="-1">
  <h1>Page title</h1>
</main>
```

```css
.sr-only:not(:focus):not(:active) {
  clip: rect(0 0 0 0);
  clip-path: inset(50%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}
```

The `tabindex="-1"` on `<main>` allows programmatic focus to land there when the skip link is activated.
