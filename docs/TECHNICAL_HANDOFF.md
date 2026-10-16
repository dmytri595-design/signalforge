# Technical handoff

## Architecture
- Static single-page app in `index.html`
- IndexedDB database `signalforge-local-db`, object store `workspace`, key `main`
- localStorage mirror/fallback `signalforge:workspace:v1`
- Native Web Crypto `crypto.subtle` for HMAC-SHA256
- File/Blob APIs for JSON, CSV and Markdown
- No third-party runtime dependencies and no outbound fetch/XHR

## Workspace schema
`{ version, settings, endpoints[], events[], experiments[], activity[], createdAt, updatedAt }`

## Persistence
IndexedDB is primary; localStorage mirrors the snapshot for fallback. Backup is a JSON snapshot. Restore replaces the local workspace after confirmation. Clearing data affects only the current browser profile. A fresh browser receives synthetic demo data.

## Safety boundaries
Endpoint URLs are labels; no webhook requests are sent. Secrets are demo-local configuration. The browser database is not encrypted or synchronized across devices.
