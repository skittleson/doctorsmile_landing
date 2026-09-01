# Local SEO Analysis — doctorsmile.com (Dr. Smile Dental Group)

Scope: `docs/index.html` — the single static chooser/landing page.
Date: 2026-08-31 · Skill: `seo-local` (v1.9.6)

---

## 1. Local SEO Score: 48/100

| Dimension | Weight | Score | Notes |
|-----------|--------|-------|-------|
| GBP Signals | 25% | 5/10 | No GBP embed, no GBP link strategy (outbound links to practice sites instead) |
| Reviews & Reputation | 20% | 1/10 | Zero review signals, no `aggregateRating`, no review widgets |
| Local On-Page SEO | 20% | 7/10 | NAP present, tel: links, hours; but single generic title/H1, no per-city targeting |
| NAP Consistency & Citations | 15% | 6/10 | Visible NAP consistent; **schema covers only 1 of 5 locations** |
| Local Schema Markup | 10% | 4/10 | Correct Dentist subtype but incomplete/misconfigured for multi-location |
| Local Link & Authority | 10% | 2/10 | No local citations/directories/authority signals detectable from page |

---

## 2. Business Type

**Brick-and-mortar** — physical addresses visible in page HTML, `tel:` links, Google Maps "Directions" links, structured `PostalAddress` in schema. Full NAP + map checks apply.

## 3. Industry Vertical Detected

**Healthcare — Dental** (Dentist). Signals: "DDS", appointments/patients language, dentistry services (oral surgery, implants, cosmetic, Invisalign, All-on-Four). Industry-specific review + schema guidance applies (see §8).

---

## 4. GBP Optimization Checklist

| Signal | Status | Recommendation |
|--------|--------|----------------|
| GBP embed / Maps iframe on page | ❌ Missing | Not required for a chooser hub, but a single consolidated `<iframe>` Google Map (lazy-loaded) of the 5 locations reinforces geographic signals |
| Primary category appropriateness | ⚠️ Inferred | `Dentist` is correct; ensure the GBP primary category for **each** office is `Dentist` (not generic), never `Dentist > General` alone |
| Secondary categories (4 recommended) | ⚠️ Unknown | Per office add: Oral Surgeon, Cosmetic Dentist, Implant Dentist where applicable |
| GBP posts / photos / Q&A | ⚠️ Off-page | Not publishable from this static page; manage in GBP dashboard. Recreate deprecated GBP Q&A as FAQ content (see risks) |
| Business hours visible | ✅ Present | Mon–Fri 8AM–6PM, Sat/Sun by appt — shared across all 5 cards |
| Click-to-call (`tel:`) | ✅ Present | Each card has new + current patient `tel:` links |
| Google Verified badge eligibility | ✅ | Multi-specialty, real addresses; claim/verify per office |

**Key GBP risk (Sterling Sky Diversity Update):** The landing page's only outbound links are to `drsmiledental.com` and `doctorsmileonline.com`. Do **not** point all 5 offices' GBP "website" fields at this chooser page — link each office's GBP to its own dedicated office page (e.g. `doctorsmileonline.com/dentist-torrance/`) to avoid suppressing per-office organic rankings.

---

## 5. Review Health Snapshot

| Signal | Status |
|--------|--------|
| Google review count visible/page schema | ❌ None |
| `aggregateRating` in schema | ❌ Absent |
| Star rating shown | ❌ None |
| Review recency signals | ❌ None |
| Third-party review presence | ❌ None on page |
| Owner response pattern | ⚠️ Off-page, unknown |

**Critical gap (20% of score = near-zero).** The 18-day rule applies: offices with no NEW reviews for ~3 weeks will trend down in the local pack for "dentist near me" queries. This page displays no review trust signals at all.

**Healthcare-specific review rule:** HIPAA prohibits confirming/denying a reviewer is a patient in responses. Any review-management guidance supplied to the practice must respect this.

**Recommended (off-page):** secure 10+ recent Google reviews per office, respond to all, and surface review content on the practice sites (`doctorsmileonline.com`), which is the page Google already trusts.

---

## 6. NAP Consistency Audit

**Visible page HTML (5 offices) — all present and internally consistent:**

| City | Address | New Patients | Current Patients |
|------|---------|--------------|------------------|
| El Segundo | 11976 Aviation Blvd., 90304 | 310-341-4788 | 310-643-6221 |
| Lomita | 2104 Pacific Coast Hwy., 90717 | 310-878-9532 | 310-539-1111 |
| San Pedro | 1622 S Gaffey St., 90731 | 310-961-4222 | 310-548-8128 |
| Torrance | 24667 Crenshaw Blvd. #D, 90505 | 310-341-4783 | 310-325-8555 |
| Corona Del Mar (Newport) | 2121 East Coast Hwy STE 140, 92625 | (949) 640-0222 | (949) 640-0222 |

**Schema vs. page comparison:**

| Source | What it contains |
|--------|------------------|
| Visible HTML | All 5 locations + 9 phone numbers + hours |
| JSON-LD `@graph` | **1** Dentist entity, El Segundo address, **ONE** telephone `+1-310-341-4788` (El Segundo new-patients) |

**Discrepancy (CRITICAL):** The structured data represents only **1 of 5** actual physical offices. The other 4 addresses and 8 phone numbers exist only in visible HTML and are missing from schema. Google's local results and AI systems reading the schema will see "Dr. Smile Dental Group" as a **single El Segundo practice**, not the 5-location group it actually is.

**Cross-source:** No GBP data is visible on-page to cross-check. Manual comparison against live GBP listings is required (not assessable from static page) — flagged in Limitations.

**Citation presence (Tier 1) — not detectable from page:** No Yelp / BBB / Facebook business-page / Apple Business Connect / Bing Places signals embedded. Recommend off-page audit: `site:yelp.com "Dr. Smile"`, claim **Apple Business Connect** (usage doubled to 27% — cheap win) and **Bing Places** (powers ChatGPT, Copilot, Alexa).

---

## 7. Local Schema Status

**Present, correct subtype, but misconfigured for multi-location.**

- Current: `"@type": ["Dentist","MedicalBusiness","LocalBusiness"]` with `@id https://www.doctorsmile.com/#practice`
- `telephone`: +1-310-341-4788 (El Segundo new-patients)
- `geo`: 33.9163, -118.3776 (El Segundo) — **only 4 decimal places** (recommend 5+)
- `address`: El Segundo PostalAddress
- `areaServed`: ["El Segundo","Lomita","San Pedro","Torrance","Newport Beach","Corona Del Mar"] — **6 cities, but page lists only 5 physical offices** (El Segundo → Newport is the same-office range, inconsistent)
- Missing: `openingHoursSpecification` (has hours on page!), `aggregateRating`, per-office entities, `branchOf` relationships

**Ready-to-use fix (recommended structure):** Model the group as one `Organization` + **5 branch `Dentist` entities**, each with its own `@id`, `address`, `geo` (5+ decimals), `telephone`, `openingHoursSpecification`, and a `branchOf` pointer back to the group's `Organization`:

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://www.doctorsmile.com/#organization",
      "name": "Dr. Smile Dental Group",
      "url": "https://www.doctorsmile.com/",
      "logo": "https://www.doctorsmile.com/img/logo.png",
      "sameAs": [
        "https://www.facebook.com/drsmiledentalgroup",
        "https://www.instagram.com/dr.smile_dental_group/"
      ]
    },
    {
      "@type": "Dentist",
      "@id": "https://www.doctorsmile.com/#location-elsegundo",
      "branchOf": { "@id": "https://www.doctorsmile.com/#organization" },
      "name": "Dr. Smile Dental Group – El Segundo",
      "url": "https://www.doctorsmile.com/",
      "telephone": "+1-310-341-4788",
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "11976 Aviation Blvd.",
        "addressLocality": "El Segundo",
        "addressRegion": "CA",
        "postalCode": "90304",
        "addressCountry": "US"
      },
      "geo": { "@type": "GeoCoordinates", "latitude": "33.9163000", "longitude": "-118.3776000" },
      "openingHoursSpecification": [
        { "@type": "OpeningHoursSpecification", "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"], "opens": "08:00", "closes": "18:00" }
      ],
      "parentOrganization": { "@id": "https://www.doctorsmile.com/#organization" }
    }
    // ... repeat branch blocks for Lomita, San Pedro, Torrance, Corona Del Mar with their own phone + geo
  ]
}
```

**Healthcare schema note:** reason and respect HIPAA. Do not add patient names or private data anywhere in schema. `sameAs` to NPI is optional and only if the practice chooses to expose it.

---

## 8. Location Page Quality (multi-location)

This is a **chooser hub**, not a set of location pages — the 5 offices are represented **inline on one page**, each linking via "More Info" to its own office page on `doctorsmileonline.com`.

- ✅ **Not a doorway pattern per se** — each card has a unique, specific blurb ("Gum care, veneers & full-mouth restoration", "Family care, implants & emergency dentistry", etc.) and distinct phone numbers. Cards are not swappable text-with-city-changed.
- ⚠️ **But the hub cannot host unique per-office content** (>60% unique requirement). The SEO weight for each office must live on the linked office pages (`doctorsmileonline.com/dentist-torrance/`, etc.), not this page.
- ⚠️ **`areaServed` mismatch** (6 cities vs 5 offices) suggests doorway-page risk if copied carelessly to practice sites. Verify each practice-site location page is **>60% unique** and passes the "swap test" — this hub is thin by design, so the practice site pages must carry the uniqueness burden.

**Action:** Ensure `doctorsmileonline.com` location pages carry real, unique, non-swappable content per office (local FAQs, local photos, area testimonials). This hub should link to them (it already does via "More Info").

---

## 9. Top 10 Prioritized Actions

**Critical**
1. **Restructure schema to 5 branch `Dentist` entities** (with `branchOf` + per-office phone/geo/hours) — the single-El-Segundo entity actively misrepresents the business.
2. **Match `areaServed` to actual offices** (5 physical locations) or remove the list; don't claim coast-to-coast coverage.
3. **Fill verification placeholder tokens** — `ADD_YOUR_BING_WEBMASTER_TOKEN`, `ADD_YOUR_YANDEX_TOKEN`, `ADD_YOUR_ALEXA_TOKEN` in the `<head>` are live placeholders that look unfinished to crawlers.

**High**
4. **Add `openingHoursSpecification`** to each office entity (hours already on the page).
5. **Add per-office `geo` with 5+ decimal precision** (currently 4 decimals, El Segundo only).
6. **Add review trust signals** — minimum `aggregateRating` on the practice site; drive 10+ recent reviews per office (18-day cadence).

**Medium**
7. **Claim/optimize Apple Business Connect** + **Bing Places** per office (both power ChatGPT/Copilot/Alexa local answers).
8. **Point each office's GBP "website" at its own office page**, not this chooser hub (Sterling Sky Diversity rule).

**Low**
9. **Add a single lazy-loaded Google Map** of the 5 office pins to reinforce geographic signals.
10. **Add city+service keywords** to title/H1 where natural (e.g. title "Dr. Smile Dental Group — Dentists in El Segundo, Lomita, San Pedro, Torrance & Newport").

---

## 10. Limitations Disclaimer

This analysis was performed on the static `index.html` only. It **could not** assess:
- Real-time local pack positions, geo-grid ranking, or GBP Insights data (off-page)
- Comprehensive backlink profile or Domain Authority
- Actual GBP listing correctness, categories, photos, or post activity (dashboard-only)
- Review velocity/response patterns (off-page)
- Domain-level citation consistency across Yelp/BBB/etc. (requires `site:` searches per directory)

Fill these gaps with: Google Business Profile dashboard per office, Google Search Console, and (optionally) DataForSEO `local_business_data` / `google_local_pack_serp` for live local-pack tracking.

---

*Generated by `seo-local` skill (AgriciDaniel v1.9.6) applied to /home/spencerkittleson/repos/doctorsmile_com_landing/docs/index.html*
