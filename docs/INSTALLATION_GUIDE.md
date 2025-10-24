````
# KIND-ID Installation Guide

### Version 1.0.0  
### Updated: October 2025  

---

## Purpose

This guide explains how to install, configure, and verify the **KIND-ID Authentication Framework** across platforms — including Python SDK, FastAPI server, and Chrome extension.  

If you followed the [README](../README.md) setup, you already have the folder structure.  
Now, complete your installation and verify your environment.

---

## 1. Prerequisites

| Component | Requirement |
|------------|--------------|
| Python | 3.11 or newer |
| Node.js | 18+ (for Chrome extension tools) |
| Git | Latest |
| Operating System | Windows 10/11, macOS 13+, Ubuntu 22.04+ |

Install system packages:

```bash
# Ubuntu/Debian
sudo apt update && sudo apt install python3-pip nodejs npm git

# macOS (Homebrew)
brew install python git node

# Windows
winget install Python.Python.3.11 Git.Git Node.Nodejs
````

---

## 2. Clone the Repository

```bash
git clone https://github.com/DrJoeTruax/KIND-ID.git
cd KIND-ID
```

If you already have a local copy, skip this step.

---

## 3. Install the Python SDK

### Option A — Editable install

```bash
pip install -e .
```

### Option B — Virtual environment

```bash
python -m venv venv
venv\Scripts\activate  # Windows
source venv/bin/activate  # macOS/Linux
pip install -r requirements.txt
```

---

## 4. Run the FastAPI Server

```bash
uvicorn server.app:app --reload
```

### Verify

Open:
➡️ [http://127.0.0.1:8000/health](http://127.0.0.1:8000/health)

Expected output:

```json
{
  "status": "ok",
  "version": "1.0.0"
}
```

---

## 5. Install the Chrome Extension

### Build Steps

```bash
cd extension
npm install
npm run build
```

Then open Chrome → `chrome://extensions` → **Enable Developer Mode** → **Load unpacked** → Select the `extension/build` folder.

After loading, a KIND-ID icon appears in your toolbar.

---

## 6. Authentication Test (End-to-End)

### Run:

```bash
python -m kindid.tests.integration
```

Expected output:

```
[✔] Descriptor generation OK
[✔] Verification OK
[✔] Encryption/Decryption OK
[✔] Server connection OK
```

If all checks pass, KIND-ID is fully operational.

---

## 7. Environment Variables (Optional)

Create a `.env` file in the root directory:

```bash
API_URL=https://api.kindid.io/v1
SECRET_KEY=change_this_to_random_string
LOG_LEVEL=info
```

---

## 8. Platform Installers (Cross-OS)

| Platform | Script                         |
| -------- | ------------------------------ |
| Windows  | `installers\setup_windows.ps1` |
| macOS    | `installers\setup_macos.sh`    |
| Linux    | `installers\setup_linux.sh`    |

Run your OS installer to configure PATH variables and dependencies automatically.

---

## 9. Troubleshooting

| Issue                  | Solution                                 |
| ---------------------- | ---------------------------------------- |
| `uvicorn not found`    | Run `pip install uvicorn`                |
| `Permission denied`    | Re-run with admin rights or `sudo`       |
| `Extension won’t load` | Ensure build directory is complete       |
| Network timeouts       | Check proxy/firewall or try offline mode |

---

## 10. Offline Installation

1. Download ZIP from GitHub.
2. Extract and run:

   ```bash
   pip install --no-index --find-links ./packages kindid
   ```
3. Start FastAPI manually:

   ```bash
   uvicorn server.app:app --host 0.0.0.0 --port 8000
   ```

---

## 11. Verification Checklist

| Step             | Status |
| ---------------- | ------ |
| SDK installed    | ✅      |
| Server running   | ✅      |
| Extension loaded | ✅      |
| End-to-end test  | ✅      |

---

## 12. Next Steps

* Explore [API Reference](API_REFERENCE.md)
* Read [Security & Threat Model](SECURITY_AND_THREAT_MODEL.md)
* See [FAQ](FAQ.md)

---

© 2025 KIND-ID Project. MIT License.

```
```

