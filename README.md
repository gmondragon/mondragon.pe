# mondragon.pe

Terminal-style portfolio for Gabriel Mondragón (Lead DevOps / Cloud Engineer).

Static site — `index.html` + `support.js`, no build step. `support.js` is the
DC runtime (loads React/ReactDOM/Babel from CDN at runtime and renders the
`<x-dc>` template in `index.html`). It's generated from Claude Design's
`dc-runtime` — do not hand-edit; re-export from the source project instead.

## Deploy (GitHub Pages)

1. Push this repo to GitHub.
2. Repo Settings → Pages → Source: **Deploy from a branch** → `main` / `/ (root)`.
3. `CNAME` is already set to `mondragon.pe` — point your DNS:
   - `A` records for the apex (`mondragon.pe`) to GitHub Pages' IPs
     (`185.199.108.153`, `.109.153`, `.110.153`, `.111.153`), or
   - `ALIAS`/`ANAME` to `<username>.github.io` if your DNS provider supports it.
   - Optional `www` → `CNAME` to `<username>.github.io`.
4. Wait for DNS to propagate, then enable **Enforce HTTPS** in the Pages settings.

Drop the `CNAME` file (and skip step 3) to use the default
`<username>.github.io/<repo>` URL instead.
