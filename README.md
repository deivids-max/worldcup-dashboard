# FIFA World Cup 2026 Dashboard

A fast, single-file dashboard for the 2026 FIFA World Cup (hosted across the USA,
Canada, and Mexico). Browse the full match schedule, group standings, and the
knockout bracket — with live results, timezone-aware kickoff times, and a clean
Swiss-typographic design.

**Live site:** https://worldcup-dashboard-2ge.pages.dev/

## Features

- **Matches** — the complete 104-match schedule grouped by day, with status badges
  (upcoming, live, full-time) and filters for stage, date, and text search, plus a
  "hide finished" toggle and quick chips (Today, Next 24h, etc.).
- **Spanish-speaking teams** — a focused view of upcoming matches involving
  Spanish-speaking nations.
- **Groups & Standings** — live-computed tables for all 12 groups (points, goal
  difference, goals for, with the top two highlighted as qualifiers).
- **Knockout bracket** — the full bracket from Round of 32 to the Final, with
  placeholder slots ("Winner of match 89") that resolve automatically as results
  come in.
- **Timezone selector** — kickoff times recompute for the timezone you choose.
- **Light / dark theme** — toggle that remembers your preference.
- **Keyboard accessible** — ARIA tablist with arrow-key navigation and focusable
  match rows.

## Data

Match data is fetched live at runtime from the community
[openfootball/worldcup.json](https://github.com/openfootball/worldcup.json) feed
(`2026/worldcup.json`). If the network request fails, the app falls back to a
built-in snapshot bundled in the page, so it always renders something. A small badge
in the UI indicates whether you're seeing live or built-in data.

## Tech

- Plain HTML, CSS, and JavaScript — **no build step, no framework, no dependencies**.
- The entire app is one file: [`public/index.html`](public/index.html).
- Design follows the Swiss / International Typographic Style (grotesk type, strict
  grid, restrained color), built on a small font/spacing design-token system.

## Running locally

Because it's a static file, just open it in a browser:

```
# macOS
open public/index.html

# Windows
start public/index.html
```

Or serve the folder with any static server (recommended, so the live data fetch
works without file:// restrictions):

```
npx serve public
```

## Deployment

The site is hosted on **Cloudflare Pages**. Only the `public/` folder is deployed,
so repository internals stay private.

```
# one-time auth (opens a browser, no API token needed)
npx wrangler login

# deploy
npx wrangler pages deploy public --project-name=worldcup-dashboard
```

See [`CLAUDE.md`](CLAUDE.md) for the full project + deployment notes.

## License

No license specified yet. Add one if you intend to allow reuse.
