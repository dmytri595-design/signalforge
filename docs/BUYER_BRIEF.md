# SignalForge — Acquisition Buyer Brief

## Product in one sentence

SignalForge is a local-first webhook reliability workbench for developers and QA teams to exercise retry failures, signature validation, duplicate delivery, and payload-contract drift without configuring a backend or contacting a receiver.

## Why an existing software company might care

The product is a compact, working foundation that could be embedded into an existing API, webhook, developer-experience, observability, QA, or integration product. A buyer with an established customer base may use it as:

- a local troubleshooting and reproducible-test utility for customers integrating webhooks;
- a developer-education or onboarding feature within an API/integration platform;
- a seed for broader contract-testing, webhook-debugging, or integration-QA tools;
- a toolkit for a QA/automation consultancy that needs repeatable demonstrations and reports.

The likely advantage is a usable workflow and feature foundation—not proven market demand or an existing revenue stream.

## Functionality available in the current browser prototype

- Event ledger with searchable/filterable fixtures, payload inspection, delivery attempts, endpoint profiles, and CSV export.
- Replay/chaos scenarios for transient 503 errors, 429 rate limits, persistent 500s, timeouts, and invalid signatures, with attempt timelines.
- HMAC-SHA256 generation/verification using the Web Crypto API, raw-body tamper checks, and timestamp tolerance.
- Idempotency lab comparing key-based, payload-fingerprint, and no-deduplication receiver models.
- Recursive JSON structural comparison for additions, removed paths and type changes, with Markdown reports.
- Insights, endpoint comparisons, failure fingerprints, saved experiment history, and an actionable test checklist.
- IndexedDB/localStorage persistence, JSON workspace backup/restore, CSV export, and Markdown reports.
- No runtime dependencies, no build step, no API keys, and no external HTTP requests from the app.

## Assets and links

- **Live demo:** https://signalforge-brown.vercel.app
- **Source repository:** https://github.com/dmytri595-design/signalforge
- **Product brief:** docs/PRODUCT_BRIEF.md
- **Technical handoff:** docs/TECHNICAL_HANDOFF.md
- **QA checklist:** docs/QA_CHECKLIST.md
- **QA report:** docs/QA_REPORT.md
- **Suggested roadmap:** docs/ROADMAP.md

The Vercel URL is a manually deployed static snapshot, separate from GitHub. It must be redeployed after source changes; the current release workflow tests GitHub source but does not automatically publish it to Vercel.

## Current stage and factual status

SignalForge is a functional local-first prototype / pre-launch / pre-revenue. No paying users or revenue are claimed. The interface uses seeded demonstration data and deterministic simulations.

The app never sends the configured endpoint URLs requests. Replay and receiver response behavior are simulated in-browser. IndexedDB/localStorage are browser-local, not a hosted shared database. The idempotency lab models receiver behavior and is not a production atomic deduplication store. HMAC Studio is a test utility, not a secret manager or production verification service. Contract diff is a structural heuristic and does not prove semantic/API compatibility. There is no hosted team workspace, authentication, server-side audit log, CI provider integration, billing, or production SLA.

## Reliability / data handling improvements

The current source normalizes and bounds imported workspace state, limits restore files to 10 MB and caps endpoint/event record counts, degrades to localStorage when IndexedDB fails where possible, warns if browser persistence is unavailable, sanitizes imported record identifiers, and prefixes formula-like string cells in CSV exports. HMAC actions validate secrets, Unix timestamps, signature-header shape, and timestamp tolerance.

These safeguards improve the demo's resilience but do not turn it into a production multi-tenant service or security-certified product.

## Production extension path

1. Define the intended buyer use cases and a reproducible scenario/contract-fixture format.
2. Add schema-aware compatibility rules (e.g. JSON Schema), fixtures for optionality and array-item variation, and report-quality evaluations.
3. Build an opt-in local receiver harness with strict loopback/SSRF controls, request limits, and isolated test credentials, if real HTTP replay is required.
4. Add a CI adapter to run saved contract fixtures within the buyer's existing test pipeline.
5. Add hosted team workspaces, access controls, shared history, audit retention and secure secret handling only if demand warrants it.

This is a proposed roadmap; those capabilities are not included in the current prototype.

## Commercial context

The current seller-prepared listing suggests an initial asking price of **USD 2,900**, with a possible faster-sale discussion around **USD 1,500–2,000**. These are seller positioning figures, not an independent valuation, market quote, or guaranteed offer. A direct acquisition offer should be based on diligence and the actual rights and assets transferred.

## IP / transaction scope

The repository currently has no top-level LICENSE file. That fact is not a substitute for legal review or a complete chain-of-title audit. Before any sale, define the assets and rights covered by the transaction (source code, product name/brand, documentation, test fixtures, deployment snapshot and any future unpublished work), disclose third-party/open-source components used in development or CI, and use a written agreement reviewed by qualified counsel.

## Best-fit buyer

An existing developer-tools, API/integration, webhook-platform, observability, SaaS or QA-services business with distribution could be a better match than a general side-project marketplace. The initial conversation should test strategic fit first; the project should not be presented as a proven business or production webhook gateway.
