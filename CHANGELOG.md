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
