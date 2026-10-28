# PushToMainDev.github.io

The Push To Main Dev home page and project pages, served by GitHub Pages at
https://pushtomain.dev. Plain HTML and CSS, no build step.

| Path | What it is |
|---|---|
| `index.html` | Home: projects and about |
| `kinkitchen/` | Kin Kitchen product page, and the "get the app" page for shared links |
| `404.html` | Not-found page; also redirects old-style Kin Kitchen links |
| `.well-known/apple-app-site-association` | Lets `pushtomain.dev/kinkitchen/...` links open in the iOS app |
| `.nojekyll` | Stops Jekyll from hiding `.well-known` |

The dev blog lives in its own repo and is served at `/development-blog/`.

## Preview locally

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Custom domain

The domain is `pushtomain.dev` (set in Settings → Pages, saved in `CNAME`).
Keep **Enforce HTTPS** on.

## Kin Kitchen shared links

Links look like `https://pushtomain.dev/kinkitchen/?recipe=<id>` (also
`?post=` and `?chef=`). With the app installed, iOS opens them in the app.
Without it, `kinkitchen/index.html` shows the "get the app" page instead of
the product page. Old `/kinkitchen/recipe/<id>` links redirect to the new
form from `404.html`.

The App Store number is in `kinkitchen/app-store.js` and in the
`apple-itunes-app` meta tag in `kinkitchen/index.html`. Change both if it
ever changes.

`.well-known/apple-app-site-association` comes from the KinKitchen repo
(`web/pushtomain-dev/`). Copy it over when the app's link setup changes, but
not that folder's `kinkitchen/index.html`: this site's version already does
the same job and is also the product page.

Check the association file after deploying:
https://app-site-association.cdn-apple.com/a/v1/pushtomain.dev
