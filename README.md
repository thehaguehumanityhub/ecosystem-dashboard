# Ecosystem dashboard

The Hague Humanity Hub's ecosystem dashboard, embedded at
<https://www.humanityhub.org/ecosystem/ecosystem-in-numbers/>.

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
comes near the viewport, so a visitor who reads the first two sectio## Served at

Always from a specific commit, never `@main`:

```
https://cdn.jsdelivr.net/gh/thehaguehumanityhub/ecosystem-dashboard@<commit>/shell.html
```

The WordPress page carries one Shortcoder shortcode that fetches that URL and injects it
inline. It also sets `window.THHH_ECO_BASE` to the same commit folder, and the shell
loads the four modules from there. No iframe: humanityhub.org sends a `frame-src`
allowlist as an HTTP header, and anything framed from outside it renders as a silent
blank box.

## Updating

1. Rebuild in the private working folder (not in this repository) and copy the five
   files here.
2. Commit and push, and note the new commit id.
3. In WordPress, Shortcoder → ecosystem-dashboard, put the new commit id in the `URL`
   line. Save and hard-refresh the page.

A commit URL never changes, so there is nothing to purge. Do not switch back to `@main`:
jsDelivr caches gzip and brotli copies separately, and a purge can leave browsers on a
stale file while command-line checks look fine.

Edit these files by hand only for visible wording, and even then prefer rebuilding: they
are generated, and the GitHub web editor corrupts special characters in JavaScript.

r corrupts special characters in JavaScript.

## Do not add the source data to this repository

Everything here is public. The build folder and the Airtable export stay in the private
working folder. That export carries contact names, related professionals, staff sizes and
membership dates for thousands of organisations, none of which belongs on a public CDN.

What these files do contain is aggregate counts, plus the names and website domains of
the Hub's active members, all of which was already published in the annual report.
