# GEO / AI Search Visibility Analysis — doctorsmile.com (Dr. Smile Dental Group)

Scope: `docs/index.html`, `docs/llms.txt`, `docs/index.md`, `docs/robots.txt`, `docs/sitemap.xml`, `.well-known/`
Date: 2026-11-23 · Skill: `seo-geo` (v1.9.6)

---

## 1. GEO Readiness Score: 66/100 (was 62 on 2026-08-31; 64 at report time)

| Dimension | Weight | Score | Notes |
|-----------|--------|-------|-------|
| Citability | 25% | 5/10 | Definitional intro + self-contained booking paragraph now exist (~30–50 words each), but still no 134–167 word answer blocks |
| Structural Readability | 20% | 6/10 | Clean H1→H2→H3 hierarchy, location grid + closing blocks; still no question-based H2s / FAQ |
| Multi-Modal Content | 15% | 6/10 | 2 doctor photos (preload/webp), map links; no video/infographic |
| Authority & Brand Signals | 20% | 6/10 | Richer schema (5 branch entities w/ geo + hours); still no bylines, dates, or citations on page |
| Technical Accessibility | 20% | 10/10 | **Excellent** — fully static SSR, all AI crawlers allowed, llms.txt + index.md + ai-catalog + Content-Signal. §3 contradiction and stale lastmod both fixed 2026-11-23 |

**Key insight (unchanged):** This is a **landing hub, not the content machine.** Its GEO strength remains technical + directional. Since August the schema and intro prose closed the cheap gaps; the remaining score is trapped behind content that belongs on `doctorsmileonline.com`.

---

## 2. Platform Breakdown

| Platform | Score | Rationale |
|----------|-------|-----------|
| Google AI Overviews | 58/100 | Indexable; per-office geo+hours in schema now helps local pack/AIO grounding; still brand-targeted, thin passages |
| ChatGPT | 52/100 | llms.txt/robots excellent; citable FAQ content still lives on the practice site |
| Perplexity | 52/100 | Same — hub is thin; llms.txt table is the best cite |
| Bing Copilot | 62/100 | Bingbot allowed; Bing Places/GBP coverage still unverifiable from the page |

---

## 3. AI Crawler Access Status ✅ (one new contradiction)

`robots.txt` explicitly allows: GPTBot, OAI-SearchBot, ChatGPT-User, ClaudeBot/Claude-Web/anthropic-ai, PerplexityBot, Google-Extended, Bingbot, FacebookBot, Applebot-Extended. `Content-Signal: ai-train=no, search=yes, ai-input=no` unchanged — deliberate, defensible.

⚠️ **New finding:** `Disallow: /.well-known/` now blocks the `ai-catalog.json` that the page advertises via `<link rel="ai-catalog">`. Crawlers honoring robots can't fetch the catalog they're pointed at. Either allow `/.well-known/ai-catalog.json` explicitly (`Allow:` line) or move the catalog to a public path.

✅ **Fixed 2026-11-23:** `robots.txt` now has `Allow: /.well-known/ai-catalog.json` (listed before the `Disallow: /.well-known/`, so longest-match and first-match crawlers agree). `sitemap.xml` lastmod bumped to 2026-11-23.

---

## 4. llms.txt Status ✅ (improved since August)

Present, well-formed, and now includes a **Booking section** ("call your nearest office… Spanish-speaking patients served at all offices") — the August recommendation to add explicit booking/emergency routing guidance is **DONE**. Locations/phones table remains the most AI-citeable artifact on the domain and matches the page. `index.md` alternate and `ai-catalog.json` (subject to §3 robots issue) are consistent with it.

**Still open:** keep all three artifacts in sync when offices change (no automated check exists).

---

## 5. Brand Mention Analysis

| Channel | Presence |
|---------|----------|
| Wikipedia / Wikidata | ❌ None |
| Reddit / YouTube / LinkedIn | ❌ None |
| Facebook / Instagram | ✅ via `sameAs` |
| Practice sites (drsmiledental.com, doctorsmileonline.com) | ✅ Linked |

**Still open (High impact):** third-party entity footprint (GBP/Bing Places per office, Yelp, BBB, local press) remains the #1 lever with zero coverage. Brand mentions correlate ~3x more with AI visibility than backlinks; no change detectable from on-site files since August.

---

## 6. Passage-Level Citability

Optimal block: 134–167 words, self-contained, direct answer in first 40–60 words.

**Since August (partially DONE):**
- ✅ Hero intro is now a definitional sentence: "Dr. Smile Dental Group is a family-owned, multi-specialty dental practice with five offices across Los Angeles' South Bay and Newport Beach, California — welcoming new and current patients." (~30 words — quotable identity answer, though below optimal length).
- ✅ "New Patients Welcome" closing block is a self-contained booking answer (~50 words) — answers "how do I book with Dr. Smile?"
- ✅ Bilingual Spanish booking block — helps Spanish-language AI queries.

**Still open:** no 134–167 word block, no question-H2s. Highest-value citability work still belongs on `doctorsmileonline.com` (service/FAQ pages).

---

## 7. Server-Side Rendering Check ✅

Fully static HTML; all content in initial response; only JS is GA4 (non-blocking) plus inline `trackLocationClick` onclick handlers. AI crawlers without JS see 100% of content. Nothing changed since August; nothing to fix.

---

## 8. Top 5 Highest-Impact Changes

1. **Fix the robots/ai-catalog contradiction** — `Disallow: /.well-known/` blocks the advertised `ai-catalog.json`. One-line robots fix. *(New.)*
2. **Point AI visibility effort at `doctorsmileonline.com`** — FAQ/service pages with question H2s + 134–167 word answers. *(Still open.)*
3. **Claim GBP + Bing Places per office** — powers ChatGPT/Copilot/Alexa local answers. *(Still open.)*
4. **Build third-party brand footprint** (Yelp, BBB, local press, Wikidata item). *(Still open.)*
5. **Bump `sitemap.xml` lastmod on deploy** and consider RSL 1.0 alongside Content-Signal. *(New/minor.)*

**August items now DONE:** per-office geo coordinates in schema ✅; `openingHoursSpecification` per branch ✅; llms.txt booking guidance ✅; definitional intro + booking paragraph on page ✅; 5 branch `Dentist` entities ✅.

---

## 9. Schema Recommendations

- ✅ **DONE:** 5 branch `Dentist`/`MedicalBusiness`/`LocalBusiness` entities with `branchOf`/`parentOrganization`, per-office `geo` and `openingHoursSpecification` — exactly what August asked for. Well-formed `@graph` with stable `@id`s.
- ⚠️ Hours in schema say Mon–Fri 08:00–18:00 only; page says "Sat/Sun by appt." — consistent enough, but consider a note or `specialOpeningHoursSpecification` if Saturday appt hours stabilize.
- 🔲 Still open: `Physician` `Person` schema for Drs. Javid/Nadi on the practice site.
- 🔲 Optional: `medicalSpecialty` entries on each branch; `hasMap` (Google Maps place URL) per branch.

---

## 10. Content Reformatting Suggestions

Minimal for a chooser hub. Since August the two August suggestions (how-to-book line; definitional intro) are **DONE** — do not add an FAQ microsection here (duplication risk with practice site stands).

Remaining, low-effort:
1. Consider merging intro + booking block into one ~140-word self-contained paragraph ("What is Dr. Smile / where / how to book") to hit the optimal citability band without adding sections.
2. Keep per-office service blurbs (they now differentiate cards well); mirror any changes into `llms.txt`/`index.md`.

---

## Limitations

Static-file assessment only. Could not verify: live ChatGPT/Perplexity retrieval, GBP/Bing Places/Yelp/BBB listings, actual brand-mention counts, or whether the deployed site matches these files (including whether `/.well-known/ai-catalog.json` serves with robots blocking). Recommend DataForSEO `ai_optimization_chat_gpt_scraper` / `ai_opt_llm_ment_search` for live LLM-retrieval verification.

---

*Generated by `seo-geo` skill (AgriciDaniel v1.9.6) applied to /root/doctorsmile_landing/docs/index.html*
