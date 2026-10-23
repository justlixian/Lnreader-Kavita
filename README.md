# Kavita Plugin for LNReader (Testing Repo)

This repository only serves as a test source for installing the Kavita plugin in LNReader.

The actual plugin code and development happen here:
https://github.com/dom-53/lnreader-plugins/blob/plugin/kavita/plugins/multi/kavita.ts

## How to install in LNReader

1. Add this URL to your plugin sources:

```
https://raw.githubusercontent.com/justlixian/Lnreader-Kavita/refs/heads/main/plugins.min.json
```

2. In Browse settings, make sure to enable the language  `multi`, otherwise the Kavita plugin will not appear.

Feel free to report bugs or request features in the main repo.

# ⚠️ Disclaimer ⚠️

This is a testing repository. It’s recommended to back up your LNReader data before using it, just to be safe. You never know.

Feel free to report bugs or request features in the main repo.

# Changelog

## v0.0.13

- Faster first load of the browse list: filter options (tags, genres, libraries, collections, presets) are now fetched in parallel and in the background instead of six sequential requests blocking the first page. Duplicate concurrent loads are merged.

## v0.0.12

- Novel summaries no longer show raw HTML tags (`<p>`, `<br>`, entities are cleaned).

## v0.0.11

- Chapters now follow the EPUB table of contents (one LNReader chapter per book chapter) instead of one chapter per page. A chapter loads all of its pages in one go.
- EPUBs with no table of contents become a single chapter. Old per-page chapter paths still open.

## v0.0.10

- Much faster novel page loading: per-file book info and table of contents are now fetched in parallel (8 at a time) instead of one after another.

## v0.0.9

- Fixed server URL and API key arriving as `undefined`: settings were read once when the plugin loaded, so values saved later were never seen. They are now read on every request.
- Server URL is normalised (trailing slash removed, `https://` added if missing, a pasted `/api/opds/...` link is trimmed to the base URL).
- API key field also accepts a pasted OPDS URL; the key is extracted from it.
- Clear error message when URL or API key is not set, instead of a malformed `undefined/...` request.
- Auth token is refreshed after 10 minutes or when URL/API key change.
- Auth token is no longer written to the log.
- Filter loading failures no longer cause unhandled promise rejections; fixed "Tagy" label typo.

## v0.0.8 - 2025-11-20

- Added support for loading and applying Kavita’s preset filters (decoded and sent as-is, bypassing manual inputs).
- Introduced sortable results with selectable sort field and direction.
- Added a limit filter to cap returned items (0 leaves results unbounded).
- Added a three-state “Want to read” filter (any / must be marked / must not be marked).
- Added include/exclude filtering by collections (CollectionTags)
- Reordered filter UI for clearer flow

## v0.0.7 - 2025-11-19

- Fixed title search to correctly respect plugin format settings during queries

## v0.0.5 - 2025-11-19

- Fix duplicate results when searching novels by name
