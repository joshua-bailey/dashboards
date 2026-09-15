# Forecasting tools — hub

A single static landing page linking to the live forecasting tools, so they can be
reached from one address instead of five bookmarks.

**Live:** https://joshua-bailey.github.io/dashboards/

## What it links to

| Tool | Link | Notes |
|---|---|---|
| US Forecast Workbook | https://us-forecast-workbook.onrender.com | Render app, shared password |
| US GDP Nowcast | https://joshua-bailey.github.io/gdp-nowcast/ | Pages, password |
| Nonfarm Payrolls Nowcast | https://joshua-bailey.github.io/nfp-nowcast/ | Pages, password, tagged **alpha** |
| FX Forecast Dashboard | https://joshua-bailey.github.io/fx-forecast-dashboard/ | Pages, password |
| US Weighted Average Tariff Rate | https://joshua-bailey.github.io/watr-dashboard/ | Pages, password |

The four Pages dashboards are encrypted and share one password. The hub itself holds no
data and no credentials, only links, so it is left open. It carries `noindex`, so it
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

A site can be rebuilt with no new content. This happened on 15 Sep 2026, when the
password was added to four dashboards, and to WATR on 8 Sep 2026. Such a card carries
two attributes:

- `data-republished` is the `Last-Modified` value of that rebuild.
- `data-updated` is the time of the last real update before it, taken from the site's
  commit history.

While `Last-Modified` is at or before `data-republished`, the card shows
`data-updated`. The next real deploy moves `Last-Modified` past it, and the live date
takes over with no edit here. If a site is rebuilt again without new content, update
both attributes.

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
