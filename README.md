# PushToMainDev.github.io

The Push To Main Dev home page and project pages, served by GitHub Pages at
https://pushtomaindev.com. Plain HTML and CSS, no build step.

| Path | What it is |
|---|---|
| `index.html` | Home: projects and about |
| `kinkitchen/` | Kin Kitchen product page |
| `404.html` | Not-found page, and the "get the app" page for shared Kin Kitchen links |
| `.well-known/apple-app-site-association` | Lets `pushtomaindev.com/kinkitchen/...` links open in the iOS app |
| `.nojekyll` | Stops Jekyll from hiding `.well-known` |

The dev blog lives in its own repo and is served at `/development-blog/`.

## Preview locally

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000. (Shared-link pages only work on GitHub
Pages, which serves `404.html` for unknown paths.)

## Custom domain

1. Repo → Settings → Pages: deploy from `main`, folder `/`.
2. Custom domain: `pushtomaindev.com`. Tick **Enforce HTTPS** once it's offered.
3. At the domain registrar, point `pushtomaindev.com` at GitHub Pages
   (A records `185.199.108.153`, `.109.153`, `.110.153`, `.111.153`) and
   `www` as a CNAME to `pushtomaindev.github.io`.

## Kin Kitchen shared links

Links like `https://pushtomaindev.com/kinkitchen/recipe/<id>` (also `/post/`
and `/chef/`) open in the app when it's installed. GitHub Pages can't
rewrite URLs, so without the app they land on `404.html`, which shows the
Kin Kitchen "get the app" page.

When the app is on the App Store:

1. Put its number in `kinkitchen/app-store.js` (`KK_APP_STORE_ID`).
2. Uncomment the `apple-itunes-app` meta tag in `kinkitchen/index.html`
   and put the same number in it.

Check the association file after deploying:
https://app-site-association.cdn-apple.com/a/v1/pushtomaindev.com
