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

## Editing

`index.html` is the whole site. Edit it, commit, push; Pages redeploys in a minute or
so. Styling matches the shared dashboard palette (warm `#f5f5f1` ground, IBM Plex
Sans/Mono, navy `#003366`, red `#E3120B` tab) so the hub reads as part of the family.

To add a tool, copy one `<a class="card">` block. Add `class="card alpha"` and a
`<span class="tag wip">` for anything not yet validated.

## Source

This repo is the deployed site — there is no separate `.site/` directory, since the
page has no build step.
