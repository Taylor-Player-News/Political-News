# The Record

A primary-source political reader, published to GitHub Pages by the
[Political News App automation](https://cursor.com/automations/22d674dd-afe9-11f1-bf4b-42ffb4d10ea7).

**Live:** https://taylor-player-news.github.io/Political-News/

## Editorial rules

- Every item links the document it came from.
- Claims are tagged `Primary document` or `Reported`. Reporting that goes beyond what a document
  states is labeled and attributed rather than blended into the summary.
- Vote tallies come from the Clerk of the House and the Senate roll call record, not from summaries
  of them.
- Court orders are described by what they actually decide, which is frequently jurisdiction rather
  than the merits.
- No left–right scoring, no bundling of unrelated issues.
- Open questions stay open, each with the specific event that would resolve it.
- No AI-generated imagery. This edition uses no imagery at all.

## Publishing a new edition

The site is plain static files at the repository root, served from `main`.

```bash
git clone "https://x-access-token:${GITHUB_TOKEN}@github.com/Taylor-Player-News/Political-News.git"
cd Political-News
# replace index.html (and any assets) with the new edition
git add -A
git commit -m "The Record — $(date -u +%Y-%m-%d)"
git push origin main
```

Requirements:

- A `GITHUB_TOKEN` Cursor secret with Contents and Pages write access. Tokens pasted into chat are
  refused by design and only last one conversation.
- Relative asset paths, since the site is served from `/Political-News/` and not the domain root.
  For a Vite build, set `base: './'` and publish the contents of `dist/` at the repository root.
- No `CNAME` file, which would break Pages on this repository.
- Bump `CACHE_NAME` in `sw.js` when assets change.
