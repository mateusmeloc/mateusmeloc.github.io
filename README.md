# mateusmeloc.github.io

Personal site, published with GitHub Pages at <https://mateusmeloc.github.io/>.

## `/` (root)

`index.html` is the landing page: a single file, in English, with no JavaScript and no
external requests, with light and dark themes. It presents the public projects
(`mcp-erp-server`, `whatsapp-receipts-agent`, the clinic website and the lists app).
To change it, edit the file directly and publish.

## `/listas/`

The **Shopping Lists — Espaço Odontológico** app, used by the clinic's management to build
the monthly list and send it ready-made over WhatsApp. The app's interface is in Portuguese
because it is an internal tool for a Brazilian clinic.

`listas/index.html` is a final, self-contained build: compiled React, CSS, logo and icons
are already embedded in the file. Do not edit it by hand — to update it, replace the whole
file with the new version.

## Why there is an `api/saude` file at the root

The app calls `fetch("/api/saude")` with an absolute path, from the domain root, to find out
whether reading a list from a photo is available. On a Node server that route is dynamic;
here it is a fixed static file:

```json
{"ok":true,"ia":false}
```

With `ia: false` the app hides the photo-reading button, which is the intended behavior —
the feature would need an API key and a server.

**If this file goes missing**, the call returns 404, the app concludes it is running on a
host with a backend and shows the button anyway — which then fails when used. Keep the file
at the root.

`.nojekyll` turns Jekyll off so the extensionless file is served as-is.
