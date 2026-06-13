# cre-ai-team.com

The cre-ai-team marketing site. Static HTML, no build step, deployed via Cloudflare Pages.

## Stack

- Single `index.html` — no framework, no build
- Fonts: Young Serif + Inter via Google Fonts CDN; Young Serif **Bold** self-hosted in `/fonts` (used for the logo wordmark)
- Cloudflare Pages for hosting (auto-deploys on push to `main`)
- Custom domain: `cre-ai-team.com`

## Editing the site

Just edit `index.html` directly. Commit and push to `main` — Cloudflare Pages auto-deploys in ~30 seconds.

For copy changes, the file is organized top-to-bottom in the order sections appear on the page:
1. `<nav>` — top navigation
2. `<section class="hero">` — first viewport
3. `<section class="band">` — "A practice, not a product" intro
4. `<section class="section" id="practice">` — three lanes (Deploy / Embed / Steward)
5. `<section class="ships" id="ships">` — six concrete deliverables
6. `<section class="industries">` — asset class strip
7. `<section class="process" id="engagement">` — three-step engagement
8. `<section class="principles">` — four operating principles
9. `<section class="cta" id="contact">` — closing CTA
10. `<footer>` — colophon

## Local preview

Open `index.html` in a browser. That's it — no server needed.

For a fancier local dev experience with auto-reload:
```bash
npx serve .
```

## Files

- `index.html` — the entire site
- `_headers` — Cloudflare Pages security headers (X-Frame-Options, HSTS, etc.)
- `_redirects` — `www.cre-ai-team.com` → `cre-ai-team.com` apex redirect
- `robots.txt` — search engine permissions
- `sitemap.xml` — for SEO crawlers

## Deploying

Cloudflare Pages is connected to this repo. Every push to `main` triggers an auto-deploy. Build settings:
- **Framework preset**: None
- **Build command**: (empty)
- **Build output directory**: `/`
