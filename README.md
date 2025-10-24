# KIND-ID v1.0.0

### “Authentication that remembers who you are.”

---

## 🧭 Table of Contents
1. [Overview](#overview)
2. [Quick Start](#quick-start)
3. [Project Structure](#project-structure)
4. [Cross-Linked Documentation](#cross-linked-documentation)
5. [Philosophy & Goals](#philosophy--goals)
6. [Community & Governance](#community--governance)
7. [Security Summary](#security-summary)
8. [License & Acknowledgments](#license--acknowledgments)

---

## Overview

KIND-ID is a **human-centric authentication SDK and framework** built to
replace passwords with phrase-based, cryptographically verified identity.

It includes:

* 🧩 **Python SDK** – Argon2id + HMAC authentication core  
* 🌐 **FastAPI Server** – challenge-response verification service  
* 🧠 **Chrome Extension** – deterministic password manager  
* 🧪 **Certification Tests** + CI pipeline  
* 🛡 **Threat Model** and Governance Charter  
* 📚 **Full Documentation Suite** (this repository)

---

## Quick Start

### 1️⃣ Install

```bash
git clone https://github.com/DrJoeTruax/KIND-ID.git
cd KIND-ID
pip install -e .
````

### 2️⃣ Run Server

```bash
uvicorn server.app:app --reload
```

### 3️⃣ Try the Demo

Open `examples/signup.html` in a browser to generate your first descriptor and verify it with the FastAPI service.

---

## Project Structure

```
kindid/             # Python SDK
server/             # FastAPI service
extension/          # Browser extension
docs/               # Documentation suite
tests/              # Unit tests
.github/workflows/  # CI/CD pipeline
installers/         # Platform installers + telemetry stubs
```

---

## Cross-Linked Documentation

* [API Reference](docs/API_REFERENCE.md)
* [Installation Guide](docs/INSTALLATION_GUIDE.md)
* [Security & Threat Model](docs/SECURITY_AND_THREAT_MODEL.md)
* [Governance Charter](docs/GOVERNANCE_CHARTER.md)
* [FAQ](docs/FAQ.md)
* [Change Log](docs/CHANGELOG.md)
* [Contributing Guide](CONTRIBUTING.md)
* [Code of Conduct](CODE_OF_CONDUCT.md)
* [License](LICENSE)

---

## Philosophy & Goals

* Humans first – security through understandable interaction.
* Zero trust without zero humanity.
* Transparency by default – all actions auditable and open-source.
* Cross-platform and multi-language future (Go, JS, Rust bindings planned).

---

## Community & Governance

* Open source under MIT License.
* Guided by the [Governance Charter](docs/GOVERNANCE_CHARTER.md).
* Maintainer team elected by contributors.
* All decisions and votes publicly logged.

---

## Security Summary

* Argon2id memory-hard key derivation.
* Salt + device ID + phrase concatenation.
* Challenge-response login flow.
* Constant-time comparison (HMAC).
* Encrypted descriptor storage (AES-256-GCM).
* Rate limiting and nonce expiration.
* Pen-test and bug-bounty program planned for v1.1.0.

---

## License & Acknowledgments

Released under the MIT License – see [LICENSE](LICENSE).
Authored and maintained by **Dr. Joe Truax** and community contributors.
Uses Argon2 (from libsodium / argon2-cffi), FastAPI, and standard cryptography libraries.
