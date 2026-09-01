# Hreflang & International SEO Analysis — doctorsmile.com (Dr. Smile Dental Group)

Scope: `docs/index.html` + `docs/sitemap.xml`
Date: 2026-08-31 · Skill: `seo-hreflang` (v1.9.6)

---

## Summary

| Metric | Value |
|--------|-------|
| Total pages scanned | 1 (`https://www.doctorsmile.com/`) |
| Language versions detected | **1 — English only** (`<html lang="en">`) |
| Hreflang tags present | **0** |
| x-default | N/A (single-language) |
| HTML `lang` attribute | ✅ `en` (valid ISO 639-1) |
| Issues found | **0 critical / 0 high** (no hreflang is *correct* here) |

**Verdict: This is a single-language site. Hreflang is NOT required and should NOT be added.** Adding hreflang to a single-language page would be an error, not an improvement.

---

## 1. Language Detection

Detected signals:
- `<html lang="en">` — English, valid ISO 639-1 code
- No `es/` subdirectory, no subdomain, no ccTLD, no alternate-language versions anywhere in the repo
- `docs/` contains a single `index.html`, `index.md`, `llms.txt`, `robots.txt`, `sitemap.xml` — all English
- The deployed `sitemap.xml` lists exactly one URL (`https://www.doctorsmile.com/`)

**No multilingual structure exists.** The correct state for this page is: **no hreflang**, single canonical.

---

## 2. Validation Checks (result: no hreflang, so no failures)

| Check | Result | Notes |
|-------|--------|-------|
| Self-referencing tags | N/A | Would only apply if alternates existed |
| Return tags | N/A | N/A |
| x-default | N/A | Single language — no fallback needed |
| Language codes | ✅ | `en` is valid |
| Region codes | N/A | No region-qualified alternates |
| Canonical alignment | ✅ | Single canonical `https://www.doctorsmile.com/` correct |
| Protocol consistency | ✅ | HTTPS everywhere |
| HTML vs sitemap duplication | ✅ | No hreflang in either (correct) |

---

## 3. Cross-Domain Note (IMPORTANT — the real i18n-relevant relationship)

This is a **chooser hub** that routes visitors to **two separate practice domains**:

- `http://www.drsmiledental.com/` (Hossein Javid, DDS)
- `https://doctorsmileonline.com/` (Mariam Nadi & Kayvon Javid, DDS)

These are **sibling practice sites, NOT hreflang alternates**. They are different content on different domains. Do **NOT** add cross-domain hreflang linking this hub to either practice site — that would incorrectly signal to Google that the chooser page and a practice page are the same content in different languages/regions, which would dilute authority and confuse indexing.

The correct relationship is **outbound internal-style linking** (which already exists), plus:
- Each practice site should be verified separately in Google Search Console
- Consider a `rel="canonical"`-safe click-through only; no shared-context signals

**Recommendation:** If the practice ever launches a Spanish version of the site (the Dr. Smile brand serves a large Hispanic market in the South Bay / LA), that Spanish content should live either on a `/es/` subdirectory of `doctorsmileonline.com` with proper `en`/`es`/`x-default` hreflang, or on the practice site — **not** on this chooser hub. See §5 for the future-proofing note.

---

## 4. Cultural Adaptation Assessment

Single-language (English), so a full cultural profile pass is not applicable. Notes:
- The practice serves Los Angeles South Bay (El Segundo, Lomita, San Pedro, Torrance) + Newport, a market with a **large Spanish-speaking population**.
- Given the brand's local market, a Spanish-language version is a *strategic* opportunity, but SEO-wise it belongs on the practice site (`doctorsmileonline.com`) with proper hreflang — not on this thin chooser page.

---

## 5. Recommended Implementation (ONLY if a Spanish version is added later)

If the practice site adds Spanish, use the HTML `<link>` method (small site, <50 variants):

English page:
```html
<link rel="alternate" hreflang="en" href="https://doctorsmileonline.com/" />
<link rel="alternate" hreflang="es" href="https://doctorsmileonline.com/es/" />
<link rel="alternate" hreflang="x-default" href="https://doctorsmileonline.com/" />
```

Spanish page (`/es/`):
```html
<link rel="alternate" hreflang="en" href="https://doctorsmileonline.com/" />
<link rel="alternate" hreflang="es" href="https://doctorsmileonline.com/es/" />
<link rel="alternate" hreflang="x-default" href="https://doctorsmileonline.com/" />
```

Rules this satisfies: self-referencing tags, bidirectional return tags (full mesh), a single `x-default`, valid `es`/`en` codes, matching HTTPS protocol, and canonical-URL alignment. Include the `xmlns:xhtml` namespace in the sitemap if the sitemap method is chosen instead.

---

## 6. Actionable Recommendation for THIS Repo

**Do nothing to `docs/index.html` re: hreflang.** It is correctly configured as a single-language canonical page. The only i18n-related action is **future-proofing**: if a Spanish version is ever planned, it belongs on the practice site, and this doc captures the exact hreflang markup to use then.

**Low-priority housekeeping:** The `sitemap.xml` uses `<changefreq>`/`<priority>`, which Google ignores (deprecated). Safe to leave, but not a hreflang concern.

---

*Generated by `seo-hreflang` skill (AgriciDaniel v1.9.6) applied to /home/spencerkittleson/repos/doctorsmile_com_landing/docs/index.html*
