# In-Progress Tasks

<!--
## Task Title
**Status:** Pending | In Progress | Waiting | Done

### Steps
- [ ] 1. Step one
  > Note: any relevant detail about this step
- [ ] 2. Step two
  > Note: any relevant detail about this step
-->

---

## Google Search Console — Sitemap Submission
**Status:** Waiting

### Steps
- [x] 1. Add property → URL prefix → `https://thearkein.github.io/hanuman-chalisa/`
  > [search.google.com/search-console](https://search.google.com/search-console)
- [x] 2. Verify ownership via HTML meta tag
  > Tag added to `index.html`, committed and pushed
- [ ] 3. Submit sitemap via Search Console → Sitemaps
  > Use full URL: `https://thearkein.github.io/hanuman-chalisa/sitemap.xml`
  > Previous attempt showed "couldn't fetch" — retry after 24 hours
- [x] 4. Request Indexing via URL Inspection
  > Verify indexing status in 1–2 weeks via URL Inspection tool

---

## Print Stylesheet
**Status:** Pending

### Steps
- [ ] 1. Add `@media print` block to `index.html` CSS
  > Hide: hero, orbs, background pattern, settings widget, progress bar, scroll-hint, intro-text, images, footer decorations
  > Show: verse text + meanings only, clean black-on-white, readable font sizes
- [ ] 2. Test via browser Print Preview (Cmd+P) — check all 40 chaupais + dohas render correctly
- [ ] 3. Verify PDF export looks clean (no cut-off verses, good page breaks)
  > Add `page-break-inside: avoid` on `.ch` and `.doha` blocks

---

## Open Graph Metadata — Verify & Fix Issues
**Status:** Pending

### Steps
- [ ] 1. Go to [opengraph.xyz](https://www.opengraph.xyz)
- [ ] 2. Submit `https://thearkein.github.io/hanuman-chalisa/`
- [ ] 3. Note any issues (missing tags, wrong image dimensions, truncated description, etc.)
- [ ] 4. Fix reported issues in `index.html` and commit + push
