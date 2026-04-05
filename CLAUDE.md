# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What's here

A multi-page personal website for Kyle Whittle — life coach. Pure HTML/CSS, no build step.

| File | Purpose |
|---|---|
| `index.html` | Homepage — hero, what-is-coaching, who I work with, Stoicism framework, FAQ |
| `about.html` | About page — personal story, values |
| `services.html` | Services/offerings page |
| `contact.html` | Contact page with inquiry form |

## Running

All files are zero-dependency, no-build HTML. Open directly in a browser:

```
open index.html
open about.html
open services.html
open contact.html
```

## Conventions

- **No frameworks, no build step** — pure HTML + CSS + vanilla JS only
- **Single-file pages** — each page is a self-contained `.html` file
- **No external CDN links or network dependencies** — everything must work fully offline
- **CSS variables** defined at `:root` for all colors/radii; use them rather than hardcoding values

## Site-wide

- Palette: bg `#ffffff`, text `#1a1a1a`, accent `#e85d26` (orange), muted `#666666`, border `#e0e0e0`
- All user-editable content is wrapped in `<!-- EDIT: ... -->` / `<!-- END EDIT -->` HTML comments
- Max-width 680px centered layout
- Shared nav and footer pattern repeated across all pages
- Hero sections use `.tagline` (large, Futura bold) + `.subtitle` (muted gray) on every page

## Page notes

### index.html
- Page journey nav (`.page-journey`) provides anchor links to sections and cross-page links
- FAQ section uses native `<details>`/`<summary>` — no JS required

### about.html
- Hero includes photo (`HS-12.jpeg`) alongside tagline/subtitle
- Sections: personal story, values grid

### contact.html
- Hero uses tagline + subtitle only (no photo/monogram)
- Contains inquiry form
