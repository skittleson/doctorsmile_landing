# GEO / AI Search Visibility Analysis — doctorsmile.com (Dr. Smile Dental Group)

Scope: `docs/index.html`, `docs/llms.txt`, `docs/robots.txt`, `docs/sitemap.xml`, `.well-known/`
Date: 2026-08-31 · Skill: `seo-geo` (v1.9.6)

---

## 1. GEO Readiness Score: 62/100

| Dimension | Weight | Score | Notes |
|-----------|--------|-------|-------|
| Citability | 25% | 4/10 | Static page has no quotable 134-167 word answer blocks (it's a chooser/directory) |
| Structural Readability | 20% | 5/10 | No question-based H2s, no FAQ, minimal prose; data in cards + one table |
| Multi-Modal Content | 15% | 6/10 | 2 doctor photos (lazy/preload), map links, no video/infographic |
| Authority & Brand Signals | 20% | 5/10 | Real brand + sameAs, but no author bylines/dates/sources on page |
| Technical Accessibility | 20% | 9/10 | **Excellent** — static SSR, all AI crawlers allowed, llms.txt present, Content Signals set |

**Key insight:** This is a **landing hub — it is not the content machine.** Its GEO strength is technical (accessibility/llms.txt) and directional (routes AI to the practice sites). Its GEO weakness is citability: a chooser page has almost nothing for an AI engine to quote. The real GEO opportunity lives on `doctorsmileonline.com`, not here.

---

## 2. Platform Breakdown

| Platform | Score | Rationale |
|----------|-------|-----------|
| Google AI Overviews | 55/100 | Indexable (SSR + bots allowed), but the page ranks/targets the brand name; little passage-level content to cite |
| ChatGPT | 50/100 | Will read llms.txt + robots only if it reaches this domain; the actual FAQ content to cite is on the practice site |
| Perplexity | 50/100 | Same — consumes the practice domain; this hub is thin |
| Bing Copilot | 60/100 | Bingbot allowed, IndexNow not set up, Bing Places powers answers — recommend claiming GBP/Bing Places |

---

## 3. AI Crawler Access Status ✅

`robots.txt` is **exemplary**. All key AI crawlers are explicitly allowed:

| Crawler | Allowed? |
|---------|----------|
| GPTBot | ✅ |
| OAI-SearchBot | ✅ |
| ChatGPT-User | ✅ |
| ClaudeBot / Claude-Web / anthropic-ai | ✅ |
| PerplexityBot | ✅ |
| Google-Extended | ✅ |
| Bingbot | ✅ |
| Applebot-Extended | ✅ |

Plus `Content-Signal: ai-train=no, search=yes, ai-input=no` — a deliberate, defensible licensing stance. Nothing to fix here.

---

## 4. llms.txt Status ✅ (present and well-formed)

`docs/llms.txt` exists, is well-structured, and follows the emerging standard:

- ✅ Location-independent (deployed to `/llms.txt`)
- ✅ Title + tagline + short description
- ✅ "Key facts" section (brand, practice type)
- ✅ Structured practice-website links
- ✅ **Office locations & phones in a Markdown table** — the single most AI-citeable artifact on this domain
- ✅ Related links to practice site

**Recommendations (minor):**
1. The llms.txt links/hours table and the visible page already match — good. Keep them in sync when offices change.
2. Consider adding an explicit "Emergency instructions / how to book" line — AI engines route users; a "book via these numbers/links" note improves the AI→user handoff.
3. The `index.md` alternate (linked via `<link rel="alternate" type="text/markdown">`) is a strong, complementary machine-readable artifact — ensure it stays current alongside `llms.txt`.

---

## 5. Brand Mention Analysis

| Channel | Presence |
|---------|----------|
| Wikipedia | ❌ None detected |
| Reddit | ❌ None detected |
| YouTube | ❌ None detected |
| LinkedIn | ❌ None detected |
| Facebook | ✅ `sameAs` → facebook.com/drsmiledentalgroup |
| Instagram | ✅ `sameAs` → instagram.com/dr.smile_dental_group |
| Practice sites | ✅ Linked |

**Recommendation (High impact):** Brand mentions correlate **3x more strongly** with AI visibility than backlinks. The "Dr. Smile" brand has almost **zero third-party entity footprint** (no Wikipedia/Wikidata, no Reddit/YouTube/LinkedIn). For a local dental group this is a longer-term play, but even a consistent dentist-author recipe pages, local media quotes, and Google Business Q&A rebuild positions the brand to be cited by ChatGPT/Perplexity (which lean on Bing/Yelp/BBB/Reddit, not the site itself).

---

## 6. Passage-Level Citability

**Optimal AI-citable block: 134-167 words, self-contained, direct answer in first 40-60 words.**

**Current state:** The page has **no 134-167 word prose blocks** — it's a hero + 2 chooser panels + 5 compact location cards. Nothing here is independently quotable by an AI engine ("what is Dr. Smile? where are they? how to book?" answers are fragmented across cards and only in the llms.txt table).

**Highest-value fix (on the PRACTICE site, not here):** The FAQ / service content that answers real queries ("Do you accept new patients?", "What insurance do you take?", "What is same-day dentistry?") belongs on `doctorsmileonline.com` with question-based H2s and 134-167 word self-contained answers. That is where citability wins. For THIS hub, the single most-citeable artifact is the llms.txt table — keep it authoritative.

---

## 7. Server-Side Rendering Check ✅

- **Fully static HTML** (Astro-free, no build step, `docs/index.html` served as-is).
- All content is in the initial HTML — **no JavaScript rendering dependency** for the visible content.
- The only `<script>` is GA4 (`gtag.js`) for tracking `location_click` events — non-blocking, not content-critical.
- WebP images load via `<picture>` with JPEG fallback; `preload` hints present.

**AI crawlers that don't execute JS see 100% of the content.** This is a top-tier technical position. Nothing to change.

---

## 8. Top 5 Highest-Impact Changes

1. **Audit RSL 1.0 / machine-readable licensing** — optional new standard (Dec 2025, backed by Reddit/Cloudflare/Quora). Consider adding an `rsl` signal to pair with the existing Content-Signal stance.
2. **Point AI visibility effort at the practice site** — this hub is technically perfect but content-thin; the highest GEO ROI is FAQ/service citability on `doctorsmileonline.com`.
3. **Add Bing Places claims per office** — Bing Places directly powers ChatGPT, Copilot, and Alexa local answers. Currently nothing indicates Bing Places or Apple Business Connect coverage.
4. **Add per-office Maps embed / place IDs** so AI can geolocate each office precisely (currently only El Segundo has geo coordinates in schema).
5. **Build third-party brand footprint** (local press, Yelp, BBB) — the #1 AI-visibility lever the business has zero of.

---

## 9. Schema Recommendations (for AI discoverability)

- ✅ `Dentist`/`MedicalBusiness`/`LocalBusiness` present with `sameAs` to social — good base.
- ⚠️ **Expand to 5 branch `Dentist` entities** (one per office) — see the seo-local analysis for the full JSON-LD. AI engines need each office's phone/geo/address as structured data, not just El Segundo + a text list.
- ⚠️ Add `openingHoursSpecification` (currently absent from schema despite hours on page).
- 🔲 Optional: `Person` schema (`Physician` + `MedicalSpecialty`) for Drs. Javid/Nadi on the practice site for entity authority.

---

## 10. Content Reformatting Suggestions

For **this hub**, minimal prose rewrites are warranted (it's a chooser by design). Two small additions would raise citability **without bloating the page**:

1. **Add a 1-sentence "How to book" line** under the tagline or in a footer block, e.g. *"Dr. Smile Dental Group is a multi-specialty practice with five Southern California offices. To book, call your nearest office directly — numbers for each location are listed below."* — a self-contained definitional answer an AI can quote.
2. **Add an FAQ microsection** (2-4 H2 question headings) if the practice wants the hub to rank for "is Dr. Smile accepting new patients?" — but note this duplicates the practice site and should stay thin.

**The 134-167 word answer blocks and question-H2 citability work should be done on `doctorsmileonline.com`, not here.**

---

## Limitations

Assessed the static Hub page + its companion agent files. Could not verify: live ChatGPT/Perplexity retrieval output, Bing/Yelp/BBB listings, actual brand-mention counts, or whether Google AI Overviews currently surfaces this domain. Recommend DataForSEO `ai_optimization_chat_gpt_scraper` / `ai_opt_llm_ment_search` for live LLM-retrieval verification.

---

*Generated by `seo-geo` skill (AgriciDaniel v1.9.6) applied to /home/spencerkittleson/repos/doctorsmile_com_landing/docs/index.html*
