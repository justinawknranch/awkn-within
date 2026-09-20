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
.github/workflows/      GitHub Pages deployment
```

## Working on it locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Open it once in a light-themed browser and once in a dark-themed one — the page
carries both palettes and follows the visitor's system setting.

## Deployment

Pushing to `main` builds and publishes the site through the
`Deploy to GitHub Pages` workflow. This requires **Settings → Pages → Build and
deployment → Source: GitHub Actions** to be selected once for the repository.

The `CNAME` file binds the site to `awknwithin.org`, which needs these DNS
records at the domain registrar:

| Type  | Name  | Value                                                      |
|-------|-------|------------------------------------------------------------|
| A     | `@`   | `185.199.108.153` `185.199.109.153` `185.199.110.153` `185.199.111.153` |
| CNAME | `www` | `justinawknranch.github.io`                                  |

Once DNS resolves, tick **Enforce HTTPS** in Settings → Pages.

## Editing the copy

All wording lives in `index.html`. The page's language is intentionally careful:
AWKN Within is described as a church and spiritual community, never as a
clinic or a provider of medical, psychiatric, or therapeutic services. Keep new
copy inside those bounds, and keep the disclaimer in the footer intact.
