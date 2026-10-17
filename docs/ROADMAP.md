# Roadmap — SignalForge

## v1.1 (current)
- Idempotency lab for repeated deliveries and receiver dedupe strategies
- Contract diff lab for nested JSON payload drift
- Persistent experiment/comparison history
- CSV and Markdown exports
- Persistence safety fix: central save helper writes IndexedDB and localStorage mirror
- Expanded browser smoke tests

## Next logical buyer extensions
1. Real local receiver harness on localhost with explicit opt-in and SSRF protections
2. JSON Schema import and schema compatibility rules
3. OpenAPI/event catalog import
4. Signed, reproducible test-case bundles
5. GitHub Actions adapter to run contract fixtures in CI
6. Hosted team workspaces, access control, and shared audit history
7. Integrations for Stripe-like, commerce, and internal event providers

## Out of scope for the local-only release
No real email, no production endpoint delivery, no hosted database, no API keys, no team accounts.
