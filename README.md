# Political-News

Permanent GitHub Pages home for **The Record**, the primary-source political news app built by the
[Political News App automation](https://cursor.com/automations/22d674dd-afe9-11f1-bf4b-42ffb4d10ea7).

**Live URL:** https://taylor-player-news.github.io/Political-News/

## Current state

A placeholder page. The automation has built the app several times but each run built it inside a temporary
machine and never pushed, so nothing was published. This repository exists with Pages enabled so a run only
has to push.

## How a run should publish

Push the built static output to the root of `main`:

```bash
# from the built app directory (e.g. dist/)
git init -b main
git remote add origin "https://x-access-token:${GITHUB_TOKEN}@github.com/Taylor-Player-News/Political-News.git"
git add -A
git commit -m "The Record — $(date -u +%Y-%m-%d)"
git push -f origin main
```

Requirements:

- A `GITHUB_TOKEN` Cursor secret with Contents and Pages write access. Tokens pasted into chat are refused by design.
- Relative asset paths, since the site is served from `/Political-News/` rather than the domain root.
  For Vite, set `base: './'`.
- No `CNAME` file, which would break Pages on this repo.
