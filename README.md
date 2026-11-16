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

## On-site SEO

The terminal is enhanced with a visible, static HTML profile below it. This gives
visitors and crawlers direct access to the professional profile, skills,
certifications, selected work, and contact links without executing JavaScript or
typing commands. Keep this profile and the terminal's English/Spanish `DATA`
content consistent when updating career details.

The page includes a descriptive title and summary, canonical URL, Open Graph and
Twitter metadata, and `ProfilePage` / `Person` JSON-LD. Structured credentials
describe the two certifications already listed in the profile; they do not imply
independent verification or guarantee a rich search result. The document language
tracks the terminal language; the static English profile has its own `lang="en"`.

`robots.txt` permits crawling and points to `sitemap.xml`, which lists the single
public page. Terminal commands such as `/certs` are interactions, not URL routes,
so they are not sitemap entries. The language toggle does not have separate URLs,
so there are no language alternate (`hreflang`) links.

After publishing, verify that `https://mondragon.pe/`, `/robots.txt`, and
`/sitemap.xml` return successfully. Submit the sitemap in Google Search Console
and inspect the homepage's rendered HTML and structured data. If the production
domain changes, update the canonical, social URL, JSON-LD IDs/URLs, robots sitemap
URL, and sitemap location together. Live HTTP status, indexing, and redirects
must be checked against the deployed site.
