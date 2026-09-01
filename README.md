# openfactory.digital

Source for the OpenFactory marketing site — two static pages, no build step, no
framework, no CI.

## Where the claims come from

Every factual claim on these pages must be provable from the **public**
[`openfactory-core`](https://github.com/Open-Factory-Digital/openfactory-core) tree.
There are three sources and no others:

| source | what it settles |
|---|---|
| [`docs/STATUS.md`](https://github.com/Open-Factory-Digital/openfactory-core/blob/main/docs/STATUS.md) | every count, the provider-axis table, and what is known broken or incomplete. **The sole home of any number** — this site links to it rather than typing one |
| [`README.md`](https://github.com/Open-Factory-Digital/openfactory-core/blob/main/README.md) | the install command, the shape of the system, the roles |
| the code itself | a registry, a contract default, an ADR — cite the file and the line |

The rule, and it is the whole of it: **a claim is provable from that tree, or it is
removed or narrowed to what is provable.** Never reworded to sound safer while
asserting the same thing. When a claim ships, its source goes in an HTML comment
beside it, so the next editor can re-check it without repeating the search.

> An earlier version of this file said copy was sourced from the platform's
> `docs/site-guide.md`. **That file is not in the public tree and never will be** —
> `docs/STATUS.md:252` lists it as deliberately excluded, and
> `tests/test_the_product_carries_no_ones_past.py:70` records the canonical
> public-claims page moving to `docs/STATUS.md` on 2026-08-26. Anyone sent to
> `site-guide.md` to check a claim would have found nothing to open.

This repository has no test suite and no CI, so nothing here can catch a claim that
goes stale. A network-marked check in the **core** suite — which is where the
`test_the_docs_do_not_drift.py` family already lives — is the mechanism for that, and
it is not built yet.

## Structure

```
index.html              the home page
how-it-works.html       the technical page — mechanism, provider axes, limits
assets/css/style.css    all styling, both pages
assets/logos/           brand kit — icon, horizontal lockup, negative variants (svg + png)
assets/icons/           provider marks, also inlined as an SVG sprite in each page
assets/favicons/        favicon.ico, 16/32px png, 512px app icon
assets/videos/          the product walkthrough and its poster frame
CNAME                   custom domain for GitHub Pages (openfactory.digital)
robots.txt
```

## Preview locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploying

Static files, no build step — works on GitHub Pages, Netlify, Vercel or Cloudflare
Pages unchanged. For GitHub Pages: push to this repo under the
[Open-Factory-Digital](https://github.com/Open-Factory-Digital) org, enable Pages on
the default branch, and point the `openfactory.digital` DNS `A`/`ALIAS` records at
GitHub Pages per [their custom-domain guide](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site) —
the `CNAME` file at the repo root already declares the domain.

## Pending media

The walkthrough video ships: `#product` in `index.html` carries a real `<video>` with
`assets/videos/openfactory.mp4` and a poster frame, and the poster replaces the video
outright below 640px. What is **still** a placeholder is the three-screenshot grid
(`.screenshot-grid`) beneath it — swap those `<div>`s for `<img>` tags once the
screenshots exist; no other change is needed.

## License

Apache-2.0, matching the platform it documents. The OpenFactory name and mark follow
the same conformance-gated governance described on the site itself.
