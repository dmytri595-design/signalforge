# QA checklist — SignalForge v1.1

## Persistence and workspace
- [ ] First visit seeds demo workspace
- [ ] Save writes to IndexedDB and localStorage fallback mirror
- [ ] Reload restores workspace from IndexedDB
- [x] IndexedDB-disabled mode uses localStorage fallback
- [x] Workspace JSON backup downloads and restores
- [x] Oversized workspace backup is rejected before parsing
- [x] Malformed/missing optional collections are normalized after valid workspace import
- [ ] Clear/reset initializes every feature history collection
- [ ] Search and status/endpoint/type filters compose

## Event and endpoint workflow
- [ ] Create event validates JSON object payload
- [ ] Add/edit/delete endpoint profiles work without deleting event history
- [x] CSV and Markdown exports download
- [x] Formula-like string cells are neutralized in CSV export
- [x] Event details escape untrusted payload strings before rendering
- [x] Imported identifiers are normalized before entering HTML attributes

## Replay lab
- [ ] Healthy replay succeeds on first attempt
- [ ] Flaky replay retries then recovers when attempt budget permits
- [ ] 429 replay records rate-limit failures and recovery
- [ ] Server-error and timeout profiles end as failed
- [ ] Experiment history persists after reload

## Idempotency lab
- [ ] Key strategy accepts first delivery and suppresses repeats
- [ ] Payload-fingerprint strategy reports the same logical duplicate behavior
- [ ] No-deduplication strategy accepts all repeats
- [ ] Empty idempotency key is rejected
- [ ] Experiment history persists and CSV export downloads

## Contract diff lab
- [ ] Valid nested JSON payloads compare recursively
- [ ] Invalid JSON is rejected with a useful message
- [ ] Removed fields and type changes are marked potentially breaking
- [ ] Added paths are reported separately
- [ ] Comparison history persists
- [ ] Markdown report downloads

## Signature studio / privacy
- [x] HMAC signature generation returns sha256 header
- [x] Empty secret and malformed/non-integer timestamps are rejected
- [ ] Valid signature verifies; tampered body fails
- [ ] Timestamp outside tolerance is rejected
- [ ] Core functionality makes no external network calls
- [ ] No production credentials are embedded in sample data
