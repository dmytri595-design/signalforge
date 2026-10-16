# SignalForge — Webhook Reliability Lab

SignalForge is a local-first testing workbench for teams building webhook consumers and event-driven integrations. It gives developers a repeatable place to exercise retry behavior, rate limits, replay, and HMAC signature handling before production.

## Features
- Local event ledger with search and filters
- Endpoint profiles, retry limits and backoff policies
- Chaos/replay lab for healthy, flaky, 429, 500, timeout and invalid-signature scenarios
- Attempt timelines and persistent experiment history
- Native Web Crypto HMAC-SHA256 signing/verification and timestamp tolerance
- Delivery health dashboard, endpoint comparisons, failure matrix
- Workspace JSON backup/restore, CSV export, Markdown reliability report
- IndexedDB local database with localStorage fallback
- No external API calls, trackers, third-party runtime libraries or credentials

## Run
Open `index.html` in a modern browser or serve this repository as a static site.

## Boundaries
Delivery is simulated; endpoint URLs are labels and are never contacted. Data stays in the browser profile unless exported. This is not a hosted multi-user database or production webhook gateway. Do not use production secrets in the demo.

## Stack
Vanilla HTML/CSS/JavaScript, IndexedDB, localStorage, Web Crypto, Blob/File APIs. No build step.
