# Duotone Collective — Intro

A minimal static page that embeds the Figma prototype fullscreen.

Live: https://intro.duotone.design

## Files

- `index.html` — page markup with the Figma prototype iframe
- `styles.css` — full-viewport, no-scroll, responsive iframe styling
- `.gitignore`

No build step. No dependencies. No JavaScript.

## Preview locally

Open the folder with any static server, for example:

```bash
python3 -m http.server 8000
```

Then visit http://localhost:8000

## Deploy to Vercel

1. Install the Vercel CLI (optional): `npm i -g vercel`
2. From this folder:

```bash
vercel        # preview deploy
vercel --prod # production deploy
```

Or import the folder as a new project from the Vercel dashboard
(“Add New → Project → import this folder’s Git repo”, or drag the folder
into a Git repo first). Framework preset: **Other**.

## Add the custom domain `intro.duotone.design`

1. In the Vercel dashboard open the project → **Settings → Domains**.
2. Add `intro.duotone.design` and save. Vercel shows the DNS record to
   create (a `CNAME` pointing to `cname.vercel-dns.com`, or an `A` record
   to `76.76.21.21`).
3. Keep the address-bar domain visible: for a subdomain, Vercel proxies
   the iframe under your own URL with a default SSL certificate.

## Porkbun DNS record

After Vercel shows the required target, create the record in the
`duotone.design` zone at Porkbun → **Domain Management → DNS**:

- **Type:** `CNAME`
- **Host / Name:** `intro`
- **Answer / Target:** the value Vercel provided (`cname.vercel-dns.com`)
- **TTL:** default

(If Vercel requests an `A` record instead, use Type `A`, Host `intro`,
Answer `76.76.21.21`.)

Propagation usually completes within a few minutes; Vercel issues the SSL
certificate automatically once the record resolves.