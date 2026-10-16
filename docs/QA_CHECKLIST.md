# QA checklist

- [ ] First visit seeds demo workspace
- [ ] Reload restores workspace from IndexedDB
- [ ] IndexedDB-disabled mode uses localStorage fallback
- [ ] Create event validates JSON object payload
- [ ] Search and status/endpoint/type filters compose
- [ ] Add/edit/delete endpoint profiles work without deleting history
- [ ] Healthy replay succeeds on first attempt
- [ ] Flaky replay retries then recovers when attempt budget permits
- [ ] 429 replay records rate-limit failures and recovery
- [ ] Server-error and timeout profiles end as failed
- [ ] Experiment history persists after reload
- [ ] HMAC signature generation returns sha256 header
- [ ] Valid signature verifies; tampered body fails
- [ ] Timestamp outside tolerance is rejected
- [ ] JSON backup imports into a workspace
- [ ] CSV and Markdown exports download
- [ ] Core functionality requires no external network calls
