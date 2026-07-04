# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project uses [Semantic Versioning](https://semver.org/).

## [1.1.0] — 2026-07-04

### Added

- `vetrix-iq.html` — a dedicated SaaS landing page for VetriX•IQ targeting oil & gas engineering companies: hero, problem statement, solution (the four platform modules), features, illustrative product-preview mockups, benefits, an FAQ accordion, a demo-request form, and a closing contact CTA
- A backend-free demo-request form: submitting it builds a prefilled `mailto:` link from the entered fields (name, work email, company, role, area of interest, message) and opens the visitor's email client; degrades to a native `mailto:` form action if JavaScript is disabled
- Cross-links between the two pages: the portfolio's VetriX•IQ section now links out to `vetrix-iq.html`, and the landing page links back to the portfolio
- A second entry in `sitemap.xml` for the new page
- A **"How It Works"** section on the VetriX•IQ landing page: a four-step numbered workflow (digitize records → assign roles → capture inspections → generate reports) with a connecting timeline line, addressing the migration/adoption question before the pricing/demo ask
- A fourth "Qualification" screenshot mockup, completing visual coverage of all four platform modules
- A compliance/standards badge row (ASME Section IX, ASNT SNT-TC-1A, API Inspection Practices) in the Features section for faster credibility scanning
- A pricing FAQ entry, answered honestly (no public price list yet, scoped on the demo call) rather than left unaddressed
- A persistent mobile call-to-action bar that appears after the hero and automatically hides once the visitor reaches the demo form, so a "Request a Demo" action is always one tap away on mobile without opening the nav menu

### Fixed

- Two inline `style` attributes (a header layout wrapper and a "no border" override) moved into CSS classes

## [1.0.0] — 2026-07-04

First stable release. The site was rebuilt from a single-file design draft into a complete, production-ready portfolio in two passes.

### Added

- **About section** — a bio bridging both careers (industrial inspection and software development), a quick-facts panel, and a two-column skills matrix
- **Services section** — three concrete offerings (QA/QC & NDT inspection, software development, workflow digitization), each with its own call to action
- **Credentials section** — merges what were previously separate Certifications, Training and Awards sections into one
- A **"currently available"** status indicator and a **"Field-proven with"** trust line naming real former employers (South Oil Company, Thi Qar Oil Company, PetroChina Halfaya) in the hero
- A hand-built inline SVG icon set (mail, external link, phone, download, wrench, code, workflow, shield/check) used consistently across contact channels, service cards, VetriX modules, skill headers, and certification cards
- A circular inspection-seal SVG graphic in the hero, replacing a plain bordered text badge
- `Person` JSON-LD structured data, Open Graph and Twitter card meta tags, an inline SVG favicon, `robots.txt`, and `sitemap.xml`
- A skip-to-content link, an accessible mobile navigation menu (hamburger toggle with keyboard/Escape/resize handling), and scroll-spy active-link highlighting
- Scroll-reveal animations, staggered card-grid reveal delays, a count-up animation on the hero stats, and hover/lift micro-interactions on cards — all automatically disabled under `prefers-reduced-motion`
- `README.md` and this `CHANGELOG.md`

### Changed

- Reordered and renumbered all sections (About → Experience → VetriX•IQ → Credentials → Services → Contact) for a clearer narrative flow
- Strengthened the Contact section with a bordered call-to-action banner (Email / WhatsApp) above the existing channel grid
- Styled the header's "Contact" link as a distinct bordered call-to-action pill (desktop nav, mobile dropdown, and active/scroll-spy state) so it stays visible while scrolling
- Tightened the meta description to avoid truncation in search results
- Extracted the CV from an inline base64 string embedded directly in the HTML into a real `Adel_K_Wali_CV.pdf` file, cutting the HTML payload from ~125 KB to ~36 KB; the PDF now downloads only when a visitor clicks it
- Replaced the Blob/`createObjectURL` CV-download script with a plain `href` pointing at the PDF
- Switched font loading to a non-render-blocking `preload` + `onload` pattern with a `<noscript>` fallback

### Fixed

- Mobile navigation was completely inaccessible below 720px (no menu, no way to reach any section) — added an accessible hamburger menu with a no-JavaScript fallback that shows a plain stacked link list
- The sticky header covered the top of each section when jumping via anchor links — fixed with `scroll-margin-top`
- A scroll-reveal implementation could briefly flash above-the-fold content invisible on load — fixed by moving the `no-js`/`js` class swap into `<head>` so it runs before first paint
- An email address wrapped mid-word in the contact grid ("adilkareem.hq@gmail" / ".com") — fixed with a `<wbr>` after the `@`

### Removed

- Dead CSS custom properties left over from an earlier draft
- The last remaining inline `style` attribute (moved into a CSS class)

### Security

- No third-party JavaScript dependencies, analytics, or tracking scripts are loaded; the only external requests are to Google Fonts
- No secrets, tokens, or credentials are present in the repository — contact details (email/phone) are intentionally public
