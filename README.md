# LENSORA

Bilingual Arabic/English creative portfolio platform for photographers, videographers, editors, and visual designers.

## Live application

The fully functional application remains hosted on Cloudflare Workers:
https://lensora-platform.m7njordan.workers.dev

## Repository layout

- `index.html` — GitHub Pages entry page linking visitors to the live application.
- `worker.js` — source mirror of the Cloudflare Worker application and API.
- `.nojekyll` — disables the default Jekyll processing for this static publishing repository.

## Important architecture note

GitHub Pages serves static files only. It does not execute the Cloudflare Worker, access its D1 database, or serve R2 media. Authentication, profiles, uploads, and API routes therefore continue to run on the existing Cloudflare Worker origin. The Pages entry page directs visitors to that live application rather than pretending the backend has moved.

## Cloudflare infrastructure

- Runtime: Cloudflare Workers
- Database: Cloudflare D1
- Media: Cloudflare R2

Do not publish secrets, passwords, session keys, or private environment variables in this repository.
