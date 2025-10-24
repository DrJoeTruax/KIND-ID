# KIND-ID Legal Compliance and License Policy

### Version 1.0.0  
### Updated: October 2025  

---

## 1. Purpose

This document outlines KIND-ID’s compliance obligations, legal framework, and open-source licensing terms.  
It ensures that distribution, contribution, and operation of KIND-ID meet global regulatory and ethical standards.  
It complements:  
- [Governance Charter](../docs/GOVERNANCE_CHARTER.md)  
- [Audit Logging Policy](../docs/AUDIT_LOGGING_POLICY.md)  
- [Commercial Release and Support Policy](../docs/COMMERCIAL_RELEASE_AND_SUPPORT.md)

---

## 2. Legal Framework Overview

KIND-ID complies with international privacy, security, and data processing laws to ensure responsible use of identity data.  

| Regulation | Jurisdiction | Key Principle |
|-------------|---------------|----------------|
| **GDPR (2016/679)** | European Union | Lawful, fair, and transparent processing. |
| **CCPA/CPRA** | California, USA | Right to access, delete, and opt-out. |
| **HIPAA** | USA | Safeguarding of health-related identifiers. |
| **ISO/IEC 27001** | Global | Information security management system (ISMS). |
| **NIST SP 800-53** | USA (Federal) | Security and privacy controls for federal systems. |

KIND-ID processes no personal data in plaintext and follows a **Zero Knowledge Architecture**.

---

## 3. Data Protection Policy

- No unencrypted personal identifiers are stored.  
- All user inputs are anonymized at source.  
- Cryptographic operations occur on-device whenever possible.  
- Data retention follows jurisdictional minimums only.  
- Logs are hashed and detached from direct user references.  
- Users can export and delete their own cryptographic materials.  

---

## 4. User Consent and Transparency

1. Consent is explicit for every identity proof operation.  
2. The extension and SDK display a **“Why and What”** modal before each verification.  
3. Consent records are signed and timestamped in the audit chain.  
4. Revoked consent automatically disables downstream verification.  

---

## 5. Contributor License Agreement (CLA)

All external contributors must agree to the **KIND-ID Contributor License Agreement** before their pull requests are merged.

| Clause | Description |
|--------|-------------|
| **Grant of Copyright License** | Contributors retain copyright but license rights to KIND-ID for use and redistribution. |
| **Grant of Patent License** | Contributors grant a perpetual, worldwide, royalty-free license for any necessary patents. |
| **Representation of Origin** | Code submissions must be original and not infringe third-party rights. |
| **Right to Revoke** | Maintainers may revoke contributor rights for violation of ethical or legal standards. |

---

## 6. Licensing Model

| Component | License | Notes |
|------------|----------|-------|
| **KIND-ID SDK / Server** | MIT License | Open-source under permissive terms. |
| **KIND-ID Extension** | MIT License | Free use, modification, and redistribution. |
| **Documentation** | CC BY 4.0 | Attribution required. |
| **Binary Builds** | Proprietary Signature Layer | Required for enterprise integrity verification. |

License files reside in the root directory (`/LICENSE`).

---

## 7. Third-Party Dependencies

All dependencies must meet open-source license compatibility with MIT.  
Automated checks (`pip-licenses`, `license-checker`) verify compliance before each release.

| Package | License | Verification |
|----------|----------|--------------|
| FastAPI | MIT | Compatible |
| PyCryptodome | BSD | Compatible |
| SQLAlchemy | MIT | Compatible |
| Node Modules | MIT/BSD/Apache 2.0 | Compatible |

Dependencies under GPL or AGPL are explicitly forbidden.

---

## 8. Export Control and Cryptography Compliance

KIND-ID uses cryptographic functions (AES, Ed25519, SHA3-512) and is subject to export controls under U.S. EAR §740.13(e).  

| Region | Compliance Requirement |
|---------|------------------------|
| **United States** | Encryption registration filed annually with BIS. |
| **EU / UK** | General use permitted under dual-use exemption. |
| **China / Russia** | Requires import compliance verification before distribution. |

All export filings documented under `/docs/legal/export/`.

---

## 9. Data Breach Protocol

1. Notify data controllers and affected users within 72 hours.  
2. Include details of nature, scope, and mitigation steps.  
3. Conduct root-cause analysis and document in `INCIDENT_REPORT.md`.  
4. Update threat model postmortem within 7 days.  
5. Report summary to governance oversight committee.  

---

## 10. Ethical Use and Restriction Policy

KIND-ID must not be used for:
- Surveillance, discrimination, or social credit scoring.  
- Military targeting or political repression.  
- Unauthorized biometric collection.  
Violations trigger revocation of license under Section 8 of the MIT License clause.  

---

## 11. Attribution Requirements

When distributing modified versions:
- Retain original copyright headers.  
- Include the full MIT license text.  
- Reference “Based on KIND-ID by Joseph Truax” in documentation.  

---

## 12. Legal Contacts

| Inquiry Type | Email |
|---------------|--------|
| Legal Compliance | legal@kindid.io |
| Licensing | license@kindid.io |
| Export Control | export@kindid.io |
| Ethics Violations | ethics@kindid.io |
