# openfactory.digital

Source for the OpenFactory marketing site — a single static page, no build step,
no framework. Copy is sourced from the platform's own `docs/site-guide.md`: every
claim on the page carries the command that proves it.

## Structure

```
index.html              the entire page
assets/css/style.css    all styling
assets/logos/           brand kit — icon, horizontal lockup, negative variants (svg + png)
assets/favicons/        favicon.ico, 16/32px png, 512px app icon
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

The `#product` section (`index.html`) reserves a video slot (`.media-video.placeholder`)
and a three-screenshot grid (`.screenshot-grid`) with instructions inline as HTML
comments. Once the walkthrough recording and product screenshots exist, swap the
placeholder `<div>`s for a real `<video>`/embed and `<img>` tags — no other changes
needed.

## License

Apache-2.0, matching the platform it documents. The OpenFactory name and mark follow
the same conformance-gated governance described on the site itself.
