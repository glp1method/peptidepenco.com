# PeptidePen Co. — Claude Instructions

## Project Overview
Static marketing website for PeptidePen Co., a precision peptide delivery supply company.
Hosted on GitHub Pages via the `glp1method/peptidepenco.com` repo, deployed automatically on push to `main`.

## Tech Stack
- Plain HTML5 / CSS3 / vanilla JavaScript — no frameworks, no build tools
- Google Fonts: Montserrat, Inter, Space Mono
- Shopify store linked externally: `https://peptidepenco-2.myshopify.com`

## File Structure
```
index.html          — Homepage
store.html          — Product listing page
how-it-works.html   — 3-step process page
about.html          — Company mission & values
faq.html            — FAQ accordion
contact.html        — Contact form (not yet wired to a backend)
css/styles.css      — Single stylesheet for entire site
assets/
  logo3.png         — Current active logo (dark background optimized)
  logo.png          — Old logo (unused)
  logo2.png         — Old logo (unused)
```

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
- CSS cache-busting: stylesheet linked as `css/styles.css?v=2` — increment version number when making CSS changes that need to bypass browser cache
- Nav on inner pages uses `class="nav scrolled"` (hardcoded). Homepage uses `class="nav"` and gets `.scrolled` added via scroll JS listener.
- All pages share identical nav and footer structure. When adding nav links, update ALL 6 HTML files (desktop nav-links, mobile nav-mobile-links, and footer Company column).
- Active nav link uses `class="active"` on the `<a>` tag matching the current page.
- `<img>` tags must always have `alt` attributes.

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
- Product prices are `$0.00` placeholders — update when products are live
- Hero and product image placeholders need real photography
- Legal pages (Privacy Policy, Terms of Use, FDA Disclaimer) are `href="#"` placeholders
