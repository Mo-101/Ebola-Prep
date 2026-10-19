# Ebola Order Tracker

Live: https://ebola-prep.vercel.app

Static site. No build step. Vercel redeploys on every push to `main`.

## Files
- `index.html` – dashboard (same as `Ebola Order Tracker v2.dc.html`)
- `BeneficiaryRisk.dc.html` – Beneficiaries & risk tab
- `support.js` – runtime
- `data/orders.json` – order lines from the weekly WHO export
- `data/impact.json`, `data/kitdocs.json` – consumption rates and kit references

## Weekly update
1. Regenerate `data/orders.json` from the new export (same structure).
2. Replace the file in the repo and push to `main`.
3. Vercel redeploys in about a minute. `data/` is served with no caching, so a normal page reload shows the new data.

If the dashboard layout changes, replace both `index.html` and `Ebola Order Tracker v2.dc.html`.
