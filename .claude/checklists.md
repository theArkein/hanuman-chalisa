# Checklists

## Domain Change Checklist

If the site is ever moved to a new domain, update every hardcoded URL (currently `https://thearkein.github.io/hanuman-chalisa/`) in:

**`index.html`**
- `<link rel="canonical" href="...">`
- `<link rel="alternate" hreflang="hi/en/x-default" href="...">`
- `<meta property="og:url" content="...">`
- `<link rel="preload" as="image" href="...">` (if images move to same domain)

**`sitemap.xml`**
- `<loc>...</loc>`
- All three `<xhtml:link href="..."/>` entries

Grep for `thearkein.github.io` across both files to find all occurrences.
