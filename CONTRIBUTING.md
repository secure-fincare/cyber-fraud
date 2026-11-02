# Contributing

Thanks for helping improve CyberLink Shield.

## Before contributing
- Read `CODE_OF_CONDUCT.md` and `SECURITY.md`.
- Open an issue for substantial changes before starting implementation.
- Never commit real malicious payloads, personal data, API keys, or private feed credentials.
- Do not add threat-feed data unless redistribution rights are documented.

## Development
- Rust: `cargo fmt --check` and `cargo test`.
- Python: install `backend/api/requirements-dev.txt`, then `pytest`.
- Add regression tests for URL parsing and detection changes.
- Explain false-positive implications in pull requests.

## Pull requests
Include purpose, implementation notes, tests performed, compatibility impact, and any privacy or security implications.
