# Signing Certificates

### 11.1 `upload-signing-certificate`

Uploads an X.509 signing certificate.

**Synopsis:**
```bash
aws iam upload-signing-certificate --certificate-body <value> [--user-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-body` | **Yes** | string | -- | PEM-encoded certificate (1-16384 chars) |
| `--user-name` | No | string | caller | User name |

**Output Schema:**
```json
{
    "Certificate": {
        "UserName": "string",
        "CertificateId": "string",
        "CertificateBody": "string",
        "Status": "Active|Inactive",
        "UploadDate": "timestamp"
    }
}
```

---

### 11.2 `list-signing-certificates`

Lists signing certificates for a user. **Paginated.**

**Synopsis:**
```bash
aws iam list-signing-certificates [--user-name <value>] [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "Certificates": [
        {
            "UserName": "string",
            "CertificateId": "string",
            "CertificateBody": "string",
            "Status": "Active|Inactive",
            "UploadDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 11.3 `update-signing-certificate`

Changes the status of a signing certificate (Active/Inactive).

**Synopsis:**
```bash
aws iam update-signing-certificate --certificate-id <value> --status <value> [--user-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID (24 chars) |
| `--status` | **Yes** | string | -- | `Active` or `Inactive` |

**Output:** None on success.

---

### 11.4 `delete-signing-certificate`

Deletes a signing certificate.

**Synopsis:**
```bash
aws iam delete-signing-certificate --certificate-id <value> [--user-name <value>]
```

**Output:** None on success.

---
