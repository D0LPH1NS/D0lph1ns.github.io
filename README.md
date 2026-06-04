# StoreSentinel — Controlled Regression Canary Site (V2)

This folder contains **templates** for the **regression** version (V2) of the
controlled canary site. It is meant to be published manually over the existing
V1 site so StoreSentinel can validate a real external **diff** between two scans.

## Differences vs V1 (intentional regressions)

- **Canary Alpha**: price `20.00 → 15.00 CAD`, availability `InStock → OutOfStock`.
- **Canary Beta**: **removed** (no `products/beta.html`). The published repo must
  have `products/beta.html` **deleted**.
- **Canary Gamma**: **added** (`products/gamma.html`), image **alt text omitted**.
- **About page**: meta description **removed**.
- **Home**: links to a non-existent `/pages/missing.html` (a real 404 after publish).

## Important

- Templates contain the `https://d0lph1ns.github.io` placeholder. Do **not** publish this folder
  directly. Use the offline preparation script:

  ```bash
  python scripts/prepare_canary_regression_site.py --base-url https://d0lph1ns.github.io
  ```

  This writes `canary_publish_regression_v2/` (placeholders filled) and a manifest
  `canary_publish_regression_v2_manifest.json`. Templates are never modified.

## Manual publication (human, later — M3B.3B)

1. Run the preparation script with the exact published base URL.
2. Upload the **contents** of `canary_publish_regression_v2/` to the root of the
   `d0lph1ns.github.io` repository (overwriting `index.html`, `products/alpha.html`,
   `pages/about.html`, adding `products/gamma.html`).
3. **Delete** the obsolete `products/beta.html` from the repository (see manifest).
4. Wait for GitHub Pages to rebuild, verify in a private window.

## Hard rules

- No secrets, tokens, credentials, or private data.
- No external resources or trackers.
- GitHub Pages serves published files **publicly**; only fictional content here.
