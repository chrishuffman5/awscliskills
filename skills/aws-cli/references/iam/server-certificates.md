# Server Certificates

### 13.1 `upload-server-certificate`

Uploads a server certificate entity (for use with ELB, CloudFront, etc.).

**Synopsis:**
```bash
aws iam upload-server-certificate \
    --server-certificate-name <value> \
    --certificate-body <value> \
    --private-key <value> \
    [--certificate-chain <value>] \
    [--path <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-certificate-name` | **Yes** | string | -- | Name (1-128 chars) |
| `--certificate-body` | **Yes** | string | -- | PEM-encoded certificate (1-16384 chars) |
| `--private-key` | **Yes** | string | -- | PEM-encoded private key (1-16384 chars) |
| `--certificate-chain` | No | string | None | PEM-encoded CA chain (1-2097152 chars) |
| `--path` | No | string | `/` | Path prefix |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "ServerCertificateMetadata": {
        "Path": "string",
        "ServerCertificateName": "string",
        "ServerCertificateId": "string",
        "Arn": "string",
        "UploadDate": "timestamp",
        "Expiration": "timestamp"
    },
    "Tags": [{ "Key": "string", "Value": "string" }]
}
```

---

### 13.2 `get-server-certificate`

Retrieves a server certificate including the certificate body.

**Synopsis:**
```bash
aws iam get-server-certificate --server-certificate-name <value>
```

**Output Schema:**
```json
{
    "ServerCertificate": {
        "ServerCertificateMetadata": {
            "Path": "string",
            "ServerCertificateName": "string",
            "ServerCertificateId": "string",
            "Arn": "string",
            "UploadDate": "timestamp",
            "Expiration": "timestamp"
        },
        "CertificateBody": "string",
        "CertificateChain": "string",
        "Tags": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 13.3 `list-server-certificates`

Lists server certificates. **Paginated.**

**Synopsis:**
```bash
aws iam list-server-certificates [--path-prefix <value>] [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "ServerCertificateMetadataList": [
        {
            "Path": "string",
            "ServerCertificateName": "string",
            "ServerCertificateId": "string",
            "Arn": "string",
            "UploadDate": "timestamp",
            "Expiration": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 13.4 `update-server-certificate`

Changes the name and/or path of a server certificate.

**Synopsis:**
```bash
aws iam update-server-certificate --server-certificate-name <value> [--new-server-certificate-name <value>] [--new-path <value>]
```

**Output:** None on success.

---

### 13.5 `delete-server-certificate`

Deletes a server certificate.

**Synopsis:**
```bash
aws iam delete-server-certificate --server-certificate-name <value>
```

**Output:** None on success.

---
