# Marketing Recommendations — doctorsmile.com (Dr. Smile Dental Group)

Scope: `docs/index.html` (chooser hub) informed by this repo's `LOCAL-SEO-ANALYSIS` (61/100) and `GEO-ANALYSIS` (66/100), both dated 2026-11-23, plus 2026 dental-marketing research.
Date: 2026-11-23. Companion sections drafted with two helper models; toothopia link intent verified via web search.

**Research anchors used:** GBP signals ≈32% of local-pack weight, reviews ≈24% (Whitespark 2026; March 2026 update weights reviews <30 days old ≈2.3x). Complete GBP profiles ≈70% more likely to earn visits; direction requests convert ≈76% within 24h. ≈60–70% of dental site traffic converts by phone; only ≈47% of dentist sites offer online booking (522-site study, Sep 2026). Perplexity names a business in ≈40% of local answers (Chat Radar, Oct 2026); AI engines ground local answers in GBP/Bing/Apple listings + consistent NAP.

---

## Executive summary

The hub page is technically in good shape (schema, GEO files, routing). The marketing gap is **trust display + reputation footprint**, not the page itself:

1. **381 real reviews (Torrance 4.8/202 Google, 4.5/107 Yelp, Lomita 43+29) are invisible** on the page and schema.
2. **4 of 5 offices have no detectable GBP/Yelp footprint** — the single largest untapped lever (GBP + reviews ≈56% of local-pack weight).
3. **Zero attribution layer**: outbound links carry no UTM, so ad/spend decisions on this hub fly blind.
4. The El Segundo card links to **toothopiadental.com** — a sister practice the owners also hold a stake in (Toothopia Dental is the rebranded former "Dr. Smile" El Segundo office, founded by Dr. Hossein Javid). The routing is intentional; the link is just **unlabeled**, so visitors can't tell it's still the same group.
5. **Search Console data (Sections D–E, pulled 2026-11-23):** non-brand organic traffic has been flat for 13 weeks (4–9 clicks/week); the index is polluted with `?utm_source=google_business_profile` duplicates and cannibalizing "best-*" pages; one money query even ranks `/contact?rwg_token=…` URLs at positions 1–2 with zero clicks. Fixing canonicalization and titles is free clicks.

---

## Section A — On-Page Conversion

1. **Sticky mobile call bar.** Fixed bottom bar <768px with one "Call now" CTA (per-card numbers vanish once scrolled). Why: 60–70% of dental traffic converts by phone; mobile-dominant audience. Effort S · Impact **High**.
2. **Surface review stars on office cards** ("★ 4.8 · 202 Google reviews" on Torrance now; others as claimed) + per-branch `aggregateRating` once ratings exist per office (sequenced with B-8). Why: stars on-page drive trust and call/directions conversion; today 381 reviews display nowhere. Effort S · Impact **High**.
3. **Label the El Segundo "Info" link.** The link to `toothopiadental.com/contact-us/` is correct group routing — Toothopia is the rebranded former Dr. Smile El Segundo office, in which the owners also hold a stake — but visitors can't tell. Rename the button "Toothopia — El Segundo Info" (or add "Formerly Dr. Smile"), add `toothopiadental.com` to schema `sameAs`, and point the El Segundo branch `url` at Toothopia's El Segundo page instead of the chooser home. Why: an unlabeled sister-brand domain on the group hub reads as a broken link and wastes a cross-brand trust signal. Effort S · Impact Med–High.
4. **UTM-tag every outbound link.** The 2 "Visit Website" chooser links and 5 "Info" buttons carry no `utm_source/utm_medium/campaign`; `trackLocationClick` records the click but the destination can't attribute it. Why: no attribution layer = no ROI read on this hub or any paid traffic pointed at it. Effort S · Impact **High**.
5. **Repeat one CTA after each major section** ("Call your nearest office" above the location grid and after it). Why: a repeated clear CTA is a top landing-page conversion predictor; the page currently relies on in-card numbers only. Effort S · Impact Med.
6. **Tighten above-the-fold on mobile.** H1 + tagline consume the first screen before the chooser panels; ensure one chooser panel starts at/near the fold, keep slogan as sub-line. Why: message-match in the first seconds predicts bounce. Effort S · Impact Med.
7. **Proper OG image (1200×630).** Current `og:image` is `img/hJavid.jpg` (730×640) — wrong ratio for `summary_large_image`, so shares/citations crop badly. Why: shared and AI-surfaced cards are a brand-mention channel. Effort S · Impact Med.
8. **Analytics hygiene.** GA4 fires without a consent notice; confirm the practice's compliance posture (and add `G-` linked ads conversion import before any paid campaigns). Effort S · Impact Med.
9. **Real photos where panels allow.** Interior/exterior/team photos outperform posed portraits on trust; keep pricing/insurance signals only if verifiable (YMYL discipline). Effort M · Impact Med.
10. **Do NOT add** long service prose, an FAQ section, or a booking widget here — hub/chooser role, content belongs on `doctorsmileonline.com` (content brief's Website Relevance rule). Online booking is a real 2026 conversion lever (≈53% of dentist sites lack it) but it belongs on the practice sites, not this hub.

## Section B — Off-Page Reputation & Local Presence

Sequence: B-7 first (1 week) → B-1 claims → B-2/B-3 per claim → B-4/5/6 in parallel → B-8 once ratings exist per office.

1. **Claim/verify GBP for El Segundo, Lomita, San Pedro, Corona Del Mar** — Dentist category, canonical new-patient phone, real hours, link to each `doctorsmileonline.com/dentist-*` page. Why: GBP ≈32% of pack weight; only ~35% of SMBs claim at all; Torrance proves the pattern. Effort M · Impact **High**.
2. **Per-office review generation** — front-desk QR card to that office's GBP review URL; SMS follow-up day 1 + day 3; target ≥3/office/month; any review older than 18 days triggers a push (keeps a review inside the 2.3x/30-day window). Why: reviews ≈24% of pack weight; recency is the cheapest rank lever after claiming. Effort M · Impact **High**.
3. **HIPAA-safe response SOP** — 100% of new reviews answered <48h, first name only, never confirm/deny patient status; negatives move offline ("call the office manager"). One owner per office, monthly audit. Effort S · Impact Med.
4. **Yelp for the 4 unlisted offices** — NAP copied exactly from GBP; Torrance (4.5/107) proves the channel. Tier-1 citation for both pack and AI grounding. Effort S · Impact Med–High.
5. **Apple Business Connect + Bing Places, all 5 offices** — sync from GBP. These feed Siri/Copilot/ChatGPT local answers. Effort S · Impact Med.
6. **BBB profile for the group** — one profile, all 5 addresses; high-authority healthcare trust citation. Effort S · Impact Low–Med.
7. **Fix NAP drift before expanding listings** — one canonical phone per office (new-patient line), settle Lomita's "Unit 5" suffix, correct Unilocal/Doctor.com, then propagate the identical string to every new listing. Every new listing built on drifted NAP amplifies the error. Effort S · Impact Med (prerequisite).
8. **`aggregateRating` + on-page stars per branch — only after real per-office ratings exist** — never surface Torrance-only numbers as group-wide. Effort S · Impact Med–High (after #1).
9. **GBP photo/post cadence** — ≥10 seed photos at claim, then 2–3 photos + 1 post per office monthly. Effort M ongoing · Impact Med.
10. **Every listing → its per-office page** — replicate Torrance's verified GBP→`dentist-torrance` pattern; fix El Segundo schema `url` (still chooser home). Effort S · Impact Med.

## Section C — AI-Search Visibility (GEO)

1. **Directory coverage is the AI lever, not just Google's.** ChatGPT/Perplexity/Copilot ground local dental answers in GBP + Bing Places + Apple Business Connect + consistent NAP; Perplexity names a listed business in ≈40% of local answers. Section B items 1/4/5 double as the AI-visibility fix — no separate on-page work needed here. Effort: folded into B · Impact **High**.
2. **Zero third-party entity footprint** (no Wikidata, press, Reddit, YouTube). Brand mentions correlate ≈3x more with AI visibility than backlinks. Create a Wikidata item for Dr. Smile Dental Group (5 offices, founded, principals) and pitch 1–2 South Bay local-press items (Toothopia rebrand story is a ready angle). Effort S–M · Impact Med.
3. **Merge hero intro + booking block into one ~140-word self-contained passage** ("what/where/how to book", answer in first 40 words) to hit the optimal citability band without new sections. Effort S · Impact Med.
4. **Question-H2 FAQ content belongs on `doctorsmileonline.com`**, not here (duplication risk stands). This hub's citable artifacts (llms.txt table, definitional intro) are already its best exports. Effort: off-hub · Impact High (for the practice site).
5. **Keep llms.txt / index.md / schema in sync manually** — no automated check exists; a stale office row is a citable misinformation source. Re-verify after the hours fixes land. Effort S · Impact Med.
6. **Test actual prompts** ("dentist in Lomita CA that takes new patients", "emergency dentist Torrance weekend") across ChatGPT/Perplexity/AI Overviews quarterly; record whether the practice is named. This repo's reports are file-based and can't see retrieval. Effort S · Impact Med.

## Section D — Data-Backed Findings (Search Console): Technical & Indexing

Pulled 2026-11-23 via GSC API (28 days, `doctorsmileonline.com`; raw data in `gsc-raw-doctorsmileonline.txt`). 132 clicks / 5,942 impressions ≈ 2.2% CTR. **Note: `doctorsmile.com` (this hub) is NOT a verified GSC property — add it (verification token already in the page).**

1. **UTM-in-URL duplication.** All four office pages are indexed WITH `?utm_source=google_business_profile` appended (`/dentist-san-pedro?utm_…` 38c/1786i; Lomita 20c/1080i; Torrance 15c/903i; Newport 13c/453i) while clean versions rank separately (Lomita clean: 2c/500i; `/contact` 3c/331i vs `/contact/` 1c/736i — trailing-slash duplication too). Why: splits ranking signals across duplicate URLs and distorts reporting. Fix: GBP website links → clean URLs; canonical tags on all pages; 301 or noindex the utm variants. Effort M · Impact **High**.
2. **Keyword cannibalization.** "best dentist san pedro ca" spreads across 6+ URLs, all 0 clicks: home p68–78, `/best-affordable-dentist-in-san-pedro/` p26–58, `/best-dental-clinic-in-san-pedro-oral-health/` p13–45, `/dentist-san-pedro/` p21. Google rotates URLs instead of consolidating one. Fix: pick one canonical San Pedro target, merge/redirect the thin "best-*" variants, internal-link to the winner. Effort M · Impact **High**.
3. **Review-widget parameter URLs indexed at money-query positions.** `/contact?rwg_token=…&source=cat` appears at positions 1–2 for "best dentist in san pedro ca" with 0 clicks. Fix: `noindex` parameterized contact URLs; block `rwg_token` in robots or strip the param at the edge. Effort S · Impact Med–High.
4. **Brand-dominated, flat traffic.** "dr smile*" variants hold most clicks; non-brand trend (query ∌ "smile") flat for 13 weeks at 4–9 clicks/week on 1,550–3,320 weekly impressions — wide-but-shallow visibility with zero growth. Effort M (Sections E + B together) · Impact **High**.
5. **Zero-click long-tail thin pages.** 0c/60+i each: `/best-walk-in-dentist-in-torrance/` 558i, `/best-dental-clinic-in-newport-beach/` 319i, `/best-deep-cleaning-dentist-in-newport-beach/` 158i, `/all-on-4-dental-implants-newport-beach/` 60i — consolidate into office/service pages. Effort S–M · Impact Med.
6. **Mobile beats desktop 2.7x on CTR** (1.6% vs 0.6%; 5,131i vs 7,927i). Desktop sees the site on wide local-modifier queries and doesn't click — same title/snippet problem as E-3. Effort S · Impact Med.

## Section E — Data-Backed Findings (Search Console): Content Opportunities

1. **Push position 4–15 queries to top-3.** "dentist near me" 109i at p4.5 (1.8% CTR), "dr smile lomita" 141i p9.8, "dentist san pedro" 151i p19.4, "lomita dentist" 12i p10.9, "san pedro dental clinic" 17i p9.7. Expected CTR at p1 ≈ 27% vs ≈6% at p5 — "dentist near me" alone roughly triples clicks at parity. Effort M · Impact **High**.
2. **Newport Beach near-zero organic presence.** "dentist in newport beach" 44i p47.6; Corona Del Mar pages all 0 clicks (`/best-dental-clinic-in-newport-beach/` 319i p35). Confirms B-1: no claimed GBP = no local pack = page 5. Claim the GBP before any Newport content work. Effort M · Impact **High**.
3. **Zero-click impression sinks → title/meta rewrites.** `/best-affordable-dentist-in-san-pedro/` 836i/0c; `/best-walk-in-dentist-in-torrance/` 558i/0c; home 1876i at 0.6%. Lead titles with location + service + differentiator (Medicare, in-network, walk-in) before writing new content. Effort S · Impact Med–High.
4. **Physician entity brand exists.** "mariam nadi" 21.4% CTR p1.2, "dr mariam nadi" 50i p15.2. Add `Physician`/`Person` schema + doctor bio pages so name queries land on owned pages and feed AI entity grounding. Effort S · Impact Med.
5. **Service queries with volume, weak ranks.** "dental implants san pedro" 83i p20.2, "dentures san pedro ca" 18i p27.4, `/how-dental-implants-in-san-pedro/` 122i p36. Strengthen or consolidate into office pages. Effort M · Impact Med–High.
6. **Desktop CTR anomaly.** 7,927i at 0.6% vs mobile 1.6% — audit desktop-visible titles/snippets (same fix as #3). Effort S · Impact Med.

## Top 5 if only five things get done

1. Claim the 4 missing GBPs (B-1) — everything else compounds on this. *(Needs practice-owner access — pending user.)*
2. Launch per-office review generation + 18-day cadence (B-2). *(Needs owner access.)*
3. Surface review stars + `aggregateRating` per branch once real (A-2/B-8). *(Sequenced after B-1/B-2.)*
4. ~~UTM-tag all outbound links (A-4).~~ **DONE 2026-11-23** — 7 links (`utm_source=doctorsmile_com`, campaign `chooser_panel`/`office_card`).
5. ~~Label the Toothopia/El Segundo link (A-3) + sticky mobile call bar (A-1).~~ **DONE 2026-11-23** — button "Toothopia Info", `sameAs` + branch `url` updated; sticky CTA bar on mobile.

**Implemented on-page 2026-11-23 (A-1, A-3, A-4):** sticky mobile call bar (scrolls to #locations; no single group number exists to dial), Toothopia labeling + schema `sameAs`/branch `url` → `toothopiadental.com/dentist-near-el-segundo`, UTM tags on all 7 practice-site links, `llms.txt` note that Toothopia = formerly Dr. Smile El Segundo, same ownership.

---

*Compiled 2026-11-23 from: LOCAL-SEO-ANALYSIS (2026-11-23), GEO-ANALYSIS (2026-11-23), CONTENT-BRIEF (2026-08-31), 2026 web research (Whitespark LSRF, Chat Radar, 522-site dentist-website study, dental CRO benchmarks), and verification search on toothopiadental.com ownership.*
