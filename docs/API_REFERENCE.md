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

**Response**

{
  "status": "success",
  "descriptor_id": "UUID",
  "message": "Descriptor created successfully."
}

POST /verify

Validates a user login attempt.

Request

{
  "username": "string",
  "phrase": "string"
}


Response

{
  "status": "verified",
  "confidence": 0.9992,
  "timestamp": "2025-10-24T00:00:00Z"
}

GET /health

Health check endpoint. Returns server operational metrics.

Response

{
  "status": "ok",
  "version": "1.0.0",
  "uptime": "48h"
}

Error Codes
Code	Meaning	Example
400	Missing or invalid parameters	"Missing field: phrase"
401	Unauthorized access	"Descriptor not verified"
429	Rate limited	"Too many attempts"
500	Internal error	"Unexpected exception"
Webhook Integration
Event	Description
descriptor.created	Triggered when a new identity is registered.
descriptor.verified	Triggered upon successful login validation.
descriptor.failed	Triggered when verification fails.

Example payload:

{
  "event": "descriptor.verified",
  "user": "username",
  "timestamp": "2025-10-24T00:00:00Z",
  "confidence": 0.998
}

Response Metadata

All responses contain:

{
  "meta": {
    "api_version": "1.0.0",
    "server_time": "UTC timestamp",
    "request_id": "uuid"
  }
}

Rate Limits

Default limit: 60 requests/minute per IP.
Exceeded requests return HTTP 429.

Changelog Reference

See CHANGELOG.md
 for updates.

© 2025 KIND-ID Project. MIT License.
'@
