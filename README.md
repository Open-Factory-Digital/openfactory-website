# openfactory.digital

Static OpenFactory website. No framework, dependencies or build step.

## Structure

- `index.html`: product overview, documented measurements and official implementation partners.
- `how-it-works.html`: technical details and operating boundaries.
- `assets/css/style.css`: existing shared design system.
- `assets/css/refresh.css`: homepage presentation, responsive layout and partner section.
- `assets/logos/`, `assets/favicons/`: OpenFactory identity.
- `assets/partners/`: partner logo and world map; see its README for source attribution.
- `assets/videos/`: existing walkthrough and poster. Playback is user controlled.

## Local preview

```bash
python3 -m http.server 8010 --bind 127.0.0.1
```

Open http://127.0.0.1:8010/ or http://127.0.0.1:8010/#partners.
Use a local server because this site uses root-relative asset URLs.

## Review and rollback

Local baseline tag: `before-partner-refresh-2026-09-27`.
It captures the complete tracked state before this refresh, including the existing
uncommitted corrections to the GitHub repository links. The snapshot commit is
reachable through the tag; the current branch was not moved to create it.

The refresh and tag have not been pushed. After approval, include the new assets
and stylesheet in the publication commit and push the tag as well.

To restore the baseline after publication, from a clean worktree:

```bash
git restore --source=before-partner-refresh-2026-09-27 --staged --worktree -- .
git commit -m "Restore website before partner refresh"
```

That creates a rollback commit without rewriting history. Publish that commit
through the normal deployment process.

## Content sources

The homepage benchmark uses `openfactory-core/docs/knowledge-layer.md`, section
“What it measured (scan of 2026-09-01)”: medians from 8 tickets per arm on one
production codebase. The unchanged wall-clock result and sample limits remain
visible alongside token, turn and cost changes.

CastelloSoft (Brazil) and Altiva Soluções (Portugal) are independent official
implementation partners. OpenFactory remains Apache-2.0; hiring a partner is optional.

## Publishing

Static hosting such as GitHub Pages can serve this directory directly.
`CNAME` sets the custom domain to `openfactory.digital`.

## License

Apache-2.0, matching the platform it documents. Partner trademarks belong to their
respective owners.
