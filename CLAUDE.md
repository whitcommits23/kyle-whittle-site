# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository. **Personal OS** (goals, tasks, `Knowledge/`) lives in `AGENTS.md` — use that for productivity context; use this file for the **static site** only.

## What's here

A multi-page personal website for Kyle Whittle — life coach. Pure HTML/CSS, no build step.

| File | Purpose |
|---|---|
| `docs/index.html` | Homepage — hero, what-is-coaching, who I work with, Stoicism framework, FAQ |
| `docs/about.html` | About page — personal story, values |
| `docs/services.html` | Services/offerings page |
| `docs/contact.html` | Contact page with inquiry form |
| `docs/course.html` | Free 5-part Stoicism mini-course |
| `docs/thankyou.html` | Post-form-submit confirmation page (noindex) |

## Deployment

Site is served as **static files** (e.g. GitHub Pages). `CNAME` maps the custom domain **whittlemethat.com**. No build step or server-side runtime — do not add bundlers or backends unless you deliberately change that setup.

## Running

All files are zero-dependency, no-build HTML. Open directly in a browser:

```
open docs/index.html
open docs/about.html
open docs/services.html
open docs/contact.html
open docs/course.html
open docs/thankyou.html
```

On Windows or Linux, open each file from the file manager or via `file://` in the browser (same idea as `open` on macOS).

## Conventions

- **No frameworks, no build step** — pure HTML + CSS + vanilla JS only
- **Single-file pages** — each page is a self-contained `.html` file
- **No external CDN links or network dependencies** — everything must work fully offline
- **CSS variables** defined at `:root` for all colors/radii; use them rather than hardcoding values

## Site-wide

- **Main column width:** `.content-col` is **680px** on most pages; `services.html` also uses `.content-col-wide` at **900px** for the service cards grid
- **CSS variables** — all 13 vars defined at `:root` on every page:
  - Light palette: `--bg #ffffff`, `--bg-alt #f5f5f5`, `--text #1a1a1a`, `--text-muted #666666`, `--accent #e85d26`, `--accent-hover #cf4f1e`, `--border #e0e0e0`
  - Dark/warm palette: `--bg-dark #0d0d0d`, `--bg-warm #f5f0e8`, `--text-on-dark #e8e0d4`, `--text-muted-on-dark #a09080`, `--border-dark rgba(255,255,255,0.10)`, `--accent-light #f07040`
- **Visual system ("Ordered Courage"):** dark full-viewport hero → alternating warm/dark/white sections → cinematic quote blocks. All pages share this aesthetic.
- **Nav behavior:** starts transparent (readable over dark hero), transitions to `var(--bg-dark)` on scroll via IntersectionObserver watching `#hero`. Nav links are always `color: #ffffff`; hover/active use `var(--accent-light)`.
- **Hero structure:** `<header class="hero" id="hero">` lives *outside* `<main>` so it can span full viewport width. Contains `.hero-eyebrow` (small caps with flanking lines) + `.tagline` / `.hero-tagline` + `.subtitle`.
- **Animations:** `.fade-up` class + IntersectionObserver (threshold 0.12). Applied to all below-fold sections. Respects `prefers-reduced-motion`.
- **Content column pattern:** sections use `<div class="content-col">` inside full-width `<section>` elements rather than constraining `<main>`.
- All user-editable content is wrapped in `<!-- EDIT: ... -->` / `<!-- END EDIT -->` HTML comments
- **Assets:** paths relative to the `docs/` folder (same directory as the HTML files), e.g. `kyle26.jpeg`, `HS-12.jpeg`. **Fonts:** system stack + Futura (no self-hosted font files required)

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
- Hero uses tagline + subtitle only (no photo/monogram); ghost "C" letter watermark
- **Inquiry form** posts to **Formspree** (`action="https://formspree.io/f/mzdknyrj"`); on success redirects to `thankyou.html`

### course.html
- Free 5-part Stoicism mini-course; lesson content sections stay white for readability
- `.lesson-prompt` ("Try This Today") boxes are dark cards (`var(--bg-dark)`) with terracotta left border
- Scroll progress bar at top of page (JS-driven, `var(--accent)` fill)

### thankyou.html
- Noindex confirmation page shown after contact form submission
- Simple: dark hero with checkmark circle + "Message received." tagline, single below-fold section with "Back to Home" CTA
