# app-docs

Support pages and privacy policies for my iOS apps and Facebook apps, served by GitHub Pages.

Published at **https://akoh17.github.io/app-docs/**

## Layout

One folder per app, each with its own `index.html` (support page) and
`privacy.html`. The root `index.html` links to them all.

```
index.html            hub — links to every app
textgrab/
  index.html          support page  → /app-docs/textgrab/
  privacy.html        privacy policy → /app-docs/textgrab/privacy.html
```

## Pages setup

Settings → Pages → Source: **Deploy from a branch**, branch `main`, folder
`/ (root)`. The repo must be public.

## Adding an app

Create `<appname>/index.html` and `<appname>/privacy.html`, then add a card for
it to the root `index.html`. The App Store Connect URLs for that app are then:

- Support URL: `https://akoh17.github.io/app-docs/<appname>/`
- Privacy Policy URL: `https://akoh17.github.io/app-docs/<appname>/privacy.html`

Both URLs must return 200 before a submission — App Store Connect rejects an
unreachable privacy policy, and a dead support URL is a common review rejection.
Verify with:

```sh
curl -o /dev/null -w "%{http_code}\n" https://akoh17.github.io/app-docs/<appname>/
curl -o /dev/null -w "%{http_code}\n" https://akoh17.github.io/app-docs/<appname>/privacy.html
```
