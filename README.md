# Forecasting tools — hub

A single static landing page linking to the live forecasting tools, so they can be
reached from one address instead of five bookmarks.

**Live:** https://joshua-bailey.github.io/dashboards/

## What it links to

| Tool | Link | Notes |
|---|---|---|
| US Forecast Workbook | https://us-forecast-workbook.onrender.com | Render app, shared password |
| US GDP Nowcast | https://joshua-bailey.github.io/gdp-nowcast/ | Pages |
| Nonfarm Payrolls Nowcast | https://joshua-bailey.github.io/nfp-nowcast/ | Pages, tagged **alpha** |
| FX Forecast Dashboard | https://joshua-bailey.github.io/fx-forecast-dashboard/ | Pages |
| US Labour Market Dashboard | https://joshua-bailey.github.io/labour-market-dashboard/ | Pages |

The page holds no data and no credentials, only links. It carries `noindex`, so it
does not turn up in search results.

## Last-updated dates

The four Pages dashboards are served from the same origin as this hub
(`joshua-bailey.github.io`), so the page can issue a same-origin `HEAD` request to each
and read the `Last-Modified` header, which is when GitHub Pages last published that
site. This runs on every page load, so the dates cannot go stale, and it needs no API
key, no rate-limit budget and no build step. `HEAD` means the multi-megabyte dashboard
bodies are never downloaded.

Each card keeps its cadence text ("Updated weekly") in the HTML as a fallback. The
script overwrites it only on a successful lookup, so with JavaScript off, a failed
fetch, or a site moved off this origin, the page degrades to the old wording instead of
showing a blank or a wrong date.

Two limits worth knowing:

- **The workbook has no date.** It is on `onrender.com`, a different origin that sends
  no CORS header, so its headers cannot be read from here. It is a live app that
  recomputes when opened, so it is labelled `Live · recomputes on open` rather than
  given a misleading timestamp.
- **Publish time is not data vintage.** `Last-Modified` is when the site was rebuilt,
  which for these dashboards is normally the same day the data was refreshed, but the
  two are not the same thing. The footer says so, and the authoritative "as of" date is
  inside each tool.

## Editing

`index.html` is the whole site. Edit it, commit, push; Pages redeploys in a minute or
so. Styling matches the shared dashboard palette (warm `#f5f5f1` ground, IBM Plex
Sans/Mono, navy `#003366`, red `#E3120B` tab) so the hub reads as part of the family.

To add a tool, copy one `<a class="card">` block. Add `class="card alpha"` and a
`<span class="tag wip">` for anything not yet validated.

## Source

This repo is the deployed site — there is no separate `.site/` directory, since the
page has no build step.
