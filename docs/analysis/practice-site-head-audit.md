# Practice Site Head Audit — doctorsmileonline.com

Date: 2026-11-23 — static curl audit (no rendering, no JS execution). All URLs returned HTTP 200.

| URL | title | meta description (truncated 80ch) | canonical | robots |
|---|---|---|---|---|
| / | Find Your Nearest Office in Corona del Mar, Newport Beach \|Dr. Smile | Find your nearest Dr. Smile office in Corona del Mar and Newport Beach for quality dental care… | / | follow, index, max-snippet:-1, max-video-preview:-1, max-image-preview:large |
| /dentist-san-pedro | Best Dentist in San Pedro \| Doctor Smile | Looking for a best dentist in San Pedro? Doctor Smile offers expert care and personalized… | /dentist-san-pedro/ | follow, index, … large |
| /dentist-san-pedro?utm_source=google_business_profile | Best Dentist in San Pedro \| Doctor Smile | Looking for a best dentist in San Pedro? Doctor Smile offers expert care and personalized… | /dentist-san-pedro/ | follow, index, … large |
| /dentist-lomita/ | Trusted Dentist in Lomita, CA for Complete Dental Care | Looking for a trusted dentist in Lomita, CA? Dr. Smile provides expert cosmetic, family… | /dentist-lomita/ | follow, index, … large |
| /dentist-torrance/ | Best Dentist in Torrance \| Expert Dental Care & Services | Looking for a trusted dentist in Torrance? Get expert dental care, from cosmetic to preventive… | /dentist-torrance/ | follow, index, … large |
| /dentist-newport/ | Dentist in Corona del Mar & Newport Beach \| Dr. Smile | Looking for a trusted dentist in Corona del Mar & Newport Beach? Get expert dental care, from… | /dentist-newport/ | follow, index, … large |
| /best-affordable-dentist-in-san-pedro/ | Choose the Best Affordable Dentist in San Pedro | Discover how to find the best affordable dentist in San Pedro. Get expert tips on quality… | /best-affordable-dentist-in-san-pedro/ | follow, index, … large |
| /best-walk-in-dentist-in-torrance/ | Best Walk-In Dentist in Torrance for Fast Emergency Care | Need urgent dental care? Visit our trusted walk-in dentist in Torrance for fast, same-day… | /best-walk-in-dentist-in-torrance/ | follow, index, … large |
| /best-dental-clinic-in-newport-beach/ | Best Dental Clinic in Newport Beach, CA for Families | Discover how to choose the best dental clinic in Newport Beach, CA for your family’s care.… | /best-dental-clinic-in-newport-beach/ | follow, index, … large |
| /contact | Contact Dr. Smile \| Corona del Mar & Newport Beach | Contact Dr. Smile in Corona del Mar and Newport Beach to schedule your dental appointment… | /contact/ | follow, index, … large |

## Findings

- (a) UTM URLs self-canonicalize: yes — `?utm_source=google_business_profile` canonicalizes to `/dentist-san-pedro/` (clean URL, trailing slash).
- (b) No missing titles/descriptions; all pages have one title + one meta description. Generic pattern: most office pages share near-identical description structure ("Looking for a trusted/best dentist in …"). Duplication risk is moderate — titles are distinct per page, but several descriptions reuse the same phrasing ("for healthy and confident smiles" appears in torrance/newport; "Looking for a trusted dentist" appears in torrance, newport, lomita).
- (c) `best-*` pages have distinct titles (Choose the Best Affordable Dentist… / Best Walk-In Dentist… / Best Dental Clinic…) and distinct descriptions, but their descriptions reuse the same "Discover how to…" template (san-pedro affordable and newport-beach clinic are near-clones in phrasing).

No 404s or bot-blocks encountered. No pages marked noindex.
