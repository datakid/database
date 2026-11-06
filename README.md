# LX Database

Explorer for sales records that it reads from two remote feeds, Workforce and Student.

## What it does

- Loads both feeds in a background worker and shows progress while rows arrive.
- Filters by source, pharmacy, region, month, method and unit type, and searches across everything, with an exact-match option.
- Groups by source, medication, pharmacy, region, month, unit type or method, and sorts by column.
- Finds duplicate rows and merges them.
- Exports the current view as CSV. Cells that start with `=`, `+`, `-` or `@` are escaped so spreadsheets do not run them as formulas.
- Syncs again every 45 seconds while the tab is visible, when Auto-sync is on.

## What it does not do

- It is read-only. It never writes back to the feeds.
- It keeps no copy of the data. When a feed is unreachable the page shows an error and offers to try again.
- It cannot read local files. The two feed addresses are fixed in `index.html`.
- It stores only the theme (`lx-theme`) and the Auto-sync choice (`lx-auto`) in `localStorage`.

## Network and install

Calls two read endpoints on a Cloudflare Worker and loads Google Fonts. It makes no other requests. Not installable; no service worker.

## Built with

One HTML file, with no build step, no framework and no libraries. A worker thread builds a columnar table in typed arrays.

## Run locally

Serve the folder with any static file server. The page needs a connection to reach its feeds.
