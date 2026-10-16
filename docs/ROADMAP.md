# Roadmap

## Current
Local event ledger, endpoint profiles, chaos replay, attempt timeline, HMAC-SHA256 signing/verification, timestamp tolerance, insights, JSON backup/restore, CSV and Markdown exports, IndexedDB persistence.

## Next
1. Add event schema templates and idempotency-key comparison.
2. Add configurable retry-after handling and dead-letter queue views.
3. Add deterministic random seeds for replay reproducibility.
4. Add browser-side diff of payload versions.
5. Optional production adapter layer for real HTTP delivery with explicit opt-in and safe URL allowlist.
6. If hosted multi-user storage is needed, introduce a first-party backend/database and auth; do not imply IndexedDB is server storage.
