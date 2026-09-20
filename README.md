# awknwithin.org

The website for **AWKN Within** — a spiritual community gathered in ceremony on
ranch land in the Texas Hill Country.

A static, single-page site. No build step, no dependencies: the HTML, CSS and
assets in this repository are what gets served.

## Layout

```
index.html              the site
404.html                not-found page
CNAME                   custom domain (awknwithin.org)
.nojekyll               serve files as-is, no Jekyll processing
robots.txt              crawl rules + sitemap pointer
sitemap.xml             one entry, the homepage
assets/mark.svg         the mark, used as favicon
assets/og.png           1200x630 social preview card
.github/workflows/      publishes main onto the gh-pages branch
```

## Working on it locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Open it once in a light-themed browser and once in a dark-themed one — the page
carries both palettes and follows the visitor's system setting.

## Deployment

GitHub Pages serves the **`gh-pages`** branch of this repository, mapped to
`awknwithin.org` by the `CNAME` file.

Pushing to `main` runs the `Publish site` workflow, which mirrors `main` onto
`gh-pages`; that push in turn triggers GitHub's own *pages build and
deployment*, which serves the files as they are. There is no build step, and
`.nojekyll` keeps Jekyll out of the way.

To publish by hand:

```sh
git push --force origin main:gh-pages
```

Note the workflow does not use `actions/deploy-pages`. The `github-pages`
environment only accepts deployments from whichever branch Pages is configured
to serve, so an Actions-based deploy running on `main` is rejected before its
first step. Mirroring the branch avoids that entirely.

### DNS

`awknwithin.org` needs these records at the registrar:

| Type  | Name  | Value                                                      |
|-------|-------|------------------------------------------------------------|
| A     | `@`   | `185.199.108.153` `185.199.109.153` `185.199.110.153` `185.199.111.153` |
| CNAME | `www` | `justinawknranch.github.io`                                  |

Once DNS resolves, tick **Enforce HTTPS** under Settings → Pages.

## Editing the copy

All wording lives in `index.html`. The page's language is intentionally careful:
AWKN Within is described as a church and spiritual community, never as a
clinic or a provider of medical, psychiatric, or therapeutic services. Keep new
copy inside those bounds, and keep the disclaimer in the footer intact.
