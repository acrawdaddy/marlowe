# Marlowe — landing site

Static, single-page marketing site for **Marlowe**, a private, cash-pay care-coordination
membership for older adults and their aging parents. No build step, no framework, no backend —
just `index.html` and a handful of root files, hosted on Vercel's CDN.

> ⚠️ **Illustrative concept mockup.** Brand name, phone number, ratings (4.9/5), testimonials,
> and the clinical reviewer are **placeholders**. They must be replaced or removed, and the
> mockup disclaimer dropped, before any real public launch. See **Before a real launch** below.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire homepage — HTML + CSS + inline SVG + JSON-LD. Self-contained except Google Fonts. |
| `robots.txt` | Allows Google + AI crawlers (GPTBot, PerplexityBot, ClaudeBot, …); blocks CCBot; points to the sitemap. |
| `llms.txt` | Plain-language overview for AI assistants. |
| `pricing.md` | Machine-readable pricing for AI agents (`/pricing.md`). |
| `sitemap.xml` | Single-URL sitemap, referenced by `robots.txt`. |
| `favicon.svg` | Logomark favicon. |
| `og-image.svg` | Link-preview image (see note below). |
| `vercel.json` | Clean URLs + security/cache headers. |

## Local preview

It's a static file — open `index.html` in a browser, or serve the folder with any static server:

```bash
# Python (no install needed on most machines)
python -m http.server 8000
# then visit http://localhost:8000
```

## Deploy (Vercel)

This is a zero-config static deploy. Pushing to the connected GitHub repo, or running
`vercel --prod`, ships it. No framework preset, output directory, or build command is required.

## SEO / AI-search

- `<head>` carries title, meta description, canonical, robots, Open Graph + Twitter cards.
- JSON-LD `@graph`: `WebSite`, `Organization`+`MedicalBusiness`, `Service` (both price offers),
  and `FAQPage`. All absolute URLs point at the live domain.
- `robots.txt`, `llms.txt`, and `pricing.md` resolve at the site root for AI answer engines.

## Before a real launch

This repo is wired for a demo. Before going public for real:

1. **Replace placeholders** — real phone, real/removed ratings & testimonials, real clinical
   reviewer (or remove the line). **Do not ship fake ratings** (Google structured-data policy +
   legal risk). Remove the "Illustrative concept mockup" disclaimer.
2. **Custom domain** — add it in Vercel, then swap the deployment URL in `index.html` (canonical,
   OG, Twitter, JSON-LD `@id`/`url`), `robots.txt`, `llms.txt`, and `sitemap.xml`.
3. **Real OG image** — replace `og-image.svg` with a 1200×630 raster (`.jpg`/`.png`); some
   platforms don't render SVG previews.
4. **Wire the CTAs** — the "Book"/"Choose"/"Talk to us" buttons currently link to `#`. Point them
   at a scheduler (Cal.com / Calendly) or a contact form that collects **contact details only —
   never health information** (keeps the form out of PHI/HIPAA scope).
5. **Legal pages** — add Privacy Policy, Terms, accessibility statement; link them from the footer
   (currently `#`). Have counsel review copy and claims.
6. **Analytics + consent** — add privacy-friendly analytics (Vercel Web Analytics / Plausible),
   plus a consent banner if cookie-based.
