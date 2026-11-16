# LENSORA

The complete LENSORA browser interface is published on GitHub Pages:

https://lensora-1.github.io

## Application architecture

- GitHub Pages serves the static LENSORA interface.
- The existing Cloudflare Worker remains the API runtime.
- Cloudflare D1 remains the account/profile database.
- Cloudflare R2 remains the portfolio media store.

The frontend sends API and media requests to the Cloudflare Worker. GitHub Pages cannot run Worker code or host D1/R2 bindings.

## Important deployment note

Cross-origin authentication from a `github.io` page to a `workers.dev` API requires exact-origin CORS and credential configuration. Browser third-party-cookie restrictions may still prevent reliable persistent login on some devices. Do not assume registration, login, profile editing, or uploads are production-ready on the GitHub Pages hostname until these flows have been tested in real browsers.

## Files

- `index.html` — complete LENSORA frontend.
- `404.html` — fallback for direct profile and nested app routes on GitHub Pages.
- `worker.js` — source mirror of the Cloudflare Worker.
- `.nojekyll` — disables Jekyll processing.

Never commit Cloudflare secrets, passwords, session keys, or private environment variables to this repository.
