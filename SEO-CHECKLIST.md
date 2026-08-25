# Findability — what I checked and what to change

Checked on 25 August 2026 by reading the actual source of each page on GitHub.

## The finding

`invisible-railway/index.html` carries this line in its `<head>`:

```html
<meta name="robots" content="noindex">
```

That is why the Texas piece never reached Google. It is a hard instruction: the
page is fetched, then dropped from the index. Nothing else — not a link, not a
sitemap, not Search Console — overrides it. **Delete that one line.**

## The state of the other pages

| Page | robots tag | Indexable |
|---|---|---|
| invisible-railway | `noindex` | **no — remove it** |
| juraplayer | none | yes |
| goms | none | yes |
| jura | none | yes |
| inflight1 | none | yes |
| planner/science.html | none | yes |
| planner/map.html | none | yes |
| FAIplaner | none | yes |
| flyfaster (railway.app) | not checked — different host, no robots.txt there | probably yes |

No robots tag means "index normally". So apart from the Texas piece, nothing was
actively blocked. The pages were simply invisible: no page linked to them, and
Google does not find what nothing points at. The new landing page fixes exactly
that — it is the one page that links to all of them.

## What to upload with the site

Two files in this folder belong in the root repo (`joergkorner.github.io`),
next to `index.html`:

- **`robots.txt`** — allows everything and names the sitemap. A robots.txt at the
  root of `joergkorner.github.io` applies to *all* your project pages on that
  host, so one file covers everything.
- **`sitemap.xml`** — lists all nine pages. flyfaster is not in it: a sitemap may
  only list URLs on its own host, and flyfaster lives on railway.app.

## After the domain is live

Three search-and-replaces, all `joergkorner.github.io` → `joerxc.org`:

1. `robots.txt` — the `Sitemap:` line
2. `sitemap.xml` — every `<loc>`
3. `index.html` — `og:url` and `og:image`, and uncomment the `<link rel="canonical">`

## Optional, if you want it to happen this month rather than eventually

Register `joerxc.org` in [Google Search Console](https://search.google.com/search-console),
submit `sitemap.xml`, and use "URL inspection → Request indexing" for the Texas
piece. Without that, a new site typically takes weeks. With it, days.

## A decision for you

The two dropped attempts (FAIplaner, planner) are currently indexable, and the
sitemap includes them. That is defensible — they are the record of the work. If
you would rather they not turn up in search results while the third attempt is
the live one, add `<meta name="robots" content="noindex">` to those pages and
delete their three lines from `sitemap.xml`. They stay linked from the landing
page either way.

Note on FAIplaner: its page currently shows a flight profile from 2026-07-30,
titled "FAI-Dreiecke Flug 2026-07-30-XCT-PAE-01" — not the hotspot/Dijkstra
planner the landing page describes. Worth a look before you send crawlers at it.
