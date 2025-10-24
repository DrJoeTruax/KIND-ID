# KIND-ID Changelog

### Version: v1.0.0  
### Updated: October 2025  

---

## Purpose

This document records the chronological evolution of the KIND-ID project, including new features, bug fixes, security patches, and governance updates.  
All releases adhere to **Semantic Versioning (SemVer 2.0.0)** and are signed by maintainers via verified Git tags.

---

## [1.0.0] — 2025-10-24

### Added
- Initial public release of the KIND-ID Authentication Framework.  
- Python SDK with Argon2id-based descriptor generation.  
- FastAPI server for secure verification.  
- Chrome extension for in-browser phrase login.  
- Full documentation suite (README, Installation Guide, API Reference, Security Model, Governance Charter, FAQ).  
- Continuous Integration pipeline and unit test baseline.  
- Open-source governance model and MIT licensing.

### Security
- Implemented constant-time comparison in descriptor verification.  
- Enforced HTTPS/TLS 1.3 across API endpoints.  
- Added nonce and rate-limit enforcement (60 requests/min per IP).  
- Configured automatic dependency scans via GitHub Actions.

---

## [0.9.0] — 2025-09-10

### Added
- Prototype SDK and test harness.  
- Draft documentation and roadmap.  
- Developer-only authentication simulator.  
- CLI utilities for descriptor generation.  

### Changed
- Migrated from bcrypt to Argon2id.  
- Consolidated FastAPI server routes for consistency.

---

## [0.8.2] — 2025-08-03

### Fixed
- Compatibility issue with Windows line endings in test harness.  
- Incorrect hash length causing verification mismatch on certain devices.

---

## [0.8.0] — 2025-07-15

### Added
- Alpha version of Chrome extension (phrase recorder).  
- Local descriptor encryption (AES-256-GCM).  
- Server health check endpoint (`/health`).

---

## [0.7.0] — 2025-06-01

### Added
- Repository scaffolding with modular architecture.  
- Integration with GitHub Actions.  
- Initial setup for Governance and Security documentation.  

---

## Upcoming Milestones

| Version | Target Date | Planned Additions |
|----------|--------------|-------------------|
| **1.1.0** | Q1 2026 | MFA + biometric fallback |
| **1.2.0** | Q2 2026 | OAuth/SSO integration |
| **1.3.0** | Q3 2026 | Encrypted backup & recovery |
| **2.0.0** | 2027 | Hardware token & TEE integration |

---

## Governance & Verification

Each release is verified via:
- Signed Git tag by at least two maintainers.  
- CI/CD build artifact checksum.  
- Updated threat model validation.  
- Public changelog announcement.

---

## Historical Context

KIND-ID originated as part of the **Legacies of Men** initiative led by Dr. Joe Truax, evolving into a universal framework for empathy-based authentication.  
The name reflects its goal: to make digital identity kind, transparent, and human again.

---

© 2025 KIND-ID Project. MIT License.
