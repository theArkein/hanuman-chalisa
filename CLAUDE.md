# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

A clean, devotional single-page website for reading the Hanuman Chalisa (40 chaupais + dohas) by Goswami Tulsidas, with per-line meanings, language toggle, and flexible font sizing.

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
  - Opening dohas (with per-line meanings + overall meaning toggle)
  - Chaupais 1–20 (`#c1`) → image card (`data-slot="2"`) → chaupais 21–35 (`#c2`) → circle image (`data-slot="3"`) → chaupais 36–40 (`#c3`)
  - Closing doha (with per-line meanings + overall meaning toggle) + footer
- Fixed overlays: progress bar (`#prog`), settings widget (`#scroller`)

**JavaScript:**
- **Image loader** — tries `.png/.jpg/.jpeg/.webp` per slot (3 Imgur images); first successful load wins and sets all `[data-slot]` elements
- **Chaupais array** (`ch[]`) — all 40 verses; `render(array, containerId, startNum)` injects `.ch` cards into `#c1/c2/c3` at page load, reading meanings from `chm[]`
- **Meanings array** (`chm[]`) — 40 entries, each with `hi1/en1` (line 1) and `hi2/en2` (line 2) meanings for the corresponding chaupai
- **Settings widget** — always-visible play/pause trigger; expands on hover (desktop) or tap (touch) to reveal: speed slider (0.25×–4×), language toggle (हि/EN), font size controls (A−/A+); collapses on mouse-out / outside tap
- **Language toggle** (`setLang(l)`) — shows/hides `.m-hi` / `.m-en` spans site-wide; default is Hindi
- **Font size** (`changeFontSize(dir)`) — steps through 7 sizes via CSS custom properties `--fs-v` and `--fs-meaning` on `:root`
- **Overall meaning toggle** (`toggleMeaning(btn)`) — reveals/hides `.meaning-overall` block below each doha
- **Progress bar** — fixed 2px top bar driven by scroll position
- **Fade-in** — `IntersectionObserver` animates `.ch`, `.doha`, `.img-card`, `.circle-img` into view

**Meaning markup pattern (dohas and chaupais):**
```html
<div class="v-block">
  <div class="v">verse line 1</div>
  <div class="v-meaning">
    <span class="m-hi">Hindi meaning</span>
    <span class="m-en" hidden>English meaning</span>
  </div>
  <div class="v" style="margin-top:6px">verse line 2</div>
  <div class="v-meaning">...</div>
</div>
<div style="text-align:right;margin-top:14px">
  <button class="meaning-btn" onclick="toggleMeaning(this)">॥ overall meaning ॥</button>
</div>
<div class="meaning-overall" style="display:none">
  <span class="m-hi">...</span><span class="m-en" hidden>...</span>
</div>
```

**Design tokens:**
- Background: `#faf6f1` (warm parchment)
- Accent: `#c45e20` (saffron)
- Text: `#3a2e25` (dark brown)
- Fonts: `Tiro Devanagari Hindi` (verse text), `Cormorant Garamond` (labels/UI)
- CSS custom properties: `--fs-v` (verse font size, default 22px), `--fs-meaning` (meaning font size, default 13px)
- Animated blurred orbs + SVG crosshatch pattern as background atmosphere
- Mobile breakpoint at 600px
