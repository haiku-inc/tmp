# Orca marketing site

A single, self-contained static landing page for **Orca by Haiku** in the haiku-ui design
language. No build step and no framework. It is one `index.html` plus the brand logos in `assets/`.

## Contents

```
marketing/
  index.html          the page (all CSS and JS inline)
  assets/
    logo.png          HAIKU wordmark (footer)
    logo-avatar.png   H monogram (header + favicon)
```

Fonts load from Google Fonts (Rajdhani, Orbitron, Cairo, Inconsolata, Bebas Neue). The contact
form is a HubSpot embed (portal `21161650`, form `96bed20b-78df-4e72-a6bb-9ae2be470b14`, region
`na1`), the same form the admin-panel landing pages use. It renders as raw HTML so the page CSS
styles it to match the brand.

## Preview locally

```bash
cd marketing
python -m http.server 8099
# open http://localhost:8099
```

Any static file server works (`npx serve`, `caddy file-server`, nginx, and so on).

## Deploy

It is a static site, so any static host serves it as is.

- **Netlify or Vercel**: point the project at this `marketing/` directory with no build command and
  a publish directory of `.`.
- **GitHub Pages**: publish this folder (or copy its contents to the Pages branch or `docs/`).
- **S3, Cloudflare Pages, nginx, Caddy**: upload `index.html` and `assets/` and serve the folder.

The HubSpot form loads its script from `js.hsforms.net` at runtime, so the deployed page needs
outbound network access for that request. Everything else is bundled with the page.

## Editing copy

All copy lives directly in `index.html`. House style for this page: no semicolons, no em dashes,
and no "noun, modifier" trailing phrases. Keep sentences plain and declarative.
