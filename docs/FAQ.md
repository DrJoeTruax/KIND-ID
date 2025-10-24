# KIND-ID Frequently Asked Questions (FAQ)

### Version 1.0.0  
### Updated: October 2025  

---

## 1. General

### Q: What is KIND-ID?
A: KIND-ID is an open-source authentication framework that replaces passwords with **phrase-based identity** verified through cryptographic descriptors. It lets users authenticate across platforms using natural language instead of passwords.

### Q: Why is it called “KIND-ID”?
A: It stands for **KIND (Knowledge-Integrated Non-Deterministic) Identity** — meaning authentication that adapts to users, not the other way around.

### Q: Is it free to use?
A: Yes. KIND-ID is fully open-source under the MIT License.

---

## 2. Installation & Setup

### Q: What are the requirements to run KIND-ID?
A: You’ll need Python 3.11+, Node.js 18+, and Git. See the [Installation Guide](INSTALLATION_GUIDE.md) for full details.

### Q: Can I install it offline?
A: Yes. Download the repository ZIP and follow the offline instructions in the Installation Guide.

### Q: How do I verify it’s working?
A: Run:
```bash
python -m kindid.tests.integration
````

All checks should pass with ✅ results.

---

## 3. Security

### Q: Does KIND-ID store my password or phrase?

A: No. The system never stores or transmits plaintext phrases — only salted, memory-hard Argon2id hashes.

### Q: How does KIND-ID prevent brute-force attacks?

A: Argon2id hashing, rate limiting, constant-time verification, and nonce validation make brute-force attempts computationally impractical.

### Q: What happens if the server is compromised?

A: Attackers would obtain only random salts and one-way hashes, which are useless without the user’s original phrase and device data.

### Q: Can I use KIND-ID for multi-factor authentication (MFA)?

A: Yes. KIND-ID supports MFA by combining phrase verification with device signature or biometric fallback (planned for v1.1.0).

---

## 4. Technical

### Q: Is it compatible with existing password systems?

A: KIND-ID can coexist with traditional logins or replace them entirely. The SDK provides compatibility layers for legacy auth fields.

### Q: Does it support OAuth or SSO?

A: Planned for v1.2.0. The design accommodates external identity providers (Google, GitHub, etc.) as secondary verifiers.

### Q: How do I integrate it with my own app?

A: Use the Python SDK or REST endpoints documented in [API_REFERENCE.md](API_REFERENCE.md).

Example:

```python
from kindid import Client
client = Client()
descriptor = client.generate_descriptor("My secure phrase", "device123")
```

### Q: What database is used?

A: SQLite for local testing, PostgreSQL for production deployments.

---

## 5. Privacy

### Q: Does KIND-ID collect analytics?

A: No personal telemetry is collected by default. Users may opt in to anonymized performance metrics.

### Q: Can I delete my data?

A: Yes. Use the `/delete` endpoint or remove the local descriptor file.

### Q: Does it comply with GDPR or CCPA?

A: Yes. KIND-ID stores minimal non-identifiable data and includes clear consent options.

---

## 6. Browser Extension

### Q: What does the Chrome extension do?

A: It integrates the KIND-ID password manager and phrase entry system directly into web forms.

### Q: How do I install it?

A: Build it using:

```bash
cd extension
npm install
npm run build
```

Then load it in Chrome under Developer Mode → Load Unpacked.

### Q: Is it available in the Chrome Web Store?

A: Pending approval for v1.0.0 public release.

---

## 7. Troubleshooting

| Problem                    | Solution                                                    |
| -------------------------- | ----------------------------------------------------------- |
| “uvicorn not recognized”   | Run `pip install uvicorn`                                   |
| “Extension failed to load” | Ensure `build` folder exists under `/extension`             |
| “Permission denied”        | Re-run with admin rights                                    |
| “Server won’t start”       | Check that FastAPI and dependencies are installed correctly |

---

## 8. Contributing

### Q: How can I contribute?

A: Fork the repository, make your changes, and open a pull request. Review the [CONTRIBUTING.md](../CONTRIBUTING.md) guide first.

### Q: Who maintains KIND-ID?

A: The Core Team, led by **Dr. Joe Truax** and supported by open-source maintainers.

### Q: How can I report a bug?

A: File an issue on GitHub with the tag `bug` or email `bugs@kindid.io`.

---

## 9. Governance & Legal

### Q: Who owns KIND-ID?

A: The community. It’s open-source under the MIT License.

### Q: What happens if the project ends?

A: The code remains open and functional under the MIT License per the [Governance Charter](GOVERNANCE_CHARTER.md).

### Q: How are security vulnerabilities reported?

A: Send responsible disclosure to `security@kindid.io`.

---

## 10. Contact

| Type       | Email                                               |
| ---------- | --------------------------------------------------- |
| General    | [contact@kindid.io](mailto:contact@kindid.io)       |
| Security   | [security@kindid.io](mailto:security@kindid.io)     |
| Governance | [governance@kindid.io](mailto:governance@kindid.io) |
| Community  | [community@kindid.io](mailto:community@kindid.io)   |

---

© 2025 KIND-ID Project. MIT License.
