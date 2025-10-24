# KIND-ID Deployment Manual

### Version 1.0.0  
### Updated: October 2025  

---

## 1. Purpose

This manual describes how to build, package, deploy, and maintain the **KIND-ID** platform across environments.  
It connects to:  
- [System Design Specification](../docs/SYSTEM_DESIGN_SPEC.md)  
- [Audit Logging Policy](../docs/AUDIT_LOGGING_POLICY.md)  
- [Security and Threat Model](../docs/SECURITY_AND_THREAT_MODEL.md)  

---

## 2. Deployment Targets

| Environment | Description | Example Host |
|--------------|--------------|---------------|
| **Local Development** | For debugging and testing on a single machine. | Developer workstation |
| **Staging** | Replica of production used for QA and pen testing. | staging.kindid.local |
| **Production** | Public release with full monitoring and redundancy. | kindid.io |

---

## 3. Pre-Deployment Requirements

1. **Python 3.11+**  
2. **Docker + Docker Compose**  
3. **Node.js 20+** (for browser extension build)  
4. **PostgreSQL 15+**  
5. **OpenSSL 3.0+**  
6. **Environment Variables:**  
   - `KINDID_ENV` = `dev | staging | prod`  
   - `DB_URL` = PostgreSQL connection string  
   - `JWT_SECRET` = 256-bit random hex key  
   - `TLS_CERT` / `TLS_KEY` = paths to TLS certificates  

---

## 4. Build Process

### SDK
```

cd kindid/
python -m build

```

### Server
```

cd server/
docker build -t kindid-server .

```

### Browser Extension
```

cd extension/
npm install
npm run build

```

### Installers
Use OS-specific scripts:
```

installers/windows/build.ps1
installers/linux/build.sh
installers/macos/build.sh

```

---

## 5. CI/CD Integration

**Location:** `.github/workflows/ci.yml`

**Steps:**
1. Run lint + type check (`flake8`, `mypy`)  
2. Run tests (`pytest`, coverage ≥ 90%)  
3. Build Docker image with SHA tag  
4. Push to container registry  
5. Trigger deploy via environment-specific GitHub Action  
6. Post-deploy: run smoke tests and update `CHANGELOG.md`

All secrets pulled from **GitHub Actions Secrets** or **HashiCorp Vault**.  

---

## 6. Deployment Procedure

### Manual (local)
```

docker compose -f docker-compose.yml up --build

```

### Staging
```

kubectl apply -f k8s/staging.yaml
kubectl rollout status deployment/kindid-server

```

### Production
1. Merge approved release branch.  
2. Action runs `deploy-prod.yml`.  
3. Deployment verified via health endpoint `/api/healthz`.  
4. CDN invalidation triggered automatically.

Rollback handled by `kubectl rollout undo`.

---

## 7. Configuration Management

All configs stored in `/config/` and mounted as read-only volumes.  
For critical settings:
- Encryption via AES-256-GCM keys in Vault  
- No plaintext passwords in repos  
- Rotations every 90 days  

---

## 8. Monitoring and Maintenance

| Component | Tool | Purpose |
|------------|------|----------|
| Server | Prometheus + Grafana | Metrics, latency, error rates |
| Logs | Loki | Aggregation and search |
| Alerts | PagerDuty / Email | 24-hour uptime alerts |
| Security | Falco | Runtime intrusion detection |

Daily integrity scan verifies all binaries match CI-signed hashes.  

---

## 9. Backup and Recovery

- Database backup: hourly incremental, daily full.  
- Audit logs stored in WORM-compliant S3 buckets.  
- Recovery tested quarterly using cold-start restore.  

---

## 10. Release Management

| Type | Frequency | Notes |
|-------|------------|-------|
| **Patch** | As needed | Security or urgent fixes |
| **Minor** | Monthly | New features, backward compatible |
| **Major** | Quarterly | Breaking or architectural changes |

Each release increments `CHANGELOG.md` and creates a Git tag (`vX.Y.Z`).

---

## 11. Security Post-Deployment

- Run `trivy` on images for CVEs.  
- Verify TLS certificate expiration.  
- Rotate API keys and JWT secrets quarterly.  
- Perform red-team audit annually.  

---

## 12. Decommission Procedure

1. Notify governance board (see [Governance Charter](../docs/GOVERNANCE_CHARTER.md)).  
2. Freeze database in read-only mode.  
3. Archive encrypted data for 3 years.  
4. Remove infrastructure credentials.  
5. Publish final audit summary to repository.

---

**Document Path:** `/docs/DEPLOYMENT_MANUAL.md`  
**Linked References:**  
- [System Design Specification](../docs/SYSTEM_DESIGN_SPEC.md)  
- [Audit Logging Policy](../docs/AUDIT_LOGGING_POLICY.md)  
- [Security and Threat Model](../docs/SECURITY_AND_THREAT_MODEL.md)  
- [Governance Charter](../docs/GOVERNANCE_CHARTER.md)

---

_End of Document_
