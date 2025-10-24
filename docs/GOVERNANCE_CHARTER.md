# KIND-ID Governance Charter

### Version 1.0.0  
### Updated: October 2025  

---

## 1. Purpose

This charter defines the governance model for the **KIND-ID Project**, ensuring transparent decision-making, fair representation, and ethical stewardship of open-source authentication technology.  

All participants, contributors, and maintainers must follow this governance model to preserve KIND-ID’s credibility, security, and mission alignment.

---

## 2. Core Principles

| Principle | Description |
|------------|--------------|
| **Transparency** | All decisions, votes, and proposals are public in repository issues or discussions. |
| **Meritocracy** | Influence comes from consistent, quality contributions. |
| **Inclusivity** | No discrimination based on identity, geography, or background. |
| **Accountability** | Maintainers must document major technical or policy decisions. |
| **Security First** | Security considerations outweigh convenience or popularity. |

---

## 3. Roles and Responsibilities

### 3.1. Contributors
- Submit code, documentation, or issue reports.  
- Must comply with [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md).  
- Gain commit rights after sustained quality contributions.

### 3.2. Maintainers
- Oversee a component (SDK, Server, Extension, Docs).  
- Approve or reject pull requests.  
- Ensure tests and CI checks pass.  
- Publish release notes and changelogs.

### 3.3. Core Team
- Elected annually by maintainers (minimum 3 members).  
- Final authority on disputes, major roadmaps, and versioning.  
- Responsible for project vision and funding partnerships.

### 3.4. Founder
- Project initiator: **Dr. Joe Truax**  
- Holds symbolic “founding vote” in case of deadlock.  
- No override beyond ethical compliance and legal safety.

---

## 4. Decision-Making Process

| Type | Decision Body | Method |
|-------|----------------|--------|
| Code changes | Maintainers | Pull request reviews (2 approvals required) |
| Documentation updates | Docs maintainers | Merge upon 1 approval |
| Major release (vX.Y.0) | Core Team | Simple majority vote |
| Governance amendments | Core Team + Public Review | 7-day open comment period |
| Security emergency | Founder + Security Lead | Immediate action allowed |

Votes are conducted transparently via GitHub Discussions or Issues.

---

## 5. Release and Versioning

KIND-ID follows **Semantic Versioning (SemVer 2.0.0):**
```

MAJOR.MINOR.PATCH

```
Example:  
- 1.0.0 – First public stable release  
- 1.1.0 – New features, backward compatible  
- 1.1.1 – Bug/security fix  

Each release must include:  
- `CHANGELOG.md` update  
- Release notes under `/docs/releases/`  
- Tagged Git commit and signed artifact  

---

## 6. Funding and Donations

The project accepts ethical funding only from organizations aligned with open-source and digital safety standards.

### Acceptable
- Foundations (Linux Foundation, OpenSSF)
- Public grants
- Individual sponsors (GitHub Sponsors, Patreon)

### Prohibited
- Entities linked to surveillance, censorship, or exploitation.
- Political organizations.

Transparency reports are published quarterly.

---

## 7. Conflict Resolution

If disputes arise:
1. Attempt resolution directly via GitHub issue comment thread.  
2. If unresolved within 7 days, escalate to maintainers.  
3. Maintainers mediate; if unresolved, escalate to Core Team.  
4. If still unresolved, Founder casts tie-breaking vote.  

All communications must remain professional and documented.

---

## 8. Security Oversight

- Appoint a **Security Lead** per major version.  
- Maintain vulnerability disclosure policy.  
- Conduct annual threat-model review.  
- Perform dependency audits before each minor release.  

Security advisories are posted under `/security/`.

---

## 9. Amendments

Governance can evolve with community input.  
Amendments require:
- 2/3 majority of maintainers  
- Public review window (7 days)  
- Documentation in `docs/GOVERNANCE_CHARTER.md` changelog section

---

## 10. Legal and Licensing

All contributions are under the **MIT License** unless otherwise stated.  
Contributors agree to the Developer Certificate of Origin (DCO 1.1).

---

## 11. Dissolution Clause

If the project ceases active maintenance:
- Code remains open under MIT License.
- Archive status declared publicly on GitHub.
- Last Core Team publishes a closure report.

---

## 12. Contact

General inquiries: `community@kindid.io`  
Security issues: `security@kindid.io`  
Governance questions: `governance@kindid.io`

---

© 2025 KIND-ID Project. MIT License.
