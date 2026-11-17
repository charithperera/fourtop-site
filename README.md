# fourtop-site

Marketing, privacy and support pages for the Fourtop iOS app. Plain static HTML and CSS: no framework, no build step, no JavaScript, no third-party requests.

Live at https://fourtop.charithp.com (Cloudflare Pages).

## Files

- `index.html` is the landing page.
- `privacy.html` is served at `/privacy`.
- `support.html` is served at `/support`.
- `styles.css` is shared by all three.
- `fonts/` holds Geist (SIL Open Font Licence, `OFL.txt` beside it), self-hosted so no visitor's request goes to a font service.
- `screenshots/` doesn't exist yet. The release task adds it. `index.html` has a comment saying where the section goes.

Links use clean URLs (`/privacy`, `/support`). Cloudflare Pages serves `privacy.html` at `/privacy` by itself. **Don't add a `_redirects` file**: it causes a redirect loop.

## Preview

```sh
python3 -m http.server 4000
```

Open http://localhost:4000. The plain Python server doesn't do clean URLs, so `/privacy` and `/support` 404 there. Open `/privacy.html` and `/support.html`, or use a server that maps `/x` to `x.html`.

## Deploy (Cloudflare Pages)

1. Push this folder to its own GitHub repo.
2. Create a Pages project from that repo: framework preset None, empty build command, output directory `/`, production branch `main`.
3. Start the first deployment (it doesn't start by itself through the API).
4. Add the custom domain `fourtop.charithp.com`, then add a proxied `CNAME fourtop` to `<project>.pages.dev` on the charithp.com zone, and retry validation.
5. Email Routing: add `fourtop@charithp.com` forwarding to the usual inbox. The support page and footer use it.

After deploy, check that `/`, `/privacy` and `/support` all return 200.

## Design

Mirrors the app's Slab language (root `DESIGN.md` in the app repo): citrus `#FFC72C` as a field (near-black in dark mode), ink and cream surfaces, Geist type with tabular figures, one big number in the hero, soft large corners, no shadows, no green. Light and dark follow `prefers-color-scheme`.
