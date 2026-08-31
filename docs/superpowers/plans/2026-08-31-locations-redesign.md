# Locations Section Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the plain 3-column text grid in the "Our Locations" section
of `docs/index.html` with styled, mobile-optimized cards (city, blurb,
address→directions link, phone(s), hours, More Info link), instrumented with
GA4 click tracking, and keep `llms.txt` / `index.md` in sync.

**Architecture:** Single static `index.html`, no build step, no new runtime
dependencies. Card markup replaces the existing `.row.loc` / `.col-md-4`
grid; new CSS rules added to the existing inline `<style>` block; one small
inline `<script>` function (`trackLocationClick`) added for GA4. Companion
files (`llms.txt`, `index.md`) updated by hand to match.

**Tech Stack:** Plain HTML/CSS/JS (ES5-compatible, no build tooling), Google
`gtag.js` (already loaded), GitHub Pages static hosting.

## Global Constraints

- No build step, no new npm/JS dependencies, no new fonts/colors — reuse
  `#a71b29` (brand red) and `'Gotham Book', sans-serif` exclusively.
- No embedded Google Maps iframes — "Directions" is a link to
  `https://www.google.com/maps/search/?api=1&query=<encoded address>`,
  opened in a new tab (`target="_blank" rel="noopener noreferrer"`).
- Grid breakpoints must match the site's existing values: `< 768px` = 1
  column, `768–991px` = 2 columns, `≥ 992px` = 3 columns.
- All tappable buttons (Call / Directions / More Info) must have
  `min-height: 44px`. Below ~400px viewport width the three buttons in a
  card stack to a single column instead of 3-across.
- No new body/label font size below `12px`.
- GA4 tracking must reuse the existing `gtag.js` already loaded in
  `<head>` — no new script tag, guard every call with
  `typeof gtag === 'function'`.
- Every `tel:`, Maps-directions, and More-Info URL must exactly match the
  Data table in
  `docs/superpowers/specs/2026-08-31-locations-redesign-design.md`.
- Existing Lighthouse 100/100/100/100 must not regress (no new
  render-blocking resources, no added layout shift).

---

### Task 1: Add card CSS to the existing `<style>` block

**Files:**
- Modify: `docs/index.html:210-217` (insert new rules right after the
  existing `.xs-flex-fix` rule, before the closing `</style>` tag at
  line 217)

**Interfaces:**
- Produces: CSS classes `.loc-grid`, `.loc-card`, `.loc-card h3`,
  `.loc-card .loc-blurb`, `.loc-card .loc-addr`, `.loc-card .loc-phone`,
  `.loc-card .loc-phone-secondary`, `.loc-card .loc-hours`,
  `.loc-card .loc-actions`, `.loc-card .loc-btn`, `.loc-card .loc-btn.solid`
  — consumed by Task 3's markup.

- [ ] **Step 1: Insert the new CSS rules**

Insert immediately after line 211 (`.xs-flex-fix { max-width: 50%; }`) and
before line 213 (the `@media screen and (min-width: 320px)...` block):

```css
        .loc-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 24px;
            margin-top: 20px;
        }

        @media (min-width: 768px) {
            .loc-grid { grid-template-columns: repeat(2, 1fr); }
        }

        @media (min-width: 992px) {
            .loc-grid { grid-template-columns: repeat(3, 1fr); }
        }

        .loc-card {
            background: #fff;
            border: 1px solid #e2e2e2;
            border-radius: 8px;
            box-shadow: 0 2px 6px rgba(0,0,0,0.08);
            padding: 20px 20px 18px;
            box-sizing: border-box;
        }

        .loc-card h3 {
            font-family: 'Gotham Book', sans-serif;
            color: #a71b29;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-size: 17px;
            font-weight: normal;
            margin: 0 0 8px;
            text-align: left;
        }

        .loc-card .loc-blurb {
            color: #666;
            font-size: 13px;
            line-height: 1.4;
            margin: 0 0 10px;
        }

        .loc-card .loc-addr {
            color: #333;
            font-size: 13px;
            line-height: 1.4;
            margin: 0 0 10px;
        }

        .loc-card .loc-addr a { color: #333; text-decoration: none; }
        .loc-card .loc-addr a:hover { text-decoration: underline; }

        .loc-card .loc-phone {
            display: inline-block;
            font-size: 18px;
            font-weight: bold;
            color: #a71b29;
            text-decoration: none;
            padding: 6px 0;
        }

        .loc-card .loc-phone-secondary {
            display: block;
            font-size: 12px;
            color: #888;
            margin-top: 2px;
        }

        .loc-card .loc-phone-secondary a { color: #888; text-decoration: none; }
        .loc-card .loc-phone-secondary a:hover { text-decoration: underline; }

        .loc-card .loc-hours {
            font-size: 12px;
            color: #777;
            margin: 10px 0 14px;
        }

        .loc-card .loc-actions {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
        }

        .loc-card .loc-btn {
            flex: 1 1 auto;
            min-width: 90px;
            min-height: 44px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 8px 10px;
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            border: 1px solid #a71b29;
            color: #a71b29;
            border-radius: 4px;
            text-decoration: none;
            box-sizing: border-box;
        }

        .loc-card .loc-btn.solid {
            background: #a71b29;
            color: #fff;
        }

        @media (max-width: 400px) {
            .loc-card .loc-actions { flex-direction: column; }
            .loc-card .loc-btn { width: 100%; }
        }
```

- [ ] **Step 2: Verify the file is still valid HTML**

Run:
```bash
python3 -c "import html.parser; html.parser.HTMLParser().feed(open('docs/index.html').read())" && echo "PARSE OK"
```
Expected output: `PARSE OK` (this only checks for gross parser errors —
full validation happens visually in Task 4).

- [ ] **Step 3: Commit**

```bash
git add docs/index.html
git commit -m "Add location card CSS (grid, cards, buttons, mobile breakpoints)"
```

---

### Task 2: Add the `trackLocationClick` GA4 helper function

**Files:**
- Modify: `docs/index.html` — insert a new `<script>` block immediately
  before the closing `</body>` tag. (Locate by content — Task 1's edit
  shifts line numbers, so don't rely on line numbers from before Task 1.)

**Interfaces:**
- Produces: global function `trackLocationClick(city, linkType, url)` —
  consumed by every Call/Directions/More-Info anchor's `onclick` in Task 3.
  Signature: `trackLocationClick(city: string, linkType: 'call'|'directions'|'more_info', url: string): void`

- [ ] **Step 1: Insert the script block**

Insert immediately before `</body>`:

```html
<script>
    function trackLocationClick(city, linkType, url) {
        if (typeof gtag === 'function') {
            gtag('event', 'location_click', {
                location_city: city,
                link_type: linkType,
                link_url: url,
                transport_type: 'beacon'
            });
        }
    }
</script>
```

- [ ] **Step 2: Verify no JS syntax errors**

Run:
```bash
node -e "
const fs = require('fs');
const html = fs.readFileSync('docs/index.html', 'utf8');
const match = html.match(/<script>\s*function trackLocationClick[\s\S]*?<\/script>/);
if (!match) { console.error('FAIL: script block not found'); process.exit(1); }
eval(match[0].replace(/<script>|<\/script>/g, ''));
if (typeof trackLocationClick !== 'function') { console.error('FAIL: not a function'); process.exit(1); }
console.log('PARSE OK');
"
```
Expected output: `PARSE OK`

- [ ] **Step 3: Commit**

```bash
git add docs/index.html
git commit -m "Add trackLocationClick GA4 helper for location card actions"
```

---

### Task 3: Replace the Locations section markup with the card grid

**Files:**
- Modify: `docs/index.html` — locate and replace the entire
  `<section class="locations">` ... `</section>` block by content (its
  exact line numbers have shifted due to Tasks 1 and 2's edits — do not
  rely on line numbers from before those tasks).

**Interfaces:**
- Consumes: CSS classes from Task 1 (`.loc-grid`, `.loc-card`, etc.) and
  `trackLocationClick(city, linkType, url)` from Task 2.
- Produces: none (this is the leaf UI — nothing later depends on its
  internal structure).

Exact data per card (from
`docs/superpowers/specs/2026-08-31-locations-redesign-design.md`):

| City | Address | Primary phone | Secondary phone | Blurb | More Info URL |
|---|---|---|---|---|---|
| El Segundo, CA | 11976 Aviation Blvd., El Segundo, CA 90304 | 310-341-4788 | 310-643-6221 | General & family dentistry, oral surgery | https://toothopiadental.com/contact-us/ |
| Lomita, CA | 2104 Pacific Coast Hwy., Lomita, CA 90717 | 310-878-9532 | 310-539-1111 | Gum care, veneers & full-mouth restoration | https://doctorsmileonline.com/dentist-lomita/ |
| San Pedro, CA | 1622 S Gaffey St, San Pedro, CA 90731 | 310-961-4222 | 310-548-8128 | Family care, implants & emergency dentistry | https://doctorsmileonline.com/dentist-san-pedro/ |
| Torrance, CA | 24667 Crenshaw Blvd. #D, Torrance, CA 90505 | 310-341-4783 | 310-325-8555 | Family dentistry, Invisalign & same-day care | https://doctorsmileonline.com/dentist-torrance/ |
| Corona Del Mar (Newport), CA | 2121 East Coast Hwy STE 140, Corona Del Mar, CA 92625 | (949) 640-0222 | *(none)* | Cosmetic dentistry, veneers & All-on-Four implants | https://doctorsmileonline.com/dentist-newport/ |

Shared hours line for every card: `Mon–Fri: 8AM–6PM · Sat/Sun: by appt.`

- [ ] **Step 1: Replace the section**

Replace the entire block from `<section class="locations">` (line 251)
through its matching `</section>` (line 299) with:

```html
    <section class="locations">
        <div class="container">
            <div class="row heading">
                <h2 class="black lg">Our Locations</h2>
            </div>
            <div class="loc-grid">

                <div class="loc-card">
                    <h3>El Segundo, CA</h3>
                    <p class="loc-blurb">General &amp; family dentistry, oral surgery</p>
                    <p class="loc-addr">
                        <a href="https://www.google.com/maps/search/?api=1&amp;query=11976+Aviation+Blvd%2C+El+Segundo%2C+CA+90304"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('El Segundo','directions', this.href)">
                            11976 Aviation Blvd.<br>El Segundo, CA 90304
                        </a>
                    </p>
                    <a class="loc-phone" href="tel:+1-310-341-4788"
                       onclick="trackLocationClick('El Segundo','call','tel:+1-310-341-4788')">310-341-4788</a>
                    <span class="loc-phone-secondary">Current patients: <a href="tel:+1-310-643-6221"
                       onclick="trackLocationClick('El Segundo','call','tel:+1-310-643-6221')">310-643-6221</a></span>
                    <p class="loc-hours">Mon&ndash;Fri: 8AM&ndash;6PM &middot; Sat/Sun: by appt.</p>
                    <div class="loc-actions">
                        <a class="loc-btn solid" href="tel:+1-310-341-4788"
                           onclick="trackLocationClick('El Segundo','call','tel:+1-310-341-4788')">Call</a>
                        <a class="loc-btn" href="https://www.google.com/maps/search/?api=1&amp;query=11976+Aviation+Blvd%2C+El+Segundo%2C+CA+90304"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('El Segundo','directions', this.href)">Directions</a>
                        <a class="loc-btn" href="https://toothopiadental.com/contact-us/"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('El Segundo','more_info', this.href)">More Info</a>
                    </div>
                </div>

                <div class="loc-card">
                    <h3>Lomita, CA</h3>
                    <p class="loc-blurb">Gum care, veneers &amp; full-mouth restoration</p>
                    <p class="loc-addr">
                        <a href="https://www.google.com/maps/search/?api=1&amp;query=2104+Pacific+Coast+Hwy%2C+Lomita%2C+CA+90717"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Lomita','directions', this.href)">
                            2104 Pacific Coast Hwy.<br>Lomita, CA 90717
                        </a>
                    </p>
                    <a class="loc-phone" href="tel:+1-310-878-9532"
                       onclick="trackLocationClick('Lomita','call','tel:+1-310-878-9532')">310-878-9532</a>
                    <span class="loc-phone-secondary">Current patients: <a href="tel:+1-310-539-1111"
                       onclick="trackLocationClick('Lomita','call','tel:+1-310-539-1111')">310-539-1111</a></span>
                    <p class="loc-hours">Mon&ndash;Fri: 8AM&ndash;6PM &middot; Sat/Sun: by appt.</p>
                    <div class="loc-actions">
                        <a class="loc-btn solid" href="tel:+1-310-878-9532"
                           onclick="trackLocationClick('Lomita','call','tel:+1-310-878-9532')">Call</a>
                        <a class="loc-btn" href="https://www.google.com/maps/search/?api=1&amp;query=2104+Pacific+Coast+Hwy%2C+Lomita%2C+CA+90717"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Lomita','directions', this.href)">Directions</a>
                        <a class="loc-btn" href="https://doctorsmileonline.com/dentist-lomita/"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Lomita','more_info', this.href)">More Info</a>
                    </div>
                </div>

                <div class="loc-card">
                    <h3>San Pedro, CA</h3>
                    <p class="loc-blurb">Family care, implants &amp; emergency dentistry</p>
                    <p class="loc-addr">
                        <a href="https://www.google.com/maps/search/?api=1&amp;query=1622+S+Gaffey+St%2C+San+Pedro%2C+CA+90731"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('San Pedro','directions', this.href)">
                            1622 S Gaffey St<br>San Pedro, CA 90731
                        </a>
                    </p>
                    <a class="loc-phone" href="tel:+1-310-961-4222"
                       onclick="trackLocationClick('San Pedro','call','tel:+1-310-961-4222')">310-961-4222</a>
                    <span class="loc-phone-secondary">Current patients: <a href="tel:+1-310-548-8128"
                       onclick="trackLocationClick('San Pedro','call','tel:+1-310-548-8128')">310-548-8128</a></span>
                    <p class="loc-hours">Mon&ndash;Fri: 8AM&ndash;6PM &middot; Sat/Sun: by appt.</p>
                    <div class="loc-actions">
                        <a class="loc-btn solid" href="tel:+1-310-961-4222"
                           onclick="trackLocationClick('San Pedro','call','tel:+1-310-961-4222')">Call</a>
                        <a class="loc-btn" href="https://www.google.com/maps/search/?api=1&amp;query=1622+S+Gaffey+St%2C+San+Pedro%2C+CA+90731"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('San Pedro','directions', this.href)">Directions</a>
                        <a class="loc-btn" href="https://doctorsmileonline.com/dentist-san-pedro/"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('San Pedro','more_info', this.href)">More Info</a>
                    </div>
                </div>

                <div class="loc-card">
                    <h3>Torrance, CA</h3>
                    <p class="loc-blurb">Family dentistry, Invisalign &amp; same-day care</p>
                    <p class="loc-addr">
                        <a href="https://www.google.com/maps/search/?api=1&amp;query=24667+Crenshaw+Blvd+%23D%2C+Torrance%2C+CA+90505"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Torrance','directions', this.href)">
                            24667 Crenshaw Blvd. #D<br>Torrance, CA 90505
                        </a>
                    </p>
                    <a class="loc-phone" href="tel:+1-310-341-4783"
                       onclick="trackLocationClick('Torrance','call','tel:+1-310-341-4783')">310-341-4783</a>
                    <span class="loc-phone-secondary">Current patients: <a href="tel:+1-310-325-8555"
                       onclick="trackLocationClick('Torrance','call','tel:+1-310-325-8555')">310-325-8555</a></span>
                    <p class="loc-hours">Mon&ndash;Fri: 8AM&ndash;6PM &middot; Sat/Sun: by appt.</p>
                    <div class="loc-actions">
                        <a class="loc-btn solid" href="tel:+1-310-341-4783"
                           onclick="trackLocationClick('Torrance','call','tel:+1-310-341-4783')">Call</a>
                        <a class="loc-btn" href="https://www.google.com/maps/search/?api=1&amp;query=24667+Crenshaw+Blvd+%23D%2C+Torrance%2C+CA+90505"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Torrance','directions', this.href)">Directions</a>
                        <a class="loc-btn" href="https://doctorsmileonline.com/dentist-torrance/"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Torrance','more_info', this.href)">More Info</a>
                    </div>
                </div>

                <div class="loc-card">
                    <h3>Corona Del Mar (Newport), CA</h3>
                    <p class="loc-blurb">Cosmetic dentistry, veneers &amp; All-on-Four implants</p>
                    <p class="loc-addr">
                        <a href="https://www.google.com/maps/search/?api=1&amp;query=2121+East+Coast+Hwy+STE+140%2C+Corona+Del+Mar%2C+CA+92625"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Corona Del Mar','directions', this.href)">
                            2121 East Coast Hwy STE 140<br>Corona Del Mar, CA 92625
                        </a>
                    </p>
                    <a class="loc-phone" href="tel:+1-949-640-0222"
                       onclick="trackLocationClick('Corona Del Mar','call','tel:+1-949-640-0222')">(949) 640-0222</a>
                    <p class="loc-hours">Mon&ndash;Fri: 8AM&ndash;6PM &middot; Sat/Sun: by appt.</p>
                    <div class="loc-actions">
                        <a class="loc-btn solid" href="tel:+1-949-640-0222"
                           onclick="trackLocationClick('Corona Del Mar','call','tel:+1-949-640-0222')">Call</a>
                        <a class="loc-btn" href="https://www.google.com/maps/search/?api=1&amp;query=2121+East+Coast+Hwy+STE+140%2C+Corona+Del+Mar%2C+CA+92625"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Corona Del Mar','directions', this.href)">Directions</a>
                        <a class="loc-btn" href="https://doctorsmileonline.com/dentist-newport/"
                           target="_blank" rel="noopener noreferrer"
                           onclick="trackLocationClick('Corona Del Mar','more_info', this.href)">More Info</a>
                    </div>
                </div>

            </div>
        </div>
    </section>
```

Note: the Corona Del Mar card has no `.loc-phone-secondary` line (only one
phone number exists for that office, per the spec).

- [ ] **Step 2: Verify HTML parses and no old markup remains**

Run:
```bash
python3 -c "import html.parser; html.parser.HTMLParser().feed(open('docs/index.html').read())" && echo "PARSE OK"
grep -c "loc-card" docs/index.html
grep -c "col-md-4" docs/index.html
```
Expected: `PARSE OK`, then `5` cards found (one `loc-card` open + logic —
actually grep -c counts line occurrences, so expect at least `5` matching
lines for `loc-card` opens), and `0` for `col-md-4` (old grid class fully
removed).

- [ ] **Step 3: Verify every phone/URL matches the spec table**

Run:
```bash
grep -o 'tel:+1-[0-9-]*' docs/index.html | sort -u
```
Expected output (9 unique numbers — El Segundo, Lomita, San Pedro, Torrance
each have 2, Corona Del Mar has 1):
```
tel:+1-310-325-8555
tel:+1-310-341-4783
tel:+1-310-341-4788
tel:+1-310-539-1111
tel:+1-310-548-8128
tel:+1-310-643-6221
tel:+1-310-878-9532
tel:+1-310-961-4222
tel:+1-949-640-0222
```

- [ ] **Step 4: Commit**

```bash
git add docs/index.html
git commit -m "Redesign Locations section as cards with blurbs, hours, and More Info links"
```

---

### Task 4: Visual verification at phone/tablet/desktop widths

**Files:** none modified — verification only.

**Interfaces:** none.

- [ ] **Step 1: Start a local static server**

```bash
cd docs && python3 -m http.server 8123 &
sleep 1
```

- [ ] **Step 2: Use the browse skill to check 375px (phone) width**

Load `http://localhost:8123/` in the browse tool at viewport 375x812.
Confirm:
- Location cards stack in a single column (no 2- or 3-column layout).
- No horizontal scrollbar / no content overflowing the viewport width.
- Call/Directions/More Info buttons are each at least 44px tall.
- Below ~400px width (test at 375px, which qualifies), the three buttons
  in each card's action row are stacked vertically, not squeezed
  horizontally.

- [ ] **Step 3: Use the browse skill to check 768px (tablet) width**

Load the same page at viewport 768x1024. Confirm cards render in a
2-column grid.

- [ ] **Step 4: Use the browse skill to check 1200px (desktop) width**

Load the same page at viewport 1200x800. Confirm cards render in a
3-column grid, matching the original `.col-md-4` 3-across intent.

- [ ] **Step 5: Stop the local server**

```bash
kill %1 2>/dev/null || true
```

- [ ] **Step 6: No commit for this task** (verification only, no file
  changes). If any check in Steps 2–4 fails, fix the CSS in Task 1's file
  location and re-run this task's verification before proceeding.

---

### Task 5: Sync `docs/llms.txt` with the new card content

**Files:**
- Modify: `docs/llms.txt`

**Interfaces:** none (leaf documentation file).

- [ ] **Step 1: Read the current file to confirm exact current content**

Run: `cat docs/llms.txt` and note the current `## Office locations & phones`
table and `## Content` / `## Related` sections (as of the prior session,
the table has 5 rows including El Segundo through Corona Del Mar, and no
blurb/hours/more-info columns yet).

- [ ] **Step 2: Replace the location table with an expanded version**

Replace the existing `## Office locations & phones (Southern California)`
table with:

```markdown
## Office locations & phones (Southern California)

| City | Address | New Patients | Current Patients | Services | More Info |
|---|---|---|---|---|---|
| El Segundo, CA | 11976 Aviation Blvd., 90304 | 310-341-4788 | 310-643-6221 | General & family dentistry, oral surgery | https://toothopiadental.com/contact-us/ |
| Lomita, CA | 2104 Pacific Coast Hwy., 90717 | 310-878-9532 | 310-539-1111 | Gum care, veneers & full-mouth restoration | https://doctorsmileonline.com/dentist-lomita/ |
| San Pedro, CA | 1622 S Gaffey St., 90731 | 310-961-4222 | 310-548-8128 | Family care, implants & emergency dentistry | https://doctorsmileonline.com/dentist-san-pedro/ |
| Torrance, CA | 24667 Crenshaw Blvd. #D, 90505 | 310-341-4783 | 310-325-8555 | Family dentistry, Invisalign & same-day care | https://doctorsmileonline.com/dentist-torrance/ |
| Corona Del Mar (Newport), CA | 2121 East Coast Hwy STE 140, 92625 | (949) 640-0222 | (949) 640-0222 | Cosmetic dentistry, veneers & All-on-Four implants | https://doctorsmileonline.com/dentist-newport/ |

**Hours (all locations):** Mon–Fri 8:00am–6:00pm, Sat/Sun by appointment only.
```

- [ ] **Step 3: Update the `## Content` section to describe the new card layout**

Replace:
```markdown
The page contains: practice logo, tagline, two doctor/practice chooser panels,
and an "Our Locations" section (5 offices; most list separate new/current
patient phone numbers, Corona Del Mar lists one "Call Now" number).
```

With:
```markdown
The page contains: practice logo, tagline, two doctor/practice chooser panels,
and an "Our Locations" section (5 office cards — each with a one-line service
blurb, address/directions link, phone number(s), shared hours, and a
"More Info" link to that office's dedicated page).
```

- [ ] **Step 4: Verify no stale city names remain**

Run: `grep -n "Whittier" docs/llms.txt`
Expected: no output (no matches).

- [ ] **Step 5: Commit**

```bash
git add docs/llms.txt
git commit -m "Sync llms.txt with redesigned location cards (blurbs, hours, more-info links)"
```

---

### Task 6: Sync `docs/index.md` with the new card content

**Files:**
- Modify: `docs/index.md`

**Interfaces:** none (leaf documentation file).

- [ ] **Step 1: Read the current file**

Run: `cat docs/index.md` to confirm current per-city sections (El Segundo,
Lomita, San Pedro, Torrance, Corona Del Mar (Newport)).

- [ ] **Step 2: Replace the `## Our Locations` section**

Replace the entire `## Our Locations` section (from that heading through
the end of the Corona Del Mar block) with:

```markdown
## Our Locations

**Hours (all locations):** Mon–Fri 8:00am–6:00pm, Sat/Sun by appointment only.

### El Segundo, CA
General & family dentistry, oral surgery
11976 Aviation Blvd., El Segundo, CA 90304
- New Patients: [310-341-4788](tel:+1-310-341-4788)
- Current Patients: [310-643-6221](tel:+1-310-643-6221)
- [More Info](https://toothopiadental.com/contact-us/)

### Lomita, CA
Gum care, veneers & full-mouth restoration
2104 Pacific Coast Hwy., Lomita, CA 90717
- New Patients: [310-878-9532](tel:+1-310-878-9532)
- Current Patients: [310-539-1111](tel:+1-310-539-1111)
- [More Info](https://doctorsmileonline.com/dentist-lomita/)

### San Pedro, CA
Family care, implants & emergency dentistry
1622 S Gaffey St, San Pedro, CA 90731
- New Patients: [310-961-4222](tel:+1-310-961-4222)
- Current Patients: [310-548-8128](tel:+1-310-548-8128)
- [More Info](https://doctorsmileonline.com/dentist-san-pedro/)

### Torrance, CA
Family dentistry, Invisalign & same-day care
24667 Crenshaw Blvd. #D, Torrance, CA 90505
- New Patients: [310-341-4783](tel:+1-310-341-4783)
- Current Patients: [310-325-8555](tel:+1-310-325-8555)
- [More Info](https://doctorsmileonline.com/dentist-torrance/)

### Corona Del Mar (Newport), CA
Cosmetic dentistry, veneers & All-on-Four implants
2121 East Coast Hwy STE 140, Corona Del Mar, CA 92625
- Call Now: [(949) 640-0222](tel:+1-949-640-0222)
- [More Info](https://doctorsmileonline.com/dentist-newport/)
```

- [ ] **Step 3: Verify no stale references remain**

Run: `grep -n "Whittier\|Progressive Dental" docs/index.md`
Expected: no output (no matches).

- [ ] **Step 4: Commit**

```bash
git add docs/index.md
git commit -m "Sync index.md with redesigned location cards (blurbs, hours, more-info links)"
```

---

### Task 7: Final cross-file consistency check

**Files:** none modified — verification only.

**Interfaces:** none.

- [ ] **Step 1: Confirm all 3 files list the same 5 cities in the same order**

Run:
```bash
grep -oE '(El Segundo|Lomita|San Pedro|Torrance|Corona Del Mar)' docs/index.html | uniq
grep -oE '(El Segundo|Lomita|San Pedro|Torrance|Corona Del Mar)' docs/llms.txt | uniq
grep -oE '(El Segundo|Lomita|San Pedro|Torrance|Corona Del Mar)' docs/index.md | uniq
```
Expected: each command outputs the same 5 cities in the same order:
`El Segundo`, `Lomita`, `San Pedro`, `Torrance`, `Corona Del Mar`.

- [ ] **Step 2: Confirm the ai-catalog.json still validates (untouched by this plan)**

Run:
```bash
python3 -m json.tool docs/.well-known/ai-catalog.json > /dev/null && echo "JSON OK"
```
Expected: `JSON OK`

- [ ] **Step 3: Confirm no leftover reference to the old grid classes**

Run:
```bash
grep -n "col-md-4\|row loc\b" docs/index.html
```
Expected: no output.

- [ ] **Step 4: No commit for this task** (verification only). If any
  check fails, return to the relevant task, fix, and re-run this task's
  checks before considering the plan complete.
