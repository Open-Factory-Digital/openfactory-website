# openfactory.digital

Source for the OpenFactory marketing site — static pages, no build step, no framework. One
workflow keeps the installer the site serves equal to the latest release's (below).

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

This repository has no test suite and no CI for its copy, so nothing here can catch a claim that
goes stale. A network-marked check in the **core** suite — which is where the
`test_the_docs_do_not_drift.py` family already lives — is the mechanism for that, and
it is not built yet.

## Structure

```
index.html              the home page
how-it-works.html       the technical page — mechanism, provider axes, limits
partners.html           implementation partners — the partner list, requirements, the
                        evidence-based certification process and the implementation
                        guidelines. The program's rules live on this page; the `certify`
                        command it names is specified in an openfactory-core issue
assets/css/style.css    all styling, both pages
assets/logos/           brand kit — icon, horizontal lockup, negative variants (svg + png)
assets/icons/           provider marks, also inlined as an SVG sprite in each page
assets/favicons/        favicon.ico, 16/32px png, 512px app icon
assets/videos/          the product walkthrough and its poster frame
CNAME                   custom domain for GitHub Pages (openfactory.digital)
robots.txt
install.sh              the installer `curl -fsSL https://openfactory.digital/install.sh | sh` runs —
                        a copy of the latest final release's, kept so by a workflow (below)
.github/workflows/installer.yml   keeps install.sh equal to the latest final release's
```

## install.sh — never edited here

`https://openfactory.digital/install.sh` is the install command the core's README and every release
page print. GitHub Pages cannot redirect a path, so the site serves a **copy** of the installer.

- **The copy is the latest final release's own `install.sh`**, checked against that release's
  `SHA256SUMS`. The `installer` workflow replaces it when it differs, every hour, and by hand after
  a release (Actions → installer → Run workflow).
- **A release candidate never reaches the site.** GitHub's "latest release" is never a pre-release.
  A candidate is installed by naming it: see "Installing a candidate" in the core's
  [`docs/RELEASING.md`](https://github.com/Open-Factory-Digital/openfactory-core/blob/main/docs/RELEASING.md).
- **Never edit `install.sh` here.** A change to the installer is a pull request on the core, and it
  reaches the site with the next final release. The copy committed on 2026-09-04 and never updated
  is why the site served the v0.1.x installer for a month (openfactory-core#531).

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

The walkthrough video ships at `#product` with controls and a poster frame. The
three items below describe product outcomes; they are not mock screenshots.

## License

Apache-2.0, matching the platform it documents. The OpenFactory name and mark follow
the same conformance-gated governance described on the site itself.

## Official implementation partners

The homepage lists CastelloSoft in Brazil and Altiva Soluções in Portugal as independent, optional official implementation partners. OpenFactory stays open source under Apache-2.0. Partner logo and map asset sources are recorded in [assets/partners/README.md](assets/partners/README.md).

The exact site revision before the partner refresh is tagged `before-partner-network-2026-09-27`. The published refresh is tagged `partner-network-preview-2026-09-27-v2`. Undo the published commit without rewriting history with `git revert partner-network-preview-2026-09-27-v2`.
