# Changelog

## v1.1 — 2026-10-17
- Added Idempotency Lab: simulate repeated webhook deliveries and compare dedupe strategies.
- Added Contract Diff Lab: recursively compare JSON payload shapes, flag removed fields and type changes, list additions, and export Markdown.
- Persisted idempotency and contract comparison histories in the workspace.
- Added idempotency results CSV and contract report Markdown exports.
- Fixed missing save() persistence helper.
- Fixed settings navigation in the second sidebar navigation group.
- Normalized workspace schema and reset/clear state for new history collections.
- Expanded Playwright smoke coverage and buyer documentation.


## v1.2 — 2026-10-26
- Hardened IndexedDB/localStorage persistence so quota or transaction failures fall back without immediately breaking the workspace.
- Normalized imported workspaces and bounded event, endpoint, history and file-size counts before rendering.
- Sanitized imported record identifiers and added export-side CSV formula-injection protection for string values.
- Tightened HMAC generation and verification input checks for Unix-second timestamps and sha256 headers.
- Guarded the scenario-matrix action when no endpoint profiles are configured.
- Expanded Playwright coverage for persistence fallback, imported identifier handling, CSV safety, and invalid HMAC inputs.
- Added a buyer-focused acquisition brief and refreshed seller-facing product documentation.
