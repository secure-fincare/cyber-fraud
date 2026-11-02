# CyberLink Shield

**Offline-first, open-source malicious URL protection for everyday users.**

CyberLink Shield is a privacy-first project blueprint and starter implementation for detecting suspicious URLs locally. The initial scaffold contains a Rust URL normalization and reputation engine, a local SQLite schema, a Python FastAPI service skeleton, tests, documentation, and GitHub Actions workflows.

> Status: early development scaffold. This is not yet a production security product and must not be relied on as the sole protection against cybercrime.

## Design principles

- **Local decisions:** URL analysis uses local code and local indicators by default.
- **No browsing telemetry by default:** clients do not upload visited URLs.
- **Signed intelligence:** future feed packages must be authenticated before installation.
- **Explainable outcomes:** detections should include reasons and confidence, not just a score.
- **Fail safely:** stale or missing intelligence is shown clearly; unknown URLs are not automatically labelled safe.
- **Least privilege:** platform integrations request only the permissions they need.

## Repository layout

- `core/engine-rust/` — shared URL normalization and local reputation library.
- `backend/api/` — optional FastAPI service skeleton for health and feed metadata.
- `database/` — SQLite schema for local indicators and local events.
- `docs/` — architecture, privacy and threat model.
- `tests/` — sample test corpus.
- `.github/workflows/` — CI checks.

## Quick start: Rust CLI

Requirements: Rust stable toolchain.

```bash
cd core/engine-rust
cargo test
cargo run -- "https://example.com/login"
```

The starter CLI normalizes a URL and reports `unknown` unless a local indicator is explicitly loaded. It does not claim an unknown URL is safe.

## Quick start: API skeleton

Requirements: Python 3.11+.

```bash
cd backend/api
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

Open `http://127.0.0.1:8000/docs`.

## Roadmap

1. Harden URL parsing and canonicalization.
2. Add signed, versioned feed format and atomic SQLite updates.
3. Implement browser extension and Android share-intent scanner.
4. Add Windows network integration with explicit consent.
5. Add feed adapters only after reviewing each provider's terms and redistribution rights.
6. Conduct independent security review before production claims.

## Threat intelligence and licensing

Potential sources include URLhaus, PhishTank, OpenPhish and MISP. Each source has its own terms, attribution, API limits and redistribution conditions. Do not bundle or redistribute feed data until those conditions have been reviewed.

## Security reporting

Please do not publish exploitable vulnerability details in public issues. See [SECURITY.md](SECURITY.md).

## License

Apache-2.0. See [LICENSE](LICENSE).
