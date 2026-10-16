# Product brief — SignalForge

## Problem
Webhook consumers fail on transient 5xx responses, 429 rate limits, delayed retries, duplicate delivery, timestamp drift, and signature mismatches. Reproducing these edge cases usually means custom scripts or waiting for a real failure.

## Product
SignalForge is a local-first webhook reliability lab. Create sample events, simulate receiver failure profiles, inspect retry timelines, and test HMAC signatures without sending requests or sharing payloads with a third party.

## Personas
- Backend engineers integrating billing, commerce and partner webhooks
- QA engineers testing retry and idempotency behavior
- Technical founders needing a focused reliability checklist without deploying infrastructure

## Differentiator
A zero-setup browser-only reliability lab with a persistent local event ledger and native HMAC studio. No credentials, API keys, external requests, or server setup are required.

## Release scope
Local-first prototype / pre-launch. Delivery is simulated. IndexedDB is a browser-local database, not shared server persistence.
