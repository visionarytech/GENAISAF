# Cookhouse Connect

A mobile-first, fictional cookhouse prototype built with React 19, Vite 7 and Tailwind CSS 4. Olive, white, charcoal and orange styling follows the supplied wireframes, with a desktop sidebar and mobile bottom navigation. All food and camp illustrations are local SVGs; no image services or runtime APIs are used.

## Run locally

Requires Node.js 20.19+ or 22.12+ and npm (validated with Node 24).

```sh
cd /workspace/GENAISAF
npm ci
npm run dev -- --port 5173
```

Open the Vite server on port **5173** in your browser (on the same computer: `http://localhost:5173`). For a remote workspace, use your editor's port-forwarding feature for port 5173. The server listens on all interfaces.

```sh
npm run build     # production files in dist/
npm run preview   # serve the production build on port 4173
npm test          # Chromium interaction tests; dev server must be running
```

Browser tests use `/usr/bin/chromium` by default. Set `CHROMIUM_PATH` to your Chromium executable if needed; set `TEST_URL` to test another server address.

## Explore

- Use the camp selector (location icon on mobile) to search and choose Camp Meranti, Camp Bayu or Camp Tembusu.
- Switch breakfast, lunch and dinner. Browse the sample date range with the arrows. This is a fixed demonstration week starting 3 November 2026; meal examples repeat across dates and camps.
- Vote for a Friday lunch. Each camp has one saved choice per browser; submitting a new choice replaces it. There is no identity verification. The demonstration poll intentionally remains open.
- Rate any meal from 1–5 stars, optionally add a comment and Taste, Portion or Variety tags, and submit feedback.
- Open Dashboard for camp-specific synthetic vote counts, a sample weekly rating trend and sample comments combined with your local entries. Trend bars are static synthetic history; totals and average ratings incorporate your entries.

Data is stored under `cookhouse-connect-v1` in browser localStorage. It persists across refreshes on the same browser and origin. Clearing that key resets your choices and feedback. Storage failures show a message instead of claiming a submission succeeded. Corrupt JSON recovers to the default state.

## Scope

Synthetic data only. No backend, authentication, external database, analytics or connection to real SAF systems. Nutritional values are explicitly illustrative, not dietary advice. Comments remain on the device; use fictional information. Changing browsers or ports does not share data.

## Validation

`npm run build` and `npm test` pass. Browser interaction checks cover 390px mobile and 1440px desktop layouts, camp search/selection, all meal tabs, dates, voting and vote updates, reload persistence, rating/comment submission, dashboard totals, isolation between camps, malformed JSON recovery, horizontal overflow and browser errors.
