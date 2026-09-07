# todo-dodo-app

The Todo-Dodo web app — **release build**.

**https://app.todo-dodo.com**

A single self-contained HTML file: no server, no account, no build step. Data
lives in the browser's storage on the machine that loaded it.

## Why this is its own repository

Browser storage is scoped by **origin** — scheme, host and port — never by path.
Two builds served from one host share one storage area, and the newer one
migrates the older one's database and then deletes the source. That is correct
on a real upgrade and destructive between channels, so each build gets its own
hostname:

| Build | Host |
|---|---|
| release | https://app.todo-dodo.com |
| development | https://alpha.app.todo-dodo.com |

They cannot see or damage each other's data.

## Layout

```
index.html   the app, self-contained
favicon-32.png, favicon.svg, apple-touch-icon.png, todo-dodo-icon-128.png
             the icons index.html and manifest.json reference
manifest.json  PWA manifest — absolute paths, so this app must be served at a domain ROOT
CNAME        the custom domain GitHub Pages serves this on
.nojekyll    serve paths verbatim; skip the Jekyll build
```

This repository holds a **built artifact**, not source. It is replaced wholesale
on each publish; do not edit `index.html` by hand.

Nothing here links to the app's source repository, which is private.

Currently published: `v0.12.0`
