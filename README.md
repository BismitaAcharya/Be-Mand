# Ventures Upgrade — Publishing Consultancy Website

A 14-page static website for **Ventures Upgrade** (working name), positioned as *India's first AI-integrated publishing, author growth & publishing venture consultancy*.

Plain HTML/CSS/JS. No framework, no build step, no dependencies — open it locally or deploy it as-is.

---

## Pages

| File | Page |
|---|---|
| `index.html` | Home |
| `about.html` | About Us |
| `services.html` | Services overview |
| `author-branding.html` | Author Branding (service detail) |
| `ai-publishing.html` | AI Publishing (service detail) |
| `educational-publishing.html` | Educational Publishing (service detail) |
| `publishing-venture-consultancy.html` | Publishing Venture Consultancy (service detail) |
| `process.html` | Our Process |
| `pricing.html` | Pricing |
| `portfolio.html` | Portfolio |
| `testimonials.html` | Success Stories |
| `blog.html` | Blog |
| `faq.html` | FAQs |
| `contact.html` | Contact |

## Folder structure

```
.
├── index.html
├── about.html
├── services.html
├── author-branding.html
├── ai-publishing.html
├── educational-publishing.html
├── publishing-venture-consultancy.html
├── process.html
├── pricing.html
├── portfolio.html
├── testimonials.html
├── blog.html
├── faq.html
├── contact.html
├── assets/
│   ├── style.css        # design system: tokens, layout, components
│   └── script.js        # nav, scroll reveal, FAQ accordion, stat counters, demo forms
├── source/               # optional — how the HTML was generated
│   ├── components.py     # shared head/nav/footer + SVG helpers
│   └── build.py          # assembles all 14 pages from components
├── .gitignore
└── README.md
```

All internal links and asset paths are relative, so the site works from any folder depth — no path rewriting needed for GitHub Pages, Netlify, Vercel, or a plain web server.

---

## Design system

- **Palette** — midnight blue, charcoal, and white as the base, with electric blue, violet, and gold as accent colors. Defined as CSS custom properties at the top of `assets/style.css`.
- **Type** — Sora for display/headings, Inter for body text, Outfit for nav and labels. Loaded via Google Fonts.
- **Signature motif** — the "manuscript constellation": small document nodes linked like a neural network, used in the hero and dark sections. Inline SVG, styled under `.constellation` in `style.css`.
- Responsive down to mobile (nav collapses into a slide-in drawer under 980px), visible focus states, and `prefers-reduced-motion` is respected throughout.

## Behavior — `assets/script.js`

- Sticky nav that condenses and blurs on scroll
- Mobile nav drawer toggle
- Scroll-triggered reveal animation, via `IntersectionObserver` (degrades gracefully without it)
- Animated stat counters on the Home and About pages
- FAQ accordion
- Contact form and newsletter signup are **front-end demos** — they show a confirmation state on submit but don't send data anywhere yet. Wire them up before launch (see below).

---

## Running locally

No install required.

```bash
# open directly
open index.html          # macOS
start index.html         # Windows

# or serve locally (avoids any relative-path quirks)
python3 -m http.server 8000
# then visit http://localhost:8000
```

---

## Deploying

**GitHub Pages**
1. Push this repo to GitHub.
2. Repo Settings → Pages → Source: select the `main` branch, root folder.
3. Site publishes at `https://<username>.github.io/<repo>/`.

**Netlify / Vercel**
Drag-and-drop the folder, or connect the repo — no build command needed, publish directory is the repo root.

**Wix**
This was also prototyped in Wix. If you want the Wix version kept in sync with this HTML source, just say so and it can be re-imported/rebuilt there.

---

## Regenerating pages from source (optional)

`source/` holds the Python scripts that generated the HTML. Useful if you want a sitewide change — like updating the phone number in the footer — applied everywhere at once instead of hand-editing all 14 files.

```bash
cd source
python3 build.py   # writes the 14 HTML files into the repo root, overwriting them
```

Requires Python 3 only, no external packages. This is optional tooling — the site itself doesn't need it to run.

---

## Before this goes live — replace placeholder content

This build focused on structure, design system, and copy *shape*. The following need real content before launch:

- **Brand name** — "Ventures Upgrade" is a placeholder per the original brief. Once the final name is locked, replace it in the `<title>` tags, nav logo, and footer across all 14 files (or update `source/components.py` and rerun the build).
- **Pricing** (`pricing.html`) — figures are illustrative starting points, not confirmed rates.
- **Testimonials** (`testimonials.html`) — names, roles, and quotes are placeholders.
- **Portfolio** (`portfolio.html`) — tiles use abstract gradient placeholders instead of real covers or screenshots.
- **Blog posts** (`blog.html`) — titles and excerpts are placeholders, not published articles.
- **Contact details** (`contact.html` and the footer on every page) — phone, email, and WhatsApp link are placeholders (`+91 99999 99999`, `hello@venturesupgrade.com`).
- **Forms** — wire the contact form and newsletter signup to a real endpoint (Formspree, a serverless function, your CRM, etc.).
- **Social links** — footer LinkedIn/Instagram/YouTube icons currently point to `#`.

---

## Notes

- No fabricated trust signals or claims of government affiliation appear anywhere in the copy, per the original brief.
- No npm packages or build tooling required — nothing to install before you can preview or edit the site.

© 2026 Ventures Upgrade Publishing Consultancy. All rights reserved.
