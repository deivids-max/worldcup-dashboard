# World Cup 2026 Dashboard

A single-file static web app. The entire app lives in `public/index.html` (HTML +
CSS + JS, no build step, no framework, no `package.json`). It pulls live match data
from the openfootball GitHub feed at runtime and falls back to embedded data when
offline. Only the `public/` folder is deployed to the web — everything else in the
repo (this file, `.claude/`, etc.) stays private.

## After making any changes, always run:

```
git add .
git commit -m "brief description of changes"
git push
```

This pushes to GitHub (`origin/master`).

## Deployment (Cloudflare Pages)

The app is hosted on Cloudflare Pages.

- **Project name:** `worldcup-dashboard`
- **Production URL:** https://worldcup-dashboard-2ge.pages.dev/
- **Build command:** none (it's a static site — there is nothing to compile)
- **Build output directory:** `public` (contains only `index.html`)
- **Production branch:** `master`

### How to deploy

Authenticate once per machine (opens a browser, no API token needed):

```
npx wrangler login
```

Then deploy the `public/` folder (NOT `.` — deploying the repo root would publish
`CLAUDE.md`, `.claude/`, and other internals, since `wrangler pages deploy` does not
honor `.gitignore` or `.assetsignore`):

```
npx wrangler pages deploy public --project-name=worldcup-dashboard
```

Each deploy returns a unique preview URL; the production URL above always points at
the latest deployment.

### Notes

- Do **not** put a Cloudflare API token in any committed file or command line. Use
  `wrangler login` instead.
- Keeping the app in `public/` is what keeps non-app files private — only ever add
  files you want publicly served to `public/`.
