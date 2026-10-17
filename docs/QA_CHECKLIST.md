# QA checklist — SignalForge v1.1

## Persistence and workspace
- [ ] First visit seeds demo workspace
- [ ] Save writes to IndexedDB and localStorage fallback mirror
- [ ] Reload restores workspace from IndexedDB
- [ ] IndexedDB-disabled mode uses localStorage fallback
- [ ] Workspace JSON backup downloads and restores
- [ ] Clear/reset initializes every feature history collection
- [ ] Search and status/endpoint/type filters compose

## Event and endpoint workflow
- [ ] Create event validates JSON object payload
- [ ] Add/edit/delete endpoint profiles work without deleting event history
- [ ] CSV and Markdown exports download
- [ ] Event details escape untrusted payload strings before rendering

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
- [ ] HMAC signature generation returns sha256 header
- [ ] Valid signature verifies; tampered body fails
- [ ] Timestamp outside tolerance is rejected
- [ ] Core functionality makes no external network calls
- [ ] No production credentials are embedded in sample data
