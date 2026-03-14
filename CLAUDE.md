# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What's here

This is a personal Desktop directory, not a software project. It contains a few standalone browser apps:

| File | Purpose |
|---|---|
| `index.html` | Personal website (single-page, pure HTML/CSS) |
| `name-game/index.html` | Face-to-name guessing game (HTML/CSS/JS, uses localStorage) |
| `tictactoe.html` | Tic Tac Toe game |

## Running

All files are zero-dependency, no-build HTML. Open directly in a browser:

```
open index.html
open tictactoe.html
open name-game/index.html
```

## Conventions

- **No frameworks, no build step** — pure HTML + CSS + vanilla JS only
- **Single-file apps** — each app lives in one `.html` file (or one file per `index.html` directory)
- **No external CDN links or network dependencies** — everything must work fully offline
- **CSS variables** defined at `:root` for all colors/radii; use them rather than hardcoding values
- **localStorage** for any persistence (see name-game)

## index.html (personal website)

- Palette: bg `#faf7f2`, text `#2c2c2c`, accent `#c8a97e`
- All user-editable content is wrapped in `<!-- EDIT: ... -->` / `<!-- END EDIT -->` HTML comments to make personalization easy
- Max-width 680px centered layout

## name-game/index.html

- Three screens managed by toggling `.active` class: `screen-setup`, `screen-game`, `screen-results`
- Participant data (name + base64 photo) stored in `localStorage` key `namegame_participants`
- Photos are read via `FileReader` → base64 data URLs; no server upload
- Game picks up to 10 random rounds from the roster; 4 multiple-choice options per round
