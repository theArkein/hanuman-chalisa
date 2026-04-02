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

## Google Search Console — Sitemap Submission
**Status:** Waiting (sitemap fetch failed; indexing requested directly)

### Steps
- [x] 1. Add property at [search.google.com/search-console](https://search.google.com/search-console) → URL prefix → `https://thearkein.github.io/hanuman-chalisa/`
- [x] 2. Verify ownership via HTML meta tag (tag added to `index.html`, committed and pushed)
- [ ] 3. Submit sitemap → Search Console → Sitemaps → enter full URL:
  ```
  https://thearkein.github.io/hanuman-chalisa/sitemap.xml
  ```
  *(Previous attempt showed "couldn't fetch" — retry after 24 hours)*
- [x] 4. URL Inspection → enter `https://thearkein.github.io/hanuman-chalisa/` → Request Indexing
  *(Requested — verify indexing status in 1–2 weeks via URL Inspection)*

## Open Graph Metadata — Verify & Fix Issues
**Status:** Pending

### Steps
- [ ] 1. Go to [opengraph.xyz](https://www.opengraph.xyz)
- [ ] 2. Submit `https://thearkein.github.io/hanuman-chalisa/`
- [ ] 3. Note any issues reported (missing tags, wrong image dimensions, truncated description, etc.)
- [ ] 4. Fix reported issues in `index.html` and commit + push
