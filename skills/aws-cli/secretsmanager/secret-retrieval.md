# Secret Retrieval

### 2.1 `get-secret-value`

Retrieves the encrypted value of a secret. Returns either `SecretString` or `SecretBinary`.

**Synopsis:**
```bash
aws secretsmanager get-secret-value \
    --secret-id <value> \
    [--version-id <value>] \
    [--version-stage <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--version-id` | No | string | None | UUID of the specific version to retrieve (32-64 chars) |
| `--version-stage` | No | string | `AWSCURRENT` | Staging label: `AWSCURRENT`, `AWSPREVIOUS`, `AWSPENDING`, or custom (1-256 chars) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "VersionId": "string",
    "SecretBinary": "blob",
    "SecretString": "string",
    "VersionStages": ["string"],
    "CreatedDate": "timestamp"
}
```

---

### 2.2 `batch-get-secret-value`

Retrieves multiple secret values in a single call. Must specify either `--secret-id-list` or `--filters`, not both.

**Synopsis:**
```bash
aws secretsmanager batch-get-secret-value \
    [--secret-id-list <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id-list` | Conditional | list(string) | None | ARNs or names of secrets (1-20 items, each 1-2048 chars). Cannot combine with `--filters` |
| `--filters` | Conditional | list | None | Filters for selecting secrets (max 10). Cannot combine with `--secret-id-list` |
| `--max-results` | No | integer | 20 | Number of results per response (1-20) |
| `--next-token` | No | string | None | Pagination token (1-4096 chars) |

**Filter Structure:**
```json
[
    {
        "Key": "description|name|tag-key|tag-value|primary-region|owning-service|all",
        "Values": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "SecretValues": [
        {
            "ARN": "string",
            "Name": "string",
            "VersionId": "string",
            "SecretString": "string",
            "SecretBinary": "blob",
            "VersionStages": ["string"],
            "CreatedDate": "timestamp"
        }
    ],
    "NextToken": "string",
    "Errors": [
        {
            "SecretId": "string",
            "ErrorCode": "string",
            "Message": "string"
        }
    ]
}
```

---
