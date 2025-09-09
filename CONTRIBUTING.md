# Contributing

- Keep Sigma rules minimal, with clear FP notes and links to ATT&CK.
- Use consistent field names; avoid vendor‑unique fields unless behind `| field` mappings.
- Add tests/sample events in `tests/` when possible.
- Run `sigma validate rules/sigma` before sending PRs.
