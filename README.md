# Ebola Order Tracker

Live: https://ebola-prep.vercel.app

Static site. No build step. Vercel redeploys on every push to `main`.

## Files
- `index.html` – dashboard (same as `Ebola Order Tracker v2.dc.html`)
- `BeneficiaryRisk.dc.html` – Beneficiaries & risk tab
- `support.js` – runtime
- `data/orders.json` – order lines from the weekly OSL export (data (3).xlsx)
- `data/impact.json` – ETC calculator rates and impact lines for Beneficiaries & risk
- `vercel.json` – no-cache headers for `data/` and pages

## Tabs
Overview · Country brief · Line details · Shipment info · Procurement · Critical items · Back orders · Beneficiaries & risk · Glossary

## Data rules
- Values are shown as recorded. Empty fields a source normally fills show “not available”.
- Values that cannot be valid for their column (e.g. `12/31/1899` in Transporter / AWB) show “Inconsistent (recorded as …)” and are excluded from calculations. Glossary → “Inconsistent values in the export” lists them, with a CSV for data cleaning.
- Requested / ordered = sum of request lines in the export; the original requested quantity is not in the export.
- Pipeline has no ETAs in the export; Beneficiaries “Delivered + pipeline” counts it from the start date.

## Weekly update
1. Regenerate `data/orders.json` (and `data/impact.json` if Beneficiaries inputs changed) from the new export, same structure.
2. Replace the files in the repo and push to `main`.
3. Vercel redeploys in about a minute; a normal reload shows the new data.

If the dashboard layout changes, replace `index.html`, `Ebola Order Tracker v2.dc.html` and `BeneficiaryRisk.dc.html`.
