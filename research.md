# Research: doctorsmile.com & doctorsmileonline.com

Prepared: 2026-08-30 · Source: direct site crawl + DuckDuckGo web search

---

## 1. Site inventory & relationship

| Property | doctorsmile.com | doctorsmileonline.com |
|---|---|---|
| Type | Static landing / chooser page | WordPress 7.1 site (custom theme `dr-smile-new`) |
| Purpose | Landing hub that routes visitors to the two practice sites | Main practice website ("Dr. Smile: Expert for Oral Surgery, Implants & More") |
| Simple? | Yes — single page | Multi-page (~25 URLs), blogs, guides, forms |
| Primary phone | None on page | **(310) 388-3669** "CALL NOW" |
| Doctors | Hossein Javid, DDS → drsmiledental.com<br>Mariam Nadi, DDS & Kayvon Javid, DDS → doctorsmileonline.com | Dr. Mariam Nadi (DDS), Dr. Kayvon Javid (PhD, DDS, DICOI, FCII, AFWCLI, CPT) |

**Relationship:** `doctorsmile.com` is the umbrella landing page with two "choose your practice" photo panels. The **left** panel (Hossein Javid, DDS) links to `drsmiledental.com`; the **right** panel (Mariam Nadi + Kayvon Javid) links to `doctorsmileonline.com`. `doctorsmileonline.com` is the larger, WordPress-based practice site for the Nadi/Javid team.

Other related sibling sites discovered (same "Dr. Smile" brand/network):
- `drsmiledental.com` (left panel — Hossein Javid's general dentistry)
- `drsmiledentistry.com`, `drsmileimplants.com`, `drsmilelomita.com`, `drsmiletorrance.com`, `drsmilenewport.com` (network/outpost sites)

---

## 2. doctorsmile.com (landing page)

**Tagline:** "A Smile is Happiness You'll Find Right Under Your Nose"

**Two practice chooser panels:**
1. **Hossein Javid, DDS** → links to `http://www.drsmiledental.com/`
2. **Mariam Nadi, DDS & Kayvon Javid, DDS** → links to `http://www.doctorsmileonline.com/`

**Our Locations (5 offices) — phones:**

| City | Address | New Patients | Current Patients |
|---|---|---|---|
| El Segundo, CA | 11976 Aviation Blvd., El Segundo, CA 90304 | 310-341-4788 | 310-643-6221 |
| Lomita, CA | 2104 Pacific Coast Hwy., Lomita, CA 90717 | 310-878-9532 | 310-539-1111 |
| San Pedro, CA | 1622 S Gaffey St., San Pedro, CA 90731 | 310-961-4222 | 310-548-8128 |
| Torrance, CA | 24667 Crenshaw Blvd. #D, Torrance, CA 90505 | 310-341-4783 | 310-325-8555 |
| Whittier, CA | 16135 Whittier Blvd. #105, Whittier, CA 90603 | 424-286-2947 | 562-943-1098 |

**Footer:** "Dental Consulting By Progressive Dental" → links to `progressivedentalmarketing.com/consulting/` (site marketing/SEO is done by Progressive Dental Marketing).

**Tech:** Bootstrap 4.0.0-alpha.6 + custom `javidLand.css`, Gotham webfonts. Static, minimal JS.

**Notable:** doctorsmile.com's location list includes **El Segundo** which is absent from doctorsmileonline.com's own location list (see below) — the two sites list somewhat different office sets. Phone inconsistencies exist even on this page (e.g., San Pedro "New" shows `tel:+1-961-4222` = 310-961-4222).

---

## 3. doctorsmileonline.com (WordPress practice site)

### 3.1 Structure
Navigation: Home · About · FAQs · Dental Guide (Dental Implant Guide / Dental Veneers Guide / Dental Invisalign Treatment) · Financing · Blog · Important Announcements · Location · Services · Contact.
Also: Testimonials, CTA form, Privacy Policy, Terms and Conditions.

### 3.2 Doctors (About page)
- **Dr. Mariam Nadi, DDS** — practiced in Southern California ~16 years; co-founded/co-built the patient-centered "Dr. Smile" brand with her husband Dr. Kayvon Javid.
- **Dr. Kayvon Javid "Dr. K", PhD, DDS, DICOI, FCII, AFWCLI, CPT (ACA)** — 25+ years advanced experience in patient care, oral surgery, periodontics, dental education; specializes in complex cases & implant dentistry. Credentials per site:
  - PhD in Oral & Maxillofacial Surgery / Periodontics
  - DDS with Honors from USC
  - Former faculty, USC Advanced Education in Dentistry program
  - Board-certified Implantologist; Diplomat of the International Congress of Oral Implantology (ICOI)
  - Board member of Biolase
  - Founder, Academy of Oral Surgery & South Bay Implant Institute
  - CEO, Global Implantology Institute
  - Editor/board member, International Journal of Growth Factors and Stem Cells in Dentistry
  - Certified Phlebotomy Instructor

### 3.3 Services (Services page + specialty pages)
Four specialty pillars:
1. **Oral Surgery, TMJ & Implants** (`/oral-surgery/`) — surgical needs, dental implants ("gold standard" over 30 yrs), **All-on-Four** (teeth-in-a-day), sedation dentistry.
2. **Cosmetics, Veneers & Whitening** (`/cosmetic-care/`) — Invisalign, Boost/Kor in-office whitening, at-home kits, 2mm porcelain veneers.
3. **Invisalign & Orthodontcs** (`/invisalign-orthodontcs/` — note typo in URL) — "Invisalign in Torrance" SEO-targeted page.
4. **All-on-Four & Prosthetics** (`/all-on-four-prosthetics/`) — "All on 4 Implants in Newport Beach" SEO-targeted page.

Other service categories on Services page: **Prevention, Cosmetic Care, Restorative Care, Oral Surgery & Dental Implants**, plus **Veneers, Bonding, Orthodontics**.

### 3.4 Location / contact
- Form "Preferred Location" options: **San Pedro, Torrance, Newport Beach, Lomita**.
- Hours: Mon–Fri 8:00am–6:00pm; Sat/Sun by appointment only.
- Schema.org structured data references: **2121 East Coast Hwy Ste 140, Corona Del Mar** and phone **949-640-0222** (Newport/Orange County outpost) — an inconsistency vs. the "South Bay/LA" offices and vs. the five locations on doctorsmile.com.
- Social: facebook.com/drsmiledentalgroup, instagram.com/dr.smile_dental_group. WhatsApp link uses placeholder number `1234567890`.
- Main CTA phone: **(310) 388-3669**.

### 3.5 Financing (`/financing/`)
Accepts most insurance; for uninsured/over-max patients offers cash, credit cards, and **no-interest financing**; dedicated team will research a patient's insurance benefits.

### 3.6 FAQs (`/faqs/`)
20 FAQs localized by city (San Pedro, Newport Beach, Torrance, Lomita): benefits, emergency care, cleaning frequency, implant surgery/recovery, cosmetic safety/affordability, financing, payment plans, visiting hours.

### 3.7 Blog
City-SEO-location blog (Newport Beach, San Pedro, Lomita, Torrance / Emergency & Same-Day Dentist). One placeholder post title "Title Will Display Here" present.

### 3.8 Guides
- Dental Implant Guide
- Dental Veneers Guide
- Dental Invisalign Treatment

### 3.9 ⚠️ Notable finding — `/pain-tramadol/` page
A page titled **"Buy Tramadol Online – Fast & Secure Pain Management Solutions"** exists on this legitimate dental site. It hosts pharmacology-heavy Q&A content about tramadol (opioid) as a dental anesthetic — with repeated phrasings like **"where can patients safely buy tramadol online"** / **"buying tramadol"**. This looks like **pharmaceutical / SEO-spam content** (selling/ads for tramadol online) on a dental practice domain — a brand/reputation and compliance risk. It is not a legitimate patient resource and should be flagged to the site owner for removal (it could also indicate a compromised or loosely-moderated WordPress install). The dedicated DDG search for "doctorsmileonline buy tramadol" returned none of the actual page in organic results (not indexed for those terms).

---

## 4. Web-search context

- **Dr. Smile Dental Group** = Southern California multi-specialty dental brand (oral surgery, implants, sedation, general & cosmetic). Multiple city sites exist (Lomita, Torrance, Newport) — consistent with a localized SEO strategy.
- Founder/lead is **Dr. Kayvon Javid** (PhD/DDS, USC, oral & maxillofacial surgery background) alongside **Dr. Mariam Nadi**; the umbrella landing page separately lists **Hossein Javid, DDS** (drsmiledental.com).
- Marketing/SEO handled by **Progressive Dental Marketing** (credited on doctorsmile.com).
- Third-party listings (MapQuest, Comercii, Reputable Businesses, Facebook) mirror the doctor/location/phone data above.

---

## 5. Medical practice locations (consolidated)

**South Bay / LA-area offices (from doctorsmile.com):**
- El Segundo (11976 Aviation Blvd., 90304)
- Lomita (2104 Pacific Coast Hwy., 90717)
- San Pedro (1622 S Gaffey St., 90731)
- Torrance (24667 Crenshaw Blvd. #D, 90505)
- Whittier (16135 Whittier Blvd. #105, 90603)

**Newport/Orange County outpost (from doctorsmileonline.com schema):**
- "Corona Del Mar" — 2121 East Coast Hwy Ste 140
- Phone 949-640-0222

---

## 6. Quick reference — key external links
- Left panel: http://www.drsmiledental.com/
- Right panel / main site: https://doctorsmileonline.com/
- Dental consulting credit: https://www.progressivedentalmarketing.com/consulting/
- Social: facebook.com/drsmiledentalgroup · instagram.com/dr.smile_dental_group

---

## 8. Agent-readiness (isitagentready.com) — work done

Per https://isitagentready.com/ advice. Note: the scanner returns HTTP **526**
(Cloudflare SSL / invalid-cert) against the live `www.doctorsmile.com`, so it
cannot be scanned directly — that 526 is itself a production finding to fix.
Checklist and guidance were extracted from the scanner and applied.

### Implemented (foundational, static-friendly)
| Standard | File | Notes |
|---|---|---|
| robots.txt (rfc 9309) | `robots.txt` | clear crawl rules + sitemap ref |
| AI bot rules | `robots.txt` | GPTBot, OAI-SearchBot, Claude-Web/ClaudeBot, anthropic-ai, Google-Extended, PerplexityBot, Bingbot, Applebot-Extended, FacebookBot |
| Content Signals | `robots.txt` | `Content-Signal: ai-train=no, search=yes, ai-input=no` (adjustable) |
| Sitemap | `sitemap.xml` | single canonical URL |
| llms.txt | `llms.txt` | plain-text site summary for LLMs/agents |
| humans.txt | `humans.txt` | team/tech attribution |
| ARD / AI catalog | `.well-known/ai-catalog.json` | agentic resource catalog (spec 1.0) |
| security.txt (RFC 9116) | `.well-known/security.txt` | security contact |
| Markdown negotiation | `index.md` | LLM-readable markdown copy of the page |
| Discoverability links | `index.html` head | `<link rel="llms">`, `rel="alternate" text/markdown`, `rel="ai-catalog"` |

### Documented as N/A (need a backend/API/payments the static page lacks)
MCP Server Card, A2A Agent Card, WebMCP, x402, MPP, ACP, UCP, OAuth/OIDC
discovery, OAuth Protected Resource, Web Bot Auth request-signing directory,
API catalog (RFC 9727) — none apply without a server API/agent.
Also noted (server/DNS config, not files): HTTP `Link` headers, DNS-AID, and
serving `/.well-known/*` with correct content types / CORS.
SEO meta (Open Graph, Twitter, geo, JSON-LD Dentist schema, Google/Bing/etc.
verification) were added in the head of `index.html`.
