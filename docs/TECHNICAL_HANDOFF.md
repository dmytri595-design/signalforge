# Technical handoff — SignalForge v1.1

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

## Integration seams for a buyer
- Replace simulated receiver with a controlled HTTP test harness behind explicit opt-in
- Add real receiver credentials only in a server-side secret store
- Move workspace and run history to a server database for multi-user use
- Add signed replay authorization, RBAC, and audit retention for hosted use
- Turn structural payload diff into schema-aware validation with JSON Schema and consumer contracts

## Limitations
All deliveries are simulated. Endpoint URLs are labels and are not contacted. Data is browser-local and not shared across users/devices. Idempotency behavior is illustrative and not a production durable store. Contract diff is a heuristic, not a formal compatibility guarantee.
