# Product brief — SignalForge v1.2

## Problem
Webhook consumers can fail in subtle ways: transient 5xx responses, 429 rate limits, delayed retries, duplicate delivery, timestamp drift, signature mismatches, and payload schema changes. Reproducing these edge cases usually requires custom scripts, a staging endpoint, or waiting for a real failure.

## Product
SignalForge is a zero-setup, browser-local reliability lab. Developers can create event fixtures, configure simulated receiver profiles, inspect retry timelines, test HMAC signatures, model duplicate delivery, and compare two JSON payload contracts before a producer change breaks consumers.

## Personas
- Backend engineers integrating billing, commerce and partner webhooks
- QA engineers testing retry, idempotency, and signature behavior
- Technical founders who need a focused reliability checklist without deploying infrastructure

## Differentiator
A private, browser-only lab that combines replay/chaos simulation, idempotency modeling, payload contract drift analysis, HMAC verification, persistent history, and exportable reports. No credentials, API keys, external requests, or server setup are required.

## v1.1 scope
- Event ledger, endpoint profiles, retry/backoff scenarios, experiment history
- HMAC-SHA256 signature generation and verification with timestamp tolerance
- Idempotency experiment with receiver strategy comparison
- Recursive JSON contract diff and Markdown report export
- IndexedDB with localStorage fallback, bounded/normalized JSON backup/restore, CSV/Markdown export

## Reliability and import safeguards
- If IndexedDB fails, the app attempts to continue with the localStorage mirror; if browser persistence is unavailable, it warns that changes are session-only.
- Imported backup files are size-bounded and normalized, with endpoint/event/history limits to reduce accidental or malformed imports.
- Imported record IDs are normalized, and CSV export prefixes formula-like string cells to reduce spreadsheet formula injection risk.
- HMAC tools require a non-empty secret and positive integer Unix timestamp; verification checks the signature header format and configured time tolerance.

## Honest boundaries
Local-first prototype / pre-launch. Delivery is simulated. IndexedDB is a browser-local database, not shared server persistence. No production receiver is contacted; no production idempotency store or CI provider integration is included.
