# KIND-ID v1.2 — “You Only Get One”

### Passwordless Identity • One-Try Lockout • Deterministic Recovery

---

## 🔍 Overview

KIND-ID is a **phrase-based authentication system** that replaces passwords with natural language identity.  
It allows human imperfection at input (spelling or phonetic drift) but enforces **absolute lockout on failure**.  
You get one verified attempt.  If the phrase or canonical form is wrong, the descriptor locks until valid recovery.

---

## 🧩 Core Features

| Capability | Description |
|-------------|--------------|
| **Multi-Truth Authentication (MTA)** | Users authenticate with personally meaningful phrases, not secrets they must remember perfectly. |
| **Fuzzy Normalization** | Text is phonetic- and spelling-normalized before hashing (`rapidfuzz` + `metaphone`). “mi nam is steev” → “my name is steve.” |
| **Cryptographic Binding** | Deterministic Argon2id key derivation: `K = Argon2id(device_id + salt + canonical_phrase + pepper)`. |
| **One-Try Lockout** | On first failed verification, descriptor is marked *used* and *locked*—no retries. |
| **Deterministic Recovery** | Recovery token (HMAC of descriptor + salt) unlocks and rotates salt/hash exactly once. |
| **Device Binding** | Every descriptor is tied to a unique device identifier.  Copying a descriptor elsewhere invalidates it. |
| **Auditable Flow** | Every verification, lock, or recovery is logged with immutable timestamps. |

---

## ⚙️ Architecture

```

KIND-ID/
├── kindid/                 # Core SDK (Argon2id + fuzzy normalization)
│   ├── kindid.py
│   ├── normalize.py
│   └── utils/
│
├── server/                 # FastAPI reference backend
│   ├── app.py              # /enroll, /verify, /recover endpoints
│   ├── db/                 # sqlite or postgres state
│   ├── config/             # server keys, pepper, logging
│   └── tests/
│
├── docs/                   # Security & governance suite
├── installers/             # Windows/macOS/Linux setup scripts
└── infra/                  # Docker/K8s/CI scaffolding (optional)

````

---

## 🚀 Quick Start

### 1️⃣ Environment

```bash
git clone https://github.com/DrJoeTruax/KIND-ID
cd KIND-ID
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
````

### 2️⃣ Local Demo (SDK only)

Train:

```bash
python kindid.py --train --text "My name is Steve" --device-id "DEVICE123" --output descriptor.json
```

Verify (fuzzy accepted):

```bash
python kindid.py --verify --text "mi nam is steev" --device-id "DEVICE123" --reference descriptor.json
```

If normalized text resolves to the same canonical form → verified.
If not → descriptor locks permanently.

---

## 🖥️ FastAPI Service

Run:

```bash
uvicorn server.app:app --reload
```

### API Endpoints

| Method | Path       | Description                        |
| ------ | ---------- | ---------------------------------- |
| `POST` | `/enroll`  | Create descriptor + recovery token |
| `POST` | `/verify`  | Verify phrase; locks on failure    |
| `POST` | `/recover` | Unlock using valid recovery token  |

All endpoints enforce TLS 1.3, constant-time comparisons, and atomic state updates.

---

## 🔒 Security Model

| Layer             | Mechanism                                                |
| ----------------- | -------------------------------------------------------- |
| **Input**         | Canonicalization and phonetic normalization              |
| **Derivation**    | Argon2id (time_cost=3, memory_cost=65536, parallelism=4) |
| **Server Secret** | Pepper stored in Vault/HSM                               |
| **Lock Policy**   | Single failed attempt → lock=true                        |
| **Recovery**      | One-time HMAC token + device attestation                 |
| **Transport**     | HTTPS (TLS 1.3, cert-pinned clients)                     |
| **Auditing**      | Immutable logs for every event                           |

---

## 🧾 Recovery Workflow

1. **At enrollment**, server issues a one-time recovery token (QR + string).
2. **If locked**, user submits token + device ID to `/recover`.
3. Server verifies token → rotates salt + hash → unlocks descriptor.
4. Token is invalidated immediately.
5. All actions logged for audit.

---

## 🧠 Philosophy

*Security through understanding.*
Humans forget, mistype, and speak imperfectly.  KIND-ID preserves that humanity while keeping the cryptography absolute.
You either know your truth—or you wait for recovery.

---

## 📜 License

MIT License © 2025 Dr. Joe Truax and community contributors.

---

## 🧪 Future Additions

* Argon2id → hybrid with hardware-based attestation keys
* Formal zero-knowledge verification layer
* SOC2/ISO27001 compliance pipeline under `/infra/compliance`
* Optional multi-modal enrollment (text + voice + gesture)
