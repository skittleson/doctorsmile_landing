# Local SEO Analysis — doctorsmile.com (Dr. Smile Dental Group)

Scope: `docs/index.html` + `docs/robots.txt` + `docs/sitemap.xml` — single static chooser/landing page.
Date: 2026-11-23 · Skill: `seo-local` (v1.9.6) · Supersedes 2026-08-31 report.
Live citation evidence gathered 2026-11-23 (GBP/Yelp/Unilocal/Doctor.com) incorporated.

---

## 1. Local SEO Score: 61/100 (was 48)

| Dimension | Weight | Score | Notes |
|-----------|--------|-------|-------|
| GBP Signals | 25% | 7/10 | Torrance GBP claimed, correct categories, links to per-office page (good). **Hours conflict page-vs-GBP (Critical).** No map embed; other 4 offices' GBP unverified |
| Reviews & Reputation | 20% | 4/10 | Reviews EXIST off-page (202 @ 4.8 Torrance GBP, 107 @ 4.5 Yelp) — but page displays zero, no `aggregateRating` |
| Local On-Page SEO | 20% | 8/10 | Title + H1 now name all 5 cities; NAP, tel:, Directions links. Hours claim wrong vs GBP |
| NAP & Citations | 15% | 5/10 | Page internally consistent; **page-vs-GBP hours mismatch**, Lomita citation phone/unit drift, thin Tier-1 coverage |
| Local Schema Markup | 10% | 8/10 | **Fixed:** Organization + 5 branch Dentist entities, per-office geo (5 decimals), hours, phones. Missing `aggregateRating`, per-branch `image` |
| Local Link & Authority | 10% | 4/10 | Torrance claimed on Google+Yelp; Lomita on Unilocal/Doctor.com. No BBB, no listings for 3 offices, no authority footprint |

Weighted: 1.75 + 0.80 + 1.60 + 0.75 + 0.80 + 0.40 = **6.1 → 61/100**.

---

## 2. Business Type

**Brick-and-mortar** — 5 physical addresses in HTML + schema, `tel:` links, Google Maps Directions links, `PostalAddress` per branch. Full NAP + map checks apply.

## 3. Industry Vertical Detected

**Healthcare — Dental** (Dentist subtype). Signals: "Dentist" schema type, DDS/dentist language, oral surgery/implants/cosmetic services. HIPAA review-response rule applies.

---

## 4. GBP Optimization Checklist

| Signal | Status | Recommendation |
|--------|--------|----------------|
| GBP claimed | ✅ Torrance confirmed claimed | Verify/claim GBP for El Segundo, Lomita, San Pedro, Corona Del Mar (not found in evidence scan) |
| Primary category | ✅ Torrance: Dentist + Oral Surgeon | Confirm same per office |
| GBP website → per-office page | ✅ Torrance links `doctorsmileonline.com/dentist-torrance` | Sterling Sky Diversity practice confirmed — replicate for other 4 |
| **Hours page-vs-GBP** | ❌ **Mismatch** | GBP Torrance: Mon–Wed 8–6, Thu 9–6, Fri 8:30–5, Sat/Sun closed. Page claims Mon–Fri 8–6 + weekend appts for ALL offices. Fix page/schema to actual per-office hours |
| Maps embed on page | ❌ Missing | Optional lazy-loaded map of 5 pins |
| Click-to-call (`tel:`) | ✅ Present | Per-card new + current patient lines |
| GBP posts/photos/Q&A | ⚠️ Off-page, unknown | Dashboard-only |

---

## 5. Review Health Snapshot

| Signal | Status |
|--------|--------|
| Google reviews | ✅ Torrance: 4.8★ / 202 ratings (live-verified 2026-11-23) |
| Yelp | ✅ Torrance: 4.5★ / 107, claimed, owner Dr. Kayvon J. |
| Unilocal / Doctor.com | ✅ Lomita: 4.1 (29) / 5.0 (43) |
| Star rating shown on page | ❌ None |
| `aggregateRating` in schema | ❌ Absent |
| Review recency / owner responses | ⚠️ Off-page, unknown |

August's "zero review signals" was too harsh — **reviews exist off-page but have zero on-page surfacing.** The 18-day cadence rule still applies per office; other 4 offices show no review presence in the evidence scan. HIPAA: never confirm/deny patient status in responses.

---

## 6. NAP Consistency Audit

**Page HTML (unchanged since August, internally consistent):**

| City | Address | New | Current |
|------|---------|-----|---------|
| El Segundo | 11976 Aviation Blvd., 90304 | 310-341-4788 | 310-643-6221 |
| Lomita | 2104 Pacific Coast Hwy., 90717 | 310-878-9532 | 310-539-1111 |
| San Pedro | 1622 S Gaffey St., 90731 | 310-961-4222 | 310-548-8128 |
| Torrance | 24667 Crenshaw Blvd. #D, 90505 | 310-341-4783 | 310-325-8555 |
| Corona Del Mar | 2121 East Coast Hwy STE 140, 92625 | (949) 640-0222 | (949) 640-0222 |

**Cross-source discrepancies (live evidence 2026-11-23):**

| # | Source | Discrepancy | Severity |
|---|--------|-------------|----------|
| 1 | Torrance GBP vs page + schema | GBP hours Mon–Wed 8–6 / Thu 9–6 / Fri 8:30–5 / closed weekends vs page "Mon–Fri 8AM–6PM · Sat/Sun by appt". Yelp matches GBP, not page | **Critical** |
| 2 | Lomita citation (Unilocal/Doctor.com) | Uses secondary phone 310-539-1111 ("current patients") and "Unit 5" suffix; page/schema use 310-878-9532, no unit | High |
| 3 | Torrance GBP phone | GBP shows 310-325-8555 (current-patients line); page primary/schema is 310-341-4783 | Medium — pick one primary number per office |

Schema now mirrors page (5 branches) — but that means the **wrong hours are now in structured data too** (all 5 branches carry identical Mon–Fri 8–6 spec).

---

## 7. Citation Presence (live scan 2026-11-23)

**Tier 1:**

| Office | Google | Yelp | BBB | Facebook | Apple Biz Connect | Bing Places |
|--------|--------|------|-----|----------|-------------------|-------------|
| Torrance | ✅ Claimed 4.8/202 | ✅ Claimed 4.5/107 | ❌ | ❌ | ❓ | ❓ |
| Lomita | ❓ | ❌ | ❌ | ❓ | ❓ | ❓ |
| El Segundo | ❓ | ❌ | ❌ | ❓ | ❓ | ❓ |
| San Pedro | ❓ | ❌ | ❌ | ❓ | ❓ | ❓ |
| Corona Del Mar | ❓ | ❌ | ❌ | ❓ | ❓ | ❓ |

**Other:** Lomita on Unilocal (4.1/29) + Doctor.com (5.0/43). No BBB profile for the group. No Wikipedia/Wikidata/Reddit/YouTube footprint. Facebook + Instagram linked in `sameAs` (ownership unverified).

---

## 8. Local Schema Status

**Mostly fixed since August** (`@graph` in `<head>`):

- ✅ `Organization` + 5 branch `Dentist` entities with `branchOf`/`parentOrganization`
- ✅ Per-office `telephone`, `PostalAddress`, `geo` (5 decimals), `openingHoursSpecification`
- ✅ Per-branch `url` points at `doctorsmileonline.com/dentist-*` office pages (except El Segundo → home)
- ✅ `priceRange: "$$"` (<100 chars OK), `areaServed` removed, WebSite + BreadcrumbList present
- ✅ Placeholder verification tokens removed from `<head>` (only real Google token ships)
- ❌ Remaining gaps: no `aggregateRating`, no per-branch `image`, no `sameAs` per branch (GBP/Yelp URLs), El Segundo branch `url` still the chooser home

Hours in schema must be corrected to match per-office GBP (see §6.1).

---

## 9. Location Page Quality

Unchanged: **chooser hub**, not location pages. Cards have unique blurbs + distinct phones (passes swap test). SEO weight lives on `doctorsmileonline.com/dentist-*` pages — hub links to them via "More Info" and now schema `url`. Verify those pages are >60% unique per office. `areaServed` mismatch (August) resolved by removal.

---

## 10. Top 10 Prioritized Actions

**Critical**
1. **Fix hours to match real per-office GBP** (page text + all 5 `openingHoursSpecification` blocks). Torrance GBP ≠ page; verify actual hours for the other 4 offices and differentiate.
2. **Align Lomita citation**: pick one primary phone; correct Unilocal/Doctor.com to page phone or page to citation phone; settle "Unit 5" suffix everywhere.
3. **Surface reviews on the practice site** + add `aggregateRating` (per branch) — 202+107+43+29 reviews exist invisibly today.
4. **Claim/create missing office listings**: GBP for El Segundo, Lomita, San Pedro, Corona Del Mar; Yelp for the 4 unlisted offices.

**High**
5. Pick one canonical phone per office (GBP currently uses current-patients line at Torrance; schema uses new-patients line).
6. Add per-branch `image` + branch-level `sameAs` (GBP/Yelp URLs) to schema; point El Segundo branch `url` at its office page.

**Medium**
7. Claim Apple Business Connect + Bing Places for all 5 offices (powers ChatGPT/Copilot/Alexa).
8. Open a BBB profile for the group.
9. Lazy-loaded Google Map with 5 pins on the hub.
10. Maintain 18-day review cadence per office; HIPAA-safe responses.

**August carryover status:** #1 schema restructure ✅ DONE · #2 areaServed ✅ DONE · #3 placeholder tokens ✅ DONE · #4 openingHours ✅ DONE (but wrong values) · #5 geo precision ✅ DONE · #6 reviews ❌ OPEN · #7 Apple/Bing ❌ OPEN · #8 GBP→office-page ✅ DONE (Torrance verified) · #9 map ❌ OPEN · #10 city keywords in title/H1 ✅ DONE.

---

## 11. Limitations

Static page + live citation spot-check only. Not assessed: local pack/geo-grid ranks, GBP Insights, backlink profile/DA, GBP categories/photos/posts for the 4 unverified offices, review velocity/response patterns, full directory sweep (only Google/Yelp/BBB/Unilocal/Doctor.com checked). Fill gaps with GBP dashboard per office, GSC, and DataForSEO `local_business_data` / `google_local_pack_serp`.

---

*Generated by `seo-local` skill (AgriciDaniel v1.9.6) applied to docs/index.html; live citation evidence supplied 2026-11-23.*
