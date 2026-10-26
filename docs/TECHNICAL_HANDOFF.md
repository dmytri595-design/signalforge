# Technical handoff — SignalForge v1.1

## Current hosted demo
- URL: https://signalforge-brown.vercel.app
- Source snapshot: `5bec74779abf5c50eac5fb2522e359434b4bb015`
- Vercel reports the deployment state as `READY`.
- The current deployment was uploaded as a static file snapshot; GitHub automatic redeploy is not connected yet. Connect the Vercel project to this repository before relying on pushes to publish updates.

## Runtime
- Single-page static HTML/CSS/JavaScript app, no build step
- Browser APIs: IndexedDB, localStorage, Web Crypto, Blob/File APIs
- No third-party runtime libraries or external HTTP calls

## Data model
- Workspace: version, settings, endpoints, events, replay experiments, activity
- v1.1 additions: idempotencyRuns and contractRuns
- IndexedDB database: signalforge-local-db, object store workspace, key main
- localStorage mirror/fallback: signalforge:workspace:v1
- JSON workspace backup includes the full workspace state; legacy backups are normalized on restore.

## Functional modules
- Event stream and endpoint profile CRUD
- Deterministic scenario outcomes with recorded retry timeline
- HMAC-SHA256 using Web Crypto over timestamp + '.' + raw body
- Idempotency simulator: key, payload-fingerprint, or no-deduplication policy
- Recursive JSON shape diff: additions, removals, and type changes
- Endpoint and workspace reports in CSV, Markdown and JSON formats

## Reliability safeguards in v1.2
- IndexedDB writes no longer depend on the localStorage mirror succeeding; if IndexedDB transactions fail, persistence degrades to localStorage where available.
- Workspace import is size-bounded and normalizes settings, endpoints, events and history collections before rendering.
- Endpoint/event identifiers are normalized to safe characters before they are used in HTML attributes.
- CSV string cells beginning with formula-triggering characters are prefixed with an apostrophe; numeric values remain numeric text.
- HMAC generation/verification requires a non-empty secret, a positive integer Unix timestamp, a correctly shaped sha256 signature header and a timestamp within the configured tolerance.

## Integration seams for a buyer
- Replace simulated receiver with a controlled HTTP test harness behind explicit opt-in
- Add real receiver credentials only in a server-side secret store
- Move workspace and run history to a server database for multi-user use
- Add signed replay authorization, RBAC, and audit retention for hosted use
- Turn structural payload diff into schema-aware validation with JSON Schema and consumer contracts

## Limitations
All deliveries are simulated. Endpoint URLs are labels and are not contacted. Data is browser-local and not shared across users/devices. Idempotency behavior is illustrative and not a production durable store. Contract diff is a heuristic, not a formal compatibility guarantee.
