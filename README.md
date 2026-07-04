# Adel K. Wali — Portfolio

Personal portfolio for **Adel K. Wali** — QA/QC Engineer & ASNT SNT-TC-1A certified NDT Level II inspector (VT, RT) with 5+ years in upstream oil & gas, and founder/developer of **VetriX•IQ**, a SaaS platform that digitizes industrial inspection workflows.

A single-page, dependency-free static site — no build step, no framework, no package manager. Everything needed to run it is `index.html`.

## Live site

Deployed automatically from this repository:
- **Vercel** — connected via the Vercel GitHub integration; every push to `main` triggers a production deployment, and every pull request gets its own preview URL (see the Vercel bot comment on the PR for the exact link).
- **GitHub Pages** — the site can also be served directly from this repo if Pages is enabled (Settings → Pages → deploy from `main`).

> `robots.txt`, `sitemap.xml`, and the `<meta property="og:url">` / `<link rel="canonical">` tags in `index.html` currently point at a GitHub Pages URL (`https://adelalwali0-hub.github.io/adel-portfolio/`). If you serve the site from a different domain (e.g. a Vercel production domain or a custom domain), update those three places to match.

## Features

- **Dual-identity storytelling** — a single narrative bridging industrial inspection (QA/QC, NDT) and software engineering, with dedicated About, Experience, Credentials, Services and Contact sections
- **VetriX•IQ showcase** — a dedicated section for the author's SaaS product, with a WhatsApp-based "request a demo" call to action
- **Fully responsive** — desktop, tablet and mobile layouts, including an accessible hamburger menu below 760px with a no-JavaScript fallback (a plain stacked list, not a hidden menu)
- **Accessible by default** — skip-to-content link, semantic landmarks and headings, visible focus states, WCAG AA color contrast, and a scroll-reveal system that leaves content fully visible if JavaScript is disabled
- **SEO-ready** — `Person` JSON-LD structured data, Open Graph / Twitter meta tags, a canonical URL, `robots.txt`, `sitemap.xml`, and a tightened meta description
- **Performance-conscious** — the CV is a real PDF file fetched only on click (not embedded as base64 in the HTML), fonts load via a non-render-blocking `preload` pattern, and animations use `opacity`/`transform` only (no layout thrashing)
- **Tasteful micro-interactions** — scroll-spy navigation highlighting, staggered reveal-on-scroll, a count-up animation on the hero stats, and hover/lift states on cards — all disabled automatically under `prefers-reduced-motion`

## Technologies

- Plain **HTML5** + **CSS3** (custom properties, Grid, Flexbox, `clamp()`) — no CSS framework
- Vanilla **JavaScript** (ES5-compatible, no build tooling, no dependencies) for the mobile nav, scroll-spy, reveal animations, and stat count-up
- **Google Fonts** (Archivo, IBM Plex Mono, Source Sans 3) loaded via a non-blocking `<link rel="preload">` pattern
- Inline **SVG** for the favicon, the hero inspection seal, and the icon set (no icon library, no image assets)

There is no `package.json`, no `node_modules`, and nothing to run `npm install` against — the entire dependency surface is the two Google Fonts `<link>` tags in `<head>`.

## Project structure

```
.
├── index.html          # the entire site: markup, CSS, and JS in one file
├── Adel_K_Wali_CV.pdf   # downloadable CV, linked from the hero and contact sections
├── robots.txt           # crawler rules + sitemap pointer
├── sitemap.xml           # single-URL sitemap for search engines
├── CHANGELOG.md
└── README.md
```

## Local development

No build step is required. Any static file server works:

```bash
# Python (built in on most systems)
python3 -m http.server 8000

# or Node, if you have it installed
npx serve .
```

Then open `http://localhost:8000`.

To edit content, open `index.html` — the CSS is in the single `<style>` block in `<head>`, and the three behavior scripts (mobile nav / scroll-spy / reveal animations, stat count-up, back-to-top) sit at the end of `<body>`.

## Deployment

**Vercel (current setup)**
1. Import the repository at [vercel.com/new](https://vercel.com/new).
2. No build command or output directory is needed — Vercel serves the static files as-is.
3. Every push to `main` deploys to production; every pull request gets a preview deployment automatically.

**GitHub Pages**
1. Repository **Settings → Pages**.
2. Source: **Deploy from a branch** → `main` → `/ (root)`.
3. The site will be published at `https://<owner>.github.io/<repo>/`.

**Any other static host** (Netlify, Cloudflare Pages, S3, etc.) — upload the four files (`index.html`, `Adel_K_Wali_CV.pdf`, `robots.txt`, `sitemap.xml`) as-is; there is no build step to configure.

## License

All content (copy, résumé, and design) is © Adel K. Wali. No open-source license is granted for reuse of the personal content; the code structure may be used as a reference.
