# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What's here

This is a personal Desktop directory, not a software project. It contains a few standalone browser apps:

| File | Purpose |
|---|---|
| `index.html` | Personal website (single-page, pure HTML/CSS) |

## Running

All files are zero-dependency, no-build HTML. Open directly in a browser:

```
open index.html
```

## Conventions

- **No frameworks, no build step** — pure HTML + CSS + vanilla JS only
- **Single-file apps** — each app lives in one `.html` file (or one file per `index.html` directory)
- **No external CDN links or network dependencies** — everything must work fully offline
- **CSS variables** defined at `:root` for all colors/radii; use them rather than hardcoding values
- **localStorage** for any persistence (see name-game)

## index.html (personal website)

- Palette: bg `#ffffff`, text `#1a1a1a`, accent `#e85d26` (orange)
- All user-editable content is wrapped in `<!-- EDIT: ... -->` / `<!-- END EDIT -->` HTML comments to make personalization easy
- Max-width 680px centered layout
