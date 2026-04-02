# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

A clean, devotional single-page website for reading the Hanuman Chalisa (40 chaupais + dohas) by Goswami Tulsidas.

## Development

Pure static site — no build step, no dependencies. Open directly in a browser or serve locally with live reload:

```bash
npx live-server --port=8000
# open http://127.0.0.1:8000
```

## Architecture

Everything lives in `index.html` (HTML + CSS + JS all inline, single file).

**Page structure:**
- Full-bleed hero with background image (`data-slot="1"`)
- `.wrap` — 720px centered column containing:
  - Opening dohas
  - Chaupais 1–20 (`#c1`) → image card (`data-slot="2"`) → chaupais 21–35 (`#c2`) → circle image (`data-slot="3"`) → chaupais 36–40 (`#c3`)
  - Closing doha + footer
- Fixed overlays: progress bar (`#prog`), auto-scroll widget (`#scroller`)

**JavaScript:**
- **Image loader** — tries `.png/.jpg/.jpeg/.webp` per slot (3 Imgur images); first successful load wins and sets all `[data-slot]` elements
- **Chaupais array** (`ch[]`) — all 40 verses; `render(array, containerId, startNum)` injects `.ch` cards into `#c1/c2/c3` at page load
- **Auto-scroll widget** — play/pause + 16-step speed slider (0.25×–4×); shows on scroll/mouse/touch, auto-hides after 3s idle, stops at page bottom
- **Progress bar** — fixed 2px top bar driven by scroll position
- **Fade-in** — `IntersectionObserver` animates `.ch`, `.doha`, `.img-card`, `.circle-img` into view

**Design tokens:**
- Background: `#faf6f1` (warm parchment)
- Accent: `#c45e20` (saffron)
- Text: `#3a2e25` (dark brown)
- Fonts: `Tiro Devanagari Hindi` (verse text), `Cormorant Garamond` (labels/UI)
- Animated blurred orbs + SVG crosshatch pattern as background atmosphere
- Mobile breakpoint at 600px
