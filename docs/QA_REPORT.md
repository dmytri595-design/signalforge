# QA report — SignalForge v1.2

## Release status
- Source branch: `main`
- Source revision used for the current Vercel deployment: `5bec74779abf5c50eac5fb2522e359434b4bb015`
- Full Playwright/Chromium validation: [GitHub Actions run 39109534074](https://github.com/dmytri595-design/signalforge/actions/runs/39109534074)
- Validation workflow: https://github.com/dmytri595-design/signalforge/actions/workflows/validate.yml
- Vercel deployment state: `READY` (production alias assigned: https://signalforge-brown.vercel.app)
- Hosting mode: static HTML snapshot; automatic GitHub-to-Vercel deployment is not connected, so later repository changes require a manual redeploy.

## Automated validation
- Inline application JavaScript syntax check: passed
- No-network boundary checks: passed
- Dashboard metrics and demo endpoint profiles: passed
- Dashboard health chart: seven daily buckets / 14 outcome bars render, and chart values are visibly rendered for seeded demo activity
- Rate-limit replay: 429 responses, retry backoff, and eventual successful delivery verified
- HMAC generation and verification: valid signature accepted
- Tampered payload: signature mismatch detected
- Idempotency lab: duplicate-delivery suppression and persisted run history verified
- Contract diff lab: breaking structural changes detected and comparison history persisted
- Contract report Markdown download: passed
- Settings navigation, IndexedDB initialization after reload, and JSON workspace backup download: passed
- Browser console/page errors: none reported by the smoke test
- Real Chromium screenshots uploaded as the `signalforge-listing-screenshots` artifact in the linked workflow run

## Bugs discovered and fixed during QA
1. Removed 51 KB of corrupted trailing duplicate source fragments that appeared after the app's real closing script tag; restored a single valid script/body/document close.
2. Restored JavaScript syntax validation and removed the source-code text that had rendered below the UI.
3. Made the dashboard chart use explicit local-day time boundaries and pixel-based bar heights; added regression checks that require visible chart output.
4. Kept the browser smoke suite focused on the major product workflows and persistent state, including replay, signatures, idempotency, contracts, exports, and reload behavior.

## Scope boundaries
All delivery/retry/receiver behavior is simulated. Endpoint URLs are labels and are never contacted. IndexedDB/localStorage are browser-local. HMAC tools are demo utilities and must not be used as a production secret vault. Contract compatibility results are structural heuristics, not a guarantee of semantic compatibility. Vercel reports the deployment as ready, but the current Vercel connector scope did not permit an external page fetch; verify the link in a normal browser before advertising it broadly.


## v1.2 hardening — 2026-10-26

- Resilient IndexedDB/localStorage fallback behavior and an explicit session-only warning when neither persistence path is available.
- Workspace import validation: maximum 10 MB, maximum 5,000 events / 200 endpoint profiles, normalized data shapes and safe record identifiers.
- CSV formula-like string mitigation for exported values.
- HMAC timestamp/header validation and graceful verification errors.
- Scenario-matrix guard when no endpoint profiles exist.
- Expanded Playwright regression coverage for localStorage fallback after reload, formula-like CSV cells, and identifier sanitization during workspace restore.

The automated browser run for this revision is being verified in GitHub Actions before the updated source is manually synced to the Vercel production alias. Until that deployment succeeds, the Vercel alias may continue serving the older snapshot.
