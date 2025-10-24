# KIND-ID API Reference

### Version: v1.0.0  
### Updated: October 2025  

---

## Overview
The **KIND-ID API** exposes both Python SDK functions and REST endpoints for authentication, verification, and descriptor management.

This document is cross-linked with:  
- [Installation Guide](INSTALLATION_GUIDE.md)  
- [Security & Threat Model](SECURITY_AND_THREAT_MODEL.md)  

---

## Python SDK

### `from kindid import Client`

The `Client` object provides local operations such as key generation, phrase verification, and encryption.

#### Methods

| Method | Description | Example |
|---------|--------------|----------|
| `generate_descriptor(phrase, device_id)` | Generates Argon2id-hashed identity descriptor. | `client.generate_descriptor("my unique phrase", "device123")` |
| `verify_descriptor(phrase, descriptor)` | Validates a phrase against a stored descriptor. | `client.verify_descriptor("my unique phrase", stored_descriptor)` |
| `export_keypair()` | Exports public/private keypair for API integration. | `pub, priv = client.export_keypair()` |
| `sign_message(message)` | Signs any string with private key (HMAC-SHA256). | `sig = client.sign_message("payload")` |
| `verify_signature(message, signature)` | Verifies a signed payload. | `client.verify_signature("payload", sig)` |

---

## FastAPI Server Endpoints

### Base URL
https://api.kindid.io/v1/

#### `POST /register`
Registers a new user descriptor.

**Request**
```json
{
  "username": "string",
  "phrase": "string",
  "device_id": "string"
}
