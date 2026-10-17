# QA report — SignalForge v1.1

## Release status
- Branch: main
- Release commit: c8f72890559600495b4e0f6b2c36ba702e0f37e8
- Validation workflow: https://github.com/dmytri595-design/signalforge/actions/runs/39018013609
- Result: SUCCESS

## Automated validation
- Inline application JavaScript syntax check: passed
- No-network boundary check: passed
- Playwright Chromium smoke: passed
- Dashboard metrics and demo endpoint profiles: passed
- Rate-limit replay: records 429 retries and successful recovery
- HMAC generation and verification: valid signature accepted
- Tampered payload: signature mismatch detected
- Idempotency lab: repeated deliveries and suppression results rendered and persisted
- Contract diff lab: sample breaking type/removal changes flagged and comparison history persisted
- Contract report Markdown download: passed
- Settings navigation, database status after reload, and JSON workspace backup download: passed
- Browser console/page errors: none reported by the smoke test

## Bugs discovered and fixed during QA
1. Missing central save helper caused actions that called save() to fail at runtime. Added a save() wrapper around IndexedDB/localStorage persistence.
2. Settings navigation was wired only to the first navigation group, making the settings view inaccessible. Bound navigation handling to both nav groups.
3. New experiment-history collections were not initialized after reset/clear. Added safe initial state and schema normalization.
4. Test assertions were expanded to validate new features and settings visibility instead of assuming navigation worked.

## Scope boundaries
All delivery/retry/receiver behavior is simulated. Endpoint URLs are never contacted. IndexedDB/localStorage are browser-local. HMAC tools are demo utilities and must not be used as a production secret vault. Contract compatibility results are structural heuristics, not a guarantee of semantic compatibility.
