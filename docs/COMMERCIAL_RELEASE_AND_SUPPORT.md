# KIND-ID Commercial Release and Support Policy

### Version 1.0.0  
### Updated: October 2025  

---

## 1. Purpose

This document defines KIND-ID’s release management, distribution channels, versioning, and long-term support (LTS) strategy.  
It ensures consistent delivery, reliability, and transparency across all product editions.  
It aligns with:  
- [Deployment Manual](../docs/DEPLOYMENT_MANUAL.md)  
- [Monitoring and Maintenance Guide](../docs/MONITORING_AND_MAINTENANCE.md)  
- [Governance Charter](../docs/GOVERNANCE_CHARTER.md)

---

## 2. Product Editions

| Edition | Target Audience | Description |
|----------|------------------|--------------|
| **Community** | Open-source developers | Free tier for experimentation and education. |
| **Enterprise** | Organizations requiring SLA and audit support | Managed deployments with signed binaries. |
| **LTS (Long-Term Support)** | Government, research, or regulated clients | Maintained for 24 months with extended security updates. |

---

## 3. Versioning Scheme

Semantic Versioning (SemVer 2.0):  
```

MAJOR.MINOR.PATCH

```

| Increment | Trigger |
|------------|----------|
| **MAJOR** | Breaking API or protocol changes |
| **MINOR** | New features, backward-compatible |
| **PATCH** | Bug or security fixes only |

Each release is digitally signed and tagged in Git (`vX.Y.Z`).

---

## 4. Release Pipeline

1. **Development** → feature branches merge into `main`.  
2. **Pre-Release** → candidate version (`-rc1`) built and tested.  
3. **QA Signoff** → automated integration + manual acceptance tests.  
4. **Release Approval** → governance board authorizes version freeze.  
5. **Tag & Publish** → pushed to PyPI, DockerHub, and Chrome Web Store.  
6. **Announcement** → published in `/docs/CHANGELOG.md` and project website.

All builds use SHA-256 checksums and reproducible Docker layers.

---

## 5. Supported Platforms

| Platform | Binary / Package | Notes |
|-----------|------------------|--------|
| **Windows 10/11** | `.exe` / `.msi` | Code-signed via EV certificate |
| **macOS 13+** | `.pkg` | Apple notarized |
| **Linux (x86_64)** | `.deb` / `.rpm` | GPG-signed repo |
| **Browser Extension** | Chrome / Edge | Manifest v3 compliant |
| **Server Image** | Docker | Immutable image with health probes |

---

## 6. Update and Patch Policy

| Category | Description | Timeline |
|-----------|--------------|----------|
| **Critical Security Fixes** | CVE or exploit-level patches | 24–48 hours |
| **Minor Bug Fixes** | Non-breaking runtime or UI errors | 1–2 weeks |
| **Feature Updates** | Enhancements or API additions | Monthly |
| **Major Versions** | Architectural or protocol changes | Quarterly |

Updates are distributed via the GitHub releases feed and package registries.  
Each release is accompanied by an updated hash manifest (`RELEASE_CHECKSUMS.txt`).

---

## 7. Support Tiers

| Tier | Coverage | Response SLA |
|------|-----------|---------------|
| **Community** | Forum + GitHub issues | 72 hours (best effort) |
| **Enterprise** | Email + on-call escalation | 4 hours |
| **LTS Clients** | Dedicated channel + patch backports | 2 hours |

Support is delivered by the KIND-ID maintainers or verified integration partners.  

---

## 8. End-of-Life (EOL) Policy

| Version Type | Support Duration | Notes |
|---------------|------------------|--------|
| **Major** | 24 months | Includes security and compatibility patches |
| **Minor** | 12 months | Maintained until next minor release |
| **Patch** | 6 months | Included in ongoing minor branch support |

Deprecated versions trigger a 90-day advance notice.  

---

## 9. Issue Tracking and Escalation

- **Primary Tracker:** GitHub Issues  
- **Labels:** `bug`, `enhancement`, `security`, `documentation`, `discussion`  
- **Escalation Path:**  
  1. Open issue  
  2. Assign severity  
  3. Triage by maintainer  
  4. Resolution or escalation to governance review  

Incident logs are archived under `/docs/support/tickets/YYYY-MM/`.

---

## 10. Communication Channels

| Purpose | Platform |
|----------|-----------|
| Release announcements | GitHub / project site |
| Security notifications | Email list (`security@kindid.io`) |
| User discussions | GitHub Discussions / Matrix |
| Enterprise coordination | Private Slack or Mattermost instance |

---

## 11. Warranty Disclaimer

KIND-ID is provided “as is” under the MIT License.  
Enterprise clients may purchase optional indemnification or liability coverage as part of the support contract.  

---

## 12. Future Roadmap Integration

Upcoming enhancements to this document will include:
- Verified vendor signature framework.  
- Automated release provenance (SLSA level 3+).  
- Cloud-native release mirrors for redundancy.  
