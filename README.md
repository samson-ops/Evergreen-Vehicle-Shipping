# Evergreen Vehicle Shipping — site

Deploy this repository as a Cloudflare Pages project (no build command, output directory `/`).

- `index.html` — homepage with the pricing tool embedded (only its `PQ_CONFIG` block was edited).
- `assets/` — logo files.
- `functions/api/quote/[[path]].js` — server-side lead proxy for the pricing tool.

## Required: set the lead key in Cloudflare

This repository is public, so the BeRocker Lead Source key is not stored in it.
In Cloudflare → Pages project → Settings → Environment variables, add:

    BEROCKER_LEAD_KEY = <this site's Lead Source key>

Then redeploy. Without it, quotes will not be saved.

## Before launch

In `PQ_CONFIG` (near the bottom of the embed in `index.html`) set `phoneDisplay`, `phoneTel`,
`brandName`, `siteUrl` and `siteLabel`, and confirm `googleMapsKey` is authorized for this domain.
Every phone link on the page reads from `PQ_CONFIG`.
