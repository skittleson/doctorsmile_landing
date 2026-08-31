# Design: Redesigned Locations Section

Date: 2026-08-31
Status: Approved (pending spec review)

## Context

`docs/index.html` currently renders "Our Locations" as a plain 3-column
Bootstrap-style grid (`.col-md-4`) with city name, address, and two phone
numbers (New Patients / Current Patients) per office. It's functional but
plain, and doesn't link out to the practice's real per-city marketing pages.

Reference for inspiration: https://skittleson.github.io/DrSmileOnline/location/
(a full Astro site with map-embedded location cards). We are **not** adopting
that architecture — this site stays a single static `index.html`, no build
step, no new runtime dependencies (README: "Lighthouse 100/100/100/100").

## Goals

1. Redesign the Locations section as styled cards (not a plain grid of text),
   matching the existing brand (red `#a71b29`, Gotham Book font, existing
   spacing conventions) — no new colors/fonts/dependencies.
2. Add a one-line service blurb and real practice hours per card.
3. Add a "More Info" link per card to the practice's real per-city page.
4. Add GA4 click tracking on all three card actions (Call, Directions, More
   Info) using the site's existing `gtag.js`.
5. Mobile-optimized: comfortable single-column stack on phones, no cramped
   tap targets, no horizontal scroll.
6. Keep `llms.txt`, `index.md`, and `.well-known/ai-catalog.json` in sync
   with the new richer card content (blurbs, hours, more-info links).

## Non-goals

- No embedded Google Maps iframes (rejected in favor of a lighter, zero
  dependency "Directions" link that opens Google Maps — Option B from the
  brainstorm).
- No build step / static site generator.
- No changes to the practice-chooser panels section above Locations.
- No new/duplicate El Segundo landing page (there isn't one — see below).

## Data (verified against live sites, 2026-08-30/31)

| City | Address | Primary phone (New Patients) | Secondary phone (Current Patients) | Blurb | More Info URL |
|---|---|---|---|---|---|
| El Segundo, CA | 11976 Aviation Blvd., El Segundo, CA 90304 | 310-341-4788 | 310-643-6221 | General & family dentistry, oral surgery | `https://toothopiadental.com/contact-us/` |
| Lomita, CA | 2104 Pacific Coast Hwy., Lomita, CA 90717 | 310-878-9532 | 310-539-1111 | Gum care, veneers & full-mouth restoration | `https://doctorsmileonline.com/dentist-lomita/` |
| San Pedro, CA | 1622 S Gaffey St, San Pedro, CA 90731 | 310-961-4222 | 310-548-8128 | Family care, implants & emergency dentistry | `https://doctorsmileonline.com/dentist-san-pedro/` |
| Torrance, CA | 24667 Crenshaw Blvd. #D, Torrance, CA 90505 | 310-341-4783 | 310-325-8555 | Family dentistry, Invisalign & same-day care | `https://doctorsmileonline.com/dentist-torrance/` |
| Corona Del Mar (Newport), CA | 2121 East Coast Hwy STE 140, Corona Del Mar, CA 92625 | (949) 640-0222 | *(none — single number)* | Cosmetic dentistry, veneers & All-on-Four implants | `https://doctorsmileonline.com/dentist-newport/` |

**Hours (shared across all 5 cards, real data — not a placeholder):**
Mon–Fri: 8:00am–6:00pm · Sat/Sun: by appointment only.
Source: doctorsmileonline.com `/dentist-san-pedro/` "Our Availability" block
and `research.md:81`. This is doctorsmileonline.com's stated hours, applied
uniformly; it has not been independently verified per-office and may not be
100% accurate for El Segundo (a separate practice/site, Toothopia Dental).

**El Segundo "More Info" link — verified 2026-08-31:** `drsmiledental.com`
redirects to Toothopia Dental, a rebranded practice site. Toothopia has no
El Segundo-specific page, but the *same physical office* (11976 Aviation
Blvd) is still listed on their site — just relabeled from "El Segundo" to
"Inglewood" (both share ZIP 90304). Legacy "El Segundo" artifacts remain
throughout Toothopia's site (photo filenames, Yelp slug, an `info.es@` email
prefix, and an "Areas We Served" list that still names El Segundo), so this
is clearly the same office, rebranded rather than closed.

The card's More Info link points to `https://toothopiadental.com/contact-us/`
— the cleanest page with both Toothopia office addresses/phones and the
"Areas We Served" mention of El Segundo. (The bare homepage buries this
info in the footer.)

**Known phone number discrepancy (flagged, not corrected in this pass):**
Toothopia's current site lists the Aviation Blvd office's phone as
**310-643-6221 only** (our "Current Patients" number) — our "New Patients"
number, **310-341-4788, does not appear anywhere on Toothopia's current
site**. It may be disconnected or simply dropped during the rebrand. Per
user decision, this redesign displays our existing data as-is (not
independently re-verified/corrected) — flagging here for a future pass to
confirm with the practice whether 310-341-4788 still rings anywhere.

## Visual design

Card grid, one card per office, matching the mockup approved in the
brainstorm session (`.superpowers/brainstorm/.../location-card-final.html`):

- City name: red (`#a71b29`), uppercase, Gotham Book — same treatment as the
  current `.loc h3`.
- One-line blurb: small muted gray text under the city name.
- Address: tappable link — `href="https://www.google.com/maps/search/?api=1&query=<url-encoded address>"`,
  `target="_blank" rel="noopener noreferrer"`. This link is the "Directions"
  action.
- Primary phone: large, bold, red, `tel:` link — the "Call" action.
- Secondary phone (where present): smaller muted line below the primary
  phone, labeled "Current patients: ###-###-####", also a `tel:` link.
  Omitted entirely for Corona Del Mar (single-number office).
- Hours line: small muted text.
- Action row: Call (solid red button) / Directions (outline button) /
  More Info (outline button) — three buttons matching the site's existing
  red brand, no new button styles invented from scratch beyond what's needed.

Card container: white background, light border, subtle box-shadow, rounded
corners (`border-radius`) — a modest lift over the current plain-text rows,
consistent with a clean, uncluttered dental-practice aesthetic.

## Layout / responsive behavior

Grid breakpoints (matches the site's existing breakpoint values used
elsewhere in `index.html`, e.g. `@media (min-width: 768px)` /
`@media (min-width: 992px)`):

- **< 768px (phone):** 1 column, full-width cards, stacked top to bottom.
- **768–991px (tablet):** 2 columns.
- **≥ 992px (desktop):** 3 columns (matches the current `.col-md-4` intent).

Mobile-specific requirements:

- Card action buttons (Call / Directions / More Info): `min-height: 44px`
  (WCAG/Apple minimum touch target). Below ~400px viewport width, the three
  buttons stack to a single column within the card instead of a cramped
  3-across row.
- Primary phone `tel:` link has generous padding, not just underlined text,
  so it's an easy, forgiving tap target on a real thumb.
- Cards are `width: 100%` inside the existing `.container` — no horizontal
  scroll or overflow at any width.
- No new font sizes below 12px; body/label text stays legible without
  pinch-zoom, consistent with the current page's mobile treatment
  (`@media screen and (min-width: 320px) and (max-width: 768px)` block).

Verification: after implementation, use the `browse` skill to render the
page at phone (375px), tablet (768px), and desktop (1200px) widths and
confirm layout, tap targets, and no overflow — not just described in this
spec but actually checked.

## GA4 tracking

Single shared inline click handler (no new script file, reuses the
`gtag.js` already loaded in `<head>`):

```js
function trackLocationClick(city, linkType, url) {
  if (typeof gtag === 'function') {
    gtag('event', 'location_click', {
      location_city: city,
      link_type: linkType,       // 'call' | 'directions' | 'more_info'
      link_url: url,
      transport_type: 'beacon'   // fire-and-forget before navigation
    });
  }
}
```

Every Call / Directions / More Info `<a>` gets an `onclick` calling this
function with its city, link type, and destination URL before the browser
navigates. Single event name (`location_click`) with a `link_type`
dimension keeps GA4 reporting simple — one event, filterable three ways.

## Files touched

- `docs/index.html` — replace the Locations section markup + add card CSS
  in the existing `<style>` block + add the `trackLocationClick` function.
- `docs/llms.txt` — location table gets blurb + hours columns; add More Info
  links to the "Related" section.
- `docs/index.md` — each location section gets its blurb, hours, and a
  "More Info" link added.
- `docs/.well-known/ai-catalog.json` — no structural change needed (it
  indexes documents, not individual locations); leave as-is unless review
  surfaces a reason to add per-location resource entries.

## Testing / acceptance

- Visual check via `browse` skill at 375px / 768px / 1200px widths.
- Manual check: every `tel:` link, every Maps directions link, and every
  More Info link resolves to the correct destination (cross-check against
  the data table above).
- `python3 -m json.tool docs/.well-known/ai-catalog.json` still validates
  (if touched).
- No new console errors; `gtag` calls guarded by `typeof gtag === 'function'`
  so nothing breaks if analytics is blocked.
- Existing Lighthouse 100/100/100/100 is not regressed (no new
  render-blocking resources, no layout shift from the card redesign).
