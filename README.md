# Dr. Smile Dental Group — Landing Page

Static recreation of [https://www.doctorsmile.com/](https://www.doctorsmile.com/),
the landing/chooser hub for **Dr. Smile Dental Group** (South Bay & LA, California).

## About

The page routes visitors to the two practice sites:

- **Hossein Javid, DDS** → [drsmiledental.com](http://www.drsmiledental.com/)
- **Mariam Nadi, DDS & Kayvon Javid, DDS** → [doctorsmileonline.com](https://doctorsmileonline.com/)

and lists the practice's five office locations with new/current-patient phone numbers
(El Segundo, Lomita, San Pedro, Torrance, Whittier).

## Tech

- Single static `index.html` — no build step, no runtime dependencies
- Bootstrap-4-style grid reproduced with inlined (critical) CSS — Lighthouse 100/100/100/100
- Images optimized to WebP (JPEG fallback), single self-hosted webfont
- SEO / social / verification meta in `<head>` (Open Graph, Twitter, geo, JSON-LD `Dentist` schema, Google/Bing/etc. verification placeholders)

## Agent-ready files (per isitagentready.com)

- `robots.txt` (with AI-bot rules + Content Signals)
- `sitemap.xml`
- `llms.txt`, `humans.txt`, `index.md`
- `.well-known/ai-catalog.json`, `.well-known/security.txt`

See `research.md` for full research and the agent-readiness details.

## Local preview

```sh
python3 -m http.server 8123
# open http://localhost:8123/
```

## Deploy

Hosted on GitHub Pages from the `main` branch → https://skittleson.github.io/doctorsmile_landing/
