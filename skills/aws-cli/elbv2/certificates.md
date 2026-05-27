# Certificates

### 5.1 `add-listener-certificates`

Adds the specified SSL server certificate to the certificate list for the specified HTTPS or TLS listener. Up to 25 additional certificates per listener.

**Synopsis:**
```bash
aws elbv2 add-listener-certificates \
    --listener-arn <value> \
    --certificates <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--certificates` | **Yes** | list | -- | Certificates to add. Shorthand: `CertificateArn=string ...` |

**Output Schema:**
```json
{
    "Certificates": [
        {
            "CertificateArn": "string",
            "IsDefault": true|false
        }
    ]
}
```

---

### 5.2 `remove-listener-certificates`

Removes the specified certificate from the certificate list for the specified HTTPS or TLS listener. Cannot remove the default certificate.

**Synopsis:**
```bash
aws elbv2 remove-listener-certificates \
    --listener-arn <value> \
    --certificates <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--certificates` | **Yes** | list | -- | Certificates to remove. Shorthand: `CertificateArn=string ...` |

**Output Schema:** None (no output on success).

---

### 5.3 `describe-listener-certificates`

Describes the default certificate and the certificate list for the specified HTTPS or TLS listener. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-listener-certificates \
    --listener-arn <value> \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Certificates": [
        {
            "CertificateArn": "string",
            "IsDefault": true|false
        }
    ],
    "NextMarker": "string"
}
```

---
