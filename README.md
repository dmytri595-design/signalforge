# SignalForge — Webhook Reliability Lab

**Break the webhook happy path before production does.**

SignalForge is a local-first testing workbench for teams building webhook consumers and event-driven integrations. It makes transient failures, retries, duplicate delivery, signature validation, and payload contract drift repeatable without standing up a test backend.

## Feature set
- **Event ledger:** searchable event stream, endpoint/status/type filters, payload inspection, CSV export, and activity history.
- **Endpoint profiles:** configure simulated receiver behavior, retry budget, backoff, and HMAC demo secrets.
- **Chaos/replay lab:** healthy, flaky 503, 429 rate limit, persistent 500, timeout, and invalid-signature scenarios; attempt timelines and experiment history.
- **Idempotency lab:** model repeated deliveries with key-based, payload-fingerprint, or no-deduplication receiver strategies; compare accepted vs suppressed deliveries and export runs.
- **Contract diff lab:** recursively compare JSON payloads, flag removed fields and type changes as potentially breaking, identify added paths, and export Markdown reports.
- **HMAC studio:** native Web Crypto HMAC-SHA256 generation/verification, raw-body tamper checks, and timestamp tolerance.
- **Insights:** delivery success, retry overhead, endpoint comparison, failure fingerprints, and actionable test checklist.
- **Workspace data:** IndexedDB persistence with localStorage fallback, JSON backup/restore, CSV exports, and Markdown reports.
- **Private by default:** no external runtime dependencies, API keys, tracking, or network calls.

## Live demo
- **Vercel:** https://signalforge-brown.vercel.app
- **Source:** https://github.com/dmytri595-design/signalforge

The hosted site is a static snapshot of the tested `main` source revision. GitHub-to-Vercel automatic redeploys are not connected yet; changes pushed to GitHub need a manual redeploy until that integration is linked.

## Run
Open index.html in a modern browser or serve this repository as a static site. No build step is required.

## Important boundaries
Delivery and receiver behavior are simulated; endpoint URLs are labels and are never contacted. Data stays in the browser profile unless exported. The contract diff is a structural heuristic, not a substitute for consumer contract tests. The idempotency lab models receiver behavior and does not provide a durable production dedupe store. This is not a hosted multi-user database or production webhook gateway. Never use production secrets in the demo.

## Status
Functional local-first developer tool / pre-launch / pre-revenue. No customers or revenue are claimed.
