# Adel K. Wali — Portfolio

Personal portfolio for **Adel K. Wali** — QA/QC Engineer & ASNT SNT-TC-1A certified NDT Level II inspector (VT, RT) with 5+ years in upstream oil & gas, and founder/developer of **VetriX•IQ**, a SaaS platform that digitizes industrial inspection workflows.

A dependency-free static site — no build step, no framework, no package manager. It's two self-contained pages:
- `index.html` — the personal portfolio
- `vetrix-iq.html` — a dedicated SaaS landing page for VetriX•IQ, targeting oil & gas engineering companies (hero, problem/solution, features, screenshots, benefits, FAQ, and a demo-request form)

The two pages cross-link: the portfolio's VetriX•IQ section links out to the landing page, and the landing page links back to the portfolio.

## Live site

Deployed automatically from this repository:
- **Vercel** — connected via the Vercel GitHub integration; every push to `main` triggers a production deployment, and every pull request gets its own preview URL (see the Vercel bot comment on the PR for the exact link).
- **GitHub Pages** — the site can also be served directly from this repo if Pages is enabled (Settings → Pages → deploy from `main`).

> `robots.txt`, `sitemap.xml`, and the `<meta property="og:url">` / `<link rel="canonical">` tags in both `index.html` and `vetrix-iq.html` currently point at a GitHub Pages URL (`https://adelalwali0-hub.github.io/adel-portfolio/`). If you serve the site from a different domain (e.g. a Vercel production domain or a custom domain), update those in both files to match.

## Features

- **Dual-identity storytelling** — a single narrative bridging industrial inspection (QA/QC, NDT) and software engineering, with dedicated About, Experience, Credentials, Services and Contact sections
- **VetriX•IQ landing page** (`vetrix-iq.html`) — a full SaaS marketing page for the product: hero, problem statement, solution (the four platform modules), features, illustrative product-preview mockups, benefits, an FAQ accordion, and a demo-request form
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

There is no `package.json`, no `node_modules`, and nothing to run `npm install` against — the entire dependency surface is the two Google Fonts `<link>` tags in `<head>` of each page.

The demo-request form on `vetrix-iq.html` has no backend: submitting it builds a prefilled `mailto:` link from the field values (name, work email, company, role, interest, message) and opens the visitor's email client. With JavaScript disabled, the form's native `mailto:` action is used instead, which degrades acceptably in most desktop mail clients.

## Project structure

```
.
├── index.html           # the personal portfolio: markup, CSS, and JS in one file
├── vetrix-iq.html        # VetriX•IQ SaaS landing page: markup, CSS, and JS in one file
├── Adel_K_Wali_CV.pdf    # downloadable CV, linked from the hero and contact sections
├── robots.txt            # crawler rules + sitemap pointer
├── sitemap.xml            # sitemap listing both pages
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

**Any other static host** (Netlify, Cloudflare Pages, S3, etc.) — upload the files (`index.html`, `vetrix-iq.html`, `Adel_K_Wali_CV.pdf`, `robots.txt`, `sitemap.xml`) as-is; there is no build step to configure.

## License

All content (copy, résumé, and design) is © Adel K. Wali. No open-source license is granted for reuse of the personal content; the code structure may be used as a reference.
