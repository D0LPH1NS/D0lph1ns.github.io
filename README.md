# StoreSentinel — Controlled External Canary Site

This folder contains **templates** for a small, fictional e-commerce site used as
the first **approved external target** for StoreSentinel after manual publication
to GitHub Pages.

## Purpose

- Provide a real, public URL to validate the StoreSentinel crawler end-to-end
  against a live origin (M3B.2), under controlled conditions.
- Everything here is **fictional and controlled**: no real products, no real
  prices, **no private data**, no secrets, no trackers, no external resources.

## Important

- These are **templates**: pages contain the placeholder `https://d0lph1ns.github.io` in their
  canonical URLs and JSON-LD. Do **not** publish this folder directly.
- Use the offline preparation script to produce a publishable copy:

  ```bash
  python scripts/prepare_canary_site.py --base-url https://USER.github.io/REPO
  ```

  This writes a `canary_publish/` folder with every `https://d0lph1ns.github.io` replaced. The
  templates in `canary_site/` are never modified.

## Manual GitHub Pages publication (done by a human, later)

> No credentials, no `git push`, no `gh`, no network calls are performed by this
> repository. The steps below are **manual** and intentionally not automated.

1. Choose the final URL, e.g. `https://USER.github.io/REPO`.
2. Run the preparation script with that exact `--base-url`.
3. Create a GitHub repository (manually) and enable **Settings → Pages**.
4. Upload the **contents of `canary_publish/`** to the branch/folder GitHub Pages
   serves (e.g. `main` / root, or `docs/`).
5. Wait for Pages to build, then verify the URL loads in a browser.

## Replacing `https://d0lph1ns.github.io`

Every occurrence of `https://d0lph1ns.github.io` must be replaced by the published origin
(scheme + host + optional repo path), **without a trailing slash**. The script
does this for you. Example: `https://d0lph1ns.github.io/products/alpha.html` →
`https://USER.github.io/REPO/products/alpha.html`.

## Expected URL after publication

`https://USER.github.io/REPO/` (exact value depends on your account/repo names).

## Deleting the site after tests

When testing is finished, remove the published site:

- Disable GitHub Pages in **Settings → Pages**, and/or
- Delete the repository (manually).

Locally, simply delete the generated `canary_publish/` folder.

## Hard rules

- **Never** add secrets, tokens, credentials, or private data to this site.
- Remember: GitHub Pages makes published files **publicly accessible**. Only put
  fictional, safe content here.
