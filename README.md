# Ecosystem dashboard

The Hague Humanity Hub's ecosystem dashboard, embedded on humanityhub.org.

This repository holds **only the built files that are served to the public**. It is
public because jsDelivr can only serve public repositories.

| File | Role |
|---|---|
| `shell.html` | The Shortcoder payload: headline figures, section navigation, the loader, and Chart.js inlined once |
| `module-orgtypes.html` | Who makes up our community |
| `module-fields.html` | What do they work on |
| `module-map.html` | Where does the ecosystem reach |
| `module-sdg.html` | Which goals does the work serve |

Only `shell.html` is loaded up front. Each module is fetched the first time its section
comes near the viewport, so a visitor who reads the first two sections never downloads
the map or the SDG chart.

## Served at

```
https://cdn.jsdelivr.net/gh/thehaguehumanityhub/ecosystem-dashboard@main/shell.html
```

The WordPress page carries one Shortcoder shortcode that fetches that URL and injects it
inline. No iframe: humanityhub.org sends a `frame-src` allowlist as an HTTP header, and
anything framed from outside it renders as a silent blank box.

## Updating

1. Rebuild in the working folder (not in this repository) and copy the five files here.
2. Commit and push.
3. jsDelivr caches for up to 12 hours. Open the purge link once for each changed file:
   `https://purge.jsdelivr.net/gh/thehaguehumanityhub/ecosystem-dashboard@main/shell.html`
4. Hard-refresh the page.

Edit these files by hand only for visible wording, and even then prefer rebuilding: they
are generated, and the GitHub web editor corrupts special characters in JavaScript.

## Do not add the source data to this repository

Everything here is public. The build folder and the Airtable export stay in the private
working folder. That export carries contact names, related professionals, staff sizes and
membership dates for thousands of organisations, none of which belongs on a public CDN.

What these files do contain is aggregate counts, plus the names and website domains of
the Hub's active members, all of which was already published in the annual report.
