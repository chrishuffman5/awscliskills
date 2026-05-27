# Schemas & Certificates

### 11.1 `describe-schemas`

Returns information about the schema for the specified endpoint. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-schemas \
    --endpoint-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "Schemas": ["string"]
}
```

---

### 11.2 `refresh-schemas`

Populates the schema for the specified endpoint by refreshing it from the source database.

**Synopsis:**
```bash
aws dms refresh-schemas \
    --endpoint-arn <value> \
    --replication-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint |
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance |

**Output Schema:**
```json
{
    "RefreshSchemasStatus": {
        "EndpointArn": "string",
        "ReplicationInstanceArn": "string",
        "Status": "successful|failed|refreshing",
        "LastRefreshDate": "timestamp",
        "LastFailureMessage": "string"
    }
}
```

---

### 11.3 `describe-refresh-schemas-status`

Returns the status of the RefreshSchemas operation.

**Synopsis:**
```bash
aws dms describe-refresh-schemas-status \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint |

**Output Schema:**
```json
{
    "RefreshSchemasStatus": {
        "EndpointArn": "string",
        "ReplicationInstanceArn": "string",
        "Status": "successful|failed|refreshing",
        "LastRefreshDate": "timestamp",
        "LastFailureMessage": "string"
    }
}
```

---

### 11.4 `import-certificate`

Uploads the specified certificate.

**Synopsis:**
```bash
aws dms import-certificate \
    --certificate-identifier <value> \
    [--certificate-pem <value>] \
    [--certificate-wallet <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-identifier` | **Yes** | string | -- | Certificate identifier |
| `--certificate-pem` | No | string | -- | PEM-encoded certificate (use this or `--certificate-wallet`) |
| `--certificate-wallet` | No | blob | -- | Binary certificate wallet (use this or `--certificate-pem`) |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "Certificate": {
        "CertificateIdentifier": "string",
        "CertificateCreationDate": "timestamp",
        "CertificatePem": "string",
        "CertificateWallet": "blob",
        "CertificateArn": "string",
        "CertificateOwner": "string",
        "ValidFromDate": "timestamp",
        "ValidToDate": "timestamp",
        "SigningAlgorithm": "string",
        "KeyLength": "integer"
    }
}
```

---

### 11.5 `delete-certificate`

Deletes the specified certificate.

**Synopsis:**
```bash
aws dms delete-certificate \
    --certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate to delete |

**Output Schema:** Same as `import-certificate`.

---

### 11.6 `describe-certificates`

Provides a description of the certificate. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-certificates \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `certificate-arn`, `certificate-id` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "Certificates": [
        {
            "CertificateIdentifier": "string",
            "CertificateCreationDate": "timestamp",
            "CertificatePem": "string",
            "CertificateWallet": "blob",
            "CertificateArn": "string",
            "CertificateOwner": "string",
            "ValidFromDate": "timestamp",
            "ValidToDate": "timestamp",
            "SigningAlgorithm": "string",
            "KeyLength": "integer"
        }
    ]
}
```
