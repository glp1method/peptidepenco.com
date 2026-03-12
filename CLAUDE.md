# PeptidePen Co. — Claude Instructions

## Project Overview
Static marketing website for PeptidePen Co., a precision peptide delivery supply company.
Hosted on GitHub Pages via the `glp1method/peptidepenco.com` repo, deployed automatically on push to `main`.

## Tech Stack
- Plain HTML5 / CSS3 / vanilla JavaScript — no frameworks, no build tools
- Google Fonts: Montserrat, Inter, Space Mono
- Shopify Storefront API: `https://peptidepenco-2.myshopify.com` (public token: `aff81598adbf890c258761da5bab6fb1`)

## File Structure
```
index.html          — Homepage (fetches featured product from Shopify)
how-it-works.html   — 3-step process page
about.html          — Company mission & values
faq.html            — FAQ accordion
contact.html        — Contact form (not yet wired to a backend)
css/styles.css      — Single stylesheet for entire site (current version: v=3)
sitemap.xml         — XML sitemap (submitted to Google Search Console)
robots.txt          — Crawler directives, references sitemap
assets/
  logo3.png         — Current active logo (dark background optimized)
  logo.png          — Old logo (unused)
  logo2.png         — Old logo (unused)
```

## Shopify Integration
Products are fetched live from the Shopify Storefront API on page load.

- **API endpoint:** `https://peptidepenco-2.myshopify.com/api/2024-01/graphql.json`
- **Token:** `aff81598adbf890c258761da5bab6fb1` (public Storefront API token — safe for frontend)
- **index.html** — fetches first product; populates hero image, featured product section (title, description, price, image, buy link)
- All "Shop Now" / "Buy Now" buttons across the site link directly to `https://peptidepenco-2.myshopify.com` and open in a new tab (`target="_blank"`)
- `store.html` was removed — the Shopify store serves as the product page

## Design System
All colors and tokens are defined as CSS variables in `:root` in `styles.css`:
- `--bg-dark: #040d1a` — main site background (near-black navy)
- `--light-gray: #081224` — card/section backgrounds
- `--navy: #0ea5e9` — primary accent (links, eyebrows, icons)
- `--gray: #7a9bb8` — body/secondary text
- `--off-white: #e8f0fe` — primary text color on dark backgrounds
- `--cyan: #38bdf8` — used in gradients
- Button primary: `#5ce1e6` background with `#040d1a` dark text

## Key Conventions
- CSS cache-busting: stylesheet linked as `css/styles.css?v=3` — increment version number when making CSS changes that need to bypass browser cache
- Nav on inner pages uses `class="nav scrolled"` (hardcoded). Homepage uses `class="nav"` and gets `.scrolled` added via scroll JS listener.
- All pages share identical nav and footer structure. When adding nav links, update ALL 5 HTML files (desktop nav-links, mobile nav-mobile-links, and footer Company column).
- Active nav link uses `class="active"` on the `<a>` tag matching the current page.
- `<img>` tags must always have `alt` attributes.

## SEO
Every page includes:
- Optimized `<title>` and `<meta name="description">` (150-160 chars)
- `<link rel="canonical">` pointing to `https://peptidepenco.com/[page]`
- `<meta name="robots" content="index, follow, ...">`
- Open Graph tags (`og:title`, `og:description`, `og:image`, `og:url`, `og:type`)
- Twitter Card tags
- JSON-LD structured data:
  - `index.html` — Organization + WebSite schema
  - `about.html` — Organization schema
  - `contact.html` — Organization + ContactPoint schema
  - `faq.html` — FAQPage schema (all 7 Q&As, eligible for Google rich snippets)
  - `how-it-works.html` — HowTo schema (3 steps, eligible for rich snippet cards)
- `sitemap.xml` submitted to Google Search Console
- OG image currently uses `assets/logo3.png` — replace with a proper 1200×630px image when available

## Deployment
```bash
git add <files>
git commit -m "message"
git pull origin main --rebase   # always pull before push
git push origin main
```
GitHub Pages deploys within ~1 minute of push.

## Known TODOs
- Contact form `action="#"` is a placeholder — needs a real backend (Formspree or similar)
- OG image (`assets/logo3.png`) should be replaced with a proper 1200×630px social preview image
- Hero and product image placeholders need real photography (currently pulled from Shopify if available)
- Legal pages (Privacy Policy, Terms of Use, FDA Disclaimer) are `href="#"` placeholders
