# Evergreen Vehicle Shipping — site

Deploy this repository as a Cloudflare Pages project (no build command, output directory `/`).

- `index.html` — homepage.
- `how-it-works.html`, `services.html`, eight service pages, `car-shipping-cost.html`,
  `car-shipping-preparation.html`, `cross-country-car-shipping.html`, `faq.html`, `contact.html`,
  `vehicle-quote.html`, `privacy-policy.html`, `terms.html`, `404.html`.
  Cloudflare Pages serves each without the `.html` (for example `/faq`), and links are written that way.
- `assets/` — logos, `site.css` (shared styles) and `quote-theme.css` (green theme for the pricing tool).
- Pages with the pricing tool embed it once; only its `PQ_CONFIG` block was edited.
- `functions/api/quote/[[path]].js` — server-side lead proxy for the pricing tool.

## Required: set the lead key in Cloudflare

This repository is public, so the BeRocker Lead Source key is not stored in it.
In Cloudflare → Pages project → Settings → Environment variables, add:

    BEROCKER_LEAD_KEY = <this site's Lead Source key>

Then redeploy. Without it, quotes will not be saved.

## Before launch

- In `PQ_CONFIG` on each page that has the pricing tool, confirm `brandName`, `siteUrl` and `siteLabel`
  (the SMS consent sentence) and that `googleMapsKey` is authorized for this domain.
- Have `privacy-policy.html` and `terms.html` reviewed; they are drafts.
- Add USDOT / MC numbers to the Licensing and insurance section of `faq.html`.
