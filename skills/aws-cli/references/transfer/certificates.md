# Certificates

Commands for managing AS2 certificates in Transfer Family.

### 9.1 `import-certificate`

Imports a certificate for use with AS2 profiles and agreements.

**Synopsis:**
```bash
aws transfer import-certificate \
    --usage <value> \
    --certificate <value> \
    [--certificate-chain <value>] \
    [--private-key <value>] \
    [--active-date <value>] \
    [--inactive-date <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage` | **Yes** | string | -- | Usage: `SIGNING`, `ENCRYPTION`, or `TLS` |
| `--certificate` | **Yes** | string | -- | Certificate content or file path (max 16384 chars) |
| `--certificate-chain` | No | string | None | Certificate chain (max 2097152 chars) |
| `--private-key` | No | string | None | Private key content (max 16384 chars) |
| `--active-date` | No | timestamp | None | Date certificate becomes active |
| `--inactive-date` | No | timestamp | None | Date certificate becomes inactive |
| `--description` | No | string | None | Description (1-200 chars) |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "CertificateId": "string"
}
```

---

### 9.2 `delete-certificate`

Deletes a certificate.

**Synopsis:**
```bash
aws transfer delete-certificate \
    --certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |

**Output:** None on success.

---

### 9.3 `describe-certificate`

Gets details about a certificate.

**Synopsis:**
```bash
aws transfer describe-certificate \
    --certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |

**Output Schema:**
```json
{
    "Certificate": {
        "Arn": "string",
        "CertificateId": "string",
        "Usage": "SIGNING|ENCRYPTION|TLS",
        "Status": "ACTIVE|PENDING_ROTATION|INACTIVE",
        "Certificate": "string",
        "CertificateChain": "string",
        "ActiveDate": "timestamp",
        "InactiveDate": "timestamp",
        "Serial": "string",
        "NotBeforeDate": "timestamp",
        "NotAfterDate": "timestamp",
        "Type": "CERTIFICATE|CERTIFICATE_WITH_PRIVATE_KEY",
        "Description": "string",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 9.4 `list-certificates`

Lists certificates. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-certificates \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "Certificates": [
        {
            "Arn": "string",
            "CertificateId": "string",
            "Usage": "SIGNING|ENCRYPTION|TLS",
            "Status": "ACTIVE|PENDING_ROTATION|INACTIVE",
            "ActiveDate": "timestamp",
            "InactiveDate": "timestamp",
            "Type": "CERTIFICATE|CERTIFICATE_WITH_PRIVATE_KEY",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `update-certificate`

Updates a certificate's active/inactive dates and description.

**Synopsis:**
```bash
aws transfer update-certificate \
    --certificate-id <value> \
    [--active-date <value>] \
    [--inactive-date <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |
| `--active-date` | No | timestamp | None | New active date |
| `--inactive-date` | No | timestamp | None | New inactive date |
| `--description` | No | string | None | New description |

**Output Schema:**
```json
{
    "CertificateId": "string"
}
```
