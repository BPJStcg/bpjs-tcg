# BPJS TCG Pro

Professional static storefront designed for GitHub Pages.

## Features
- Responsive professional storefront
- BPJS TCG SVG logo
- Real card photography via Scryfall image URLs in the sample catalog
- Search and category filtering
- Local cart with stock limits
- Shipping method selector and free-shipping threshold setting
- Inventory admin page with add/edit/delete, JSON export/import
- Stripe Payment Link and PayPal Payment Link settings
- Sell-your-cards intake form
- GitHub Pages-ready (`.nojekyll`)

## Important payment architecture
GitHub Pages is static hosting. It cannot safely hold Stripe/PayPal secret keys or provide a server-side order creation endpoint. Stripe Payment Links or PayPal hosted payment links can be used from a static site. For a true dynamic cart checkout that calculates the cart server-side, reserves inventory, captures payment, sends receipts, and handles webhooks, add a small serverless backend.

PayPal's current documentation recommends its JavaScript SDK v6 for new integrations and shows server-side order creation/capture. Stripe Checkout also requires server-side/session creation for a dynamic cart.

## GitHub Pages
1. Create a public GitHub repository, e.g. `bpjs-tcg`.
2. Upload this folder.
3. Settings → Pages → deploy from `main` branch (or GitHub Actions).
4. Your site will be available at `https://YOUR-USERNAME.github.io/bpjs-tcg/`.

GitHub Free supports Pages for public repositories.

## Replace sample products
Edit the product array in `index.html` or use `/admin/` locally. For a production catalog, export the JSON and update the site inventory.

## Payments
- Stripe: create Payment Links in Stripe and paste the URL into admin settings.
- PayPal: use a hosted PayPal payment link or add the PayPal SDK with a secure server endpoint for dynamic orders.
- Do not put PayPal secrets or Stripe secret keys in this repository.

## Shipping
The storefront includes Standard, Express and Priority shipping options and a $100 free-shipping threshold. Adjust those values in the admin page or code to match your actual policy.
