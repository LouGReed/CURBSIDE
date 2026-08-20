# curbside-cre.com

The Curbside CRE marketing site. Static HTML, no build step, deployed via Cloudflare Pages.

## Stack

- Single `index.html` — no framework, no build, no bundler
- Fonts: Young Serif + Inter via Google Fonts CDN; Young Serif **Bold** self-hosted in `/fonts` (used for the logo wordmark)
- Cloudflare Pages for hosting (auto-deploys on push to `main`, ~30 seconds)
- Custom domain: `curbside-cre.com` (see `CNAME`)

## Positioning

The site sells one offer: a **done-for-you ChatGPT advertising build for
commercial brokerages**, with setup fees half off through Labor Day
(Monday, September 7, 2026). **No dollar figures appear anywhere on the page** —
pricing scales per brokerage and is set in conversation, not published.

## Editing the site

Just edit `index.html` directly. Commit and push to `main` — Cloudflare Pages
auto-deploys in ~30 seconds. The file is organized top-to-bottom in the order
sections appear on the page:

1. `<nav>` — top navigation (logo lockup, `How it works` / `The offer`, CTA button)
2. `<section class="hero">` — "Your next client is asking an AI who they should call."
3. `<section class="section" id="proof">` — the ChatGPT screenshot + who it named
4. `<section class="section" id="how">` — channel comparison (Meta / Google / ChatGPT)
5. `<section class="section" id="offer">` — the Labor Day offer panel + countdown
6. `<section class="section">` — why this channel, right now (three-up)
7. `<section class="argument">` — "the revenue side has to scale with it" band
8. `<section class="suite">` — the product suite, demoted to a credibility strip
9. `<section class="cta" id="contact">` — closing CTA
10. `<footer>` — brand lockup + offer-ends date

The only CTA target on the page is the Google Calendar booking link. There is no
email address and no form — don't reintroduce them without asking.

## When the offer ends

The offer deadline lives in **one place**: the `DEADLINE` constant in the
countdown `<script>` at the bottom of `index.html`:

```js
var DEADLINE = Date.parse('2026-09-08T05:00:00Z'); // end of Mon Sep 7, 2026, Central
```

- The live countdown, its post-deadline swap, and the footer "Offer ends …" date
  all derive from this constant.
- After the deadline passes, the page **degrades on its own**: the "Half off /
  setup fees" stack and countdown hide, replaced by a line telling visitors the
  discount has closed. The offer section still reads correctly with the discount
  gone — nobody has to remember to edit it.

**To move the offer date:** change the `DEADLINE` line, then update the two
human-readable strings that must match it — the `Sept 7` in the offer block
(`.offer-through`) and the footer fallback text in `#foot-date`.

## Local preview

Open `index.html` in a browser. That's it — no server needed.

For auto-reload:
```bash
npx serve .
```

## Files

- `index.html` — the entire site
- `assets/chatgpt-answer-austin.png` — the ChatGPT proof screenshot (§ proof block)
- `fonts/` — self-hosted Young Serif Bold (wordmark)
- `_headers` — Cloudflare Pages security headers (X-Frame-Options, HSTS, etc.)
- `robots.txt` — search engine permissions
- `sitemap.xml` — for SEO crawlers
- `CNAME` — custom domain for Cloudflare Pages

## Deploying

Cloudflare Pages is connected to this repo. Every push to `main` triggers an
auto-deploy. Build settings:
- **Framework preset**: None
- **Build command**: (empty)
- **Build output directory**: `/`
