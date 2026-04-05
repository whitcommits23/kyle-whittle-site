# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository. **Personal OS** (goals, tasks, `Knowledge/`) lives in `AGENTS.md` — use that for productivity context; use this file for the **static site** only.

## What's here

A multi-page personal website for Kyle Whittle — life coach. Pure HTML/CSS, no build step.

| File | Purpose |
|---|---|
| `index.html` | Homepage — hero, what-is-coaching, who I work with, Stoicism framework, FAQ |
| `about.html` | About page — personal story, values |
| `services.html` | Services/offerings page |
| `contact.html` | Contact page with inquiry form |

## Deployment

Site is served as **static files** (e.g. GitHub Pages). `CNAME` maps the custom domain **whittlemethat.com**. No build step or server-side runtime — do not add bundlers or backends unless you deliberately change that setup.

## Running

All files are zero-dependency, no-build HTML. Open directly in a browser:

```
open index.html
open about.html
open services.html
open contact.html
```

On Windows or Linux, open each file from the file manager or via `file://` in the browser (same idea as `open` on macOS).

## Conventions

- **No frameworks, no build step** — pure HTML + CSS + vanilla JS only
- **Single-file pages** — each page is a self-contained `.html` file
- **No external CDN links or network dependencies** — everything must work fully offline
- **CSS variables** defined at `:root` for all colors/radii; use them rather than hardcoding values

## Site-wide

- **Main column width:** `main` is **680px** on `index.html`, `about.html`, and `contact.html`; **900px** on `services.html` for the wider offerings layout
- Palette: bg `#ffffff`, text `#1a1a1a`, accent `#e85d26` (orange), muted `#666666`, border `#e0e0e0`
- All user-editable content is wrapped in `<!-- EDIT: ... -->` / `<!-- END EDIT -->` HTML comments
- Shared nav and footer pattern repeated across all pages
- Hero sections use `.tagline` (large, Futura bold) + `.subtitle` (muted gray) on every page
- **Assets:** reference images and similar files with **paths relative to the repo root** (same folder as the HTML), e.g. `HS-12.jpeg` on about. **Fonts:** system stack + Futura (no self-hosted font files required)

## Page notes

### index.html
- Page journey nav (`.page-journey`) provides anchor links to sections and cross-page links
- FAQ section uses native `<details>`/`<summary>` — no JS required

### about.html
- Hero includes photo (`HS-12.jpeg`) alongside tagline/subtitle
- Sections: personal story, values grid (`.values-grid` uses a wider cap than the main column)

### services.html
- Hero: tagline + subtitle only (no photo)
- **What I Offer** (`#services`): `.services-list` — three offerings (1-on-1, Stoicism programs, workshops)
- **How to Work With Me** (`#process`): numbered `.steps-list` (reach out → discovery call → coaching begins)
- **CTA:** closing section plus fixed **floating button** (`.cta-floating`) linking to `contact.html`

### contact.html
- Hero uses tagline + subtitle only (no photo/monogram)
- **Inquiry form** is **presentational only**: `<form ... onsubmit="return false;">` with no `action`, no backend, and no JS handler — submit does not send data. Do not assume mailto, Netlify forms, or an API unless you wire one up intentionally
