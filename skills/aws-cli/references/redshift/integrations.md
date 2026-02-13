# Integrations

### 8.1 `create-integration`

Creates a zero-ETL integration with another AWS service (e.g., Aurora to Redshift).

**Synopsis:**
```bash
aws redshift create-integration \
    --source-arn <value> \
    --target-arn <value> \
    --integration-name <value> \
    [--kms-key-id <value>] \
    [--tag-list <value>] \
    [--additional-encryption-context <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-arn` | **Yes** | string | -- | Source ARN (e.g., Aurora cluster ARN) |
| `--target-arn` | **Yes** | string | -- | Target Redshift namespace ARN |
| `--integration-name` | **Yes** | string | -- | Name for the integration |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--tag-list` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--additional-encryption-context` | No | map | -- | Additional encryption context key-value pairs |
| `--description` | No | string | -- | Description |

**Output Schema:**
```json
{
    "IntegrationArn": "string",
    "IntegrationName": "string",
    "SourceArn": "string",
    "TargetArn": "string",
    "Status": "creating|active|modifying|failed|deleting|syncing|needs_attention",
    "Errors": [
        {
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ],
    "CreateTime": "timestamp",
    "Description": "string",
    "KMSKeyId": "string",
    "AdditionalEncryptionContext": {"string": "string"},
    "Tags": [{"Key": "string", "Value": "string"}]
}
```

---

### 8.2 `delete-integration`

Deletes a zero-ETL integration.

**Synopsis:**
```bash
aws redshift delete-integration \
    --integration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-arn` | **Yes** | string | -- | Integration ARN to delete |

**Output Schema:**
```json
{
    "IntegrationArn": "string",
    "IntegrationName": "string",
    "SourceArn": "string",
    "TargetArn": "string",
    "Status": "deleting"
}
```

---

### 8.3 `describe-integrations`

Describes zero-ETL integrations. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-integrations \
    [--integration-arn <value>] \
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
| `--integration-arn` | No | string | -- | Specific integration ARN |
| `--filters` | No | list | -- | Filters. Shorthand: `Name=integration-arn\|source-arn\|target-arn\|status,Values=string,string ...` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Integrations": [
        {
            "IntegrationArn": "string",
            "IntegrationName": "string",
            "SourceArn": "string",
            "TargetArn": "string",
            "Status": "string",
            "Errors": [],
            "CreateTime": "timestamp",
            "Description": "string",
            "KMSKeyId": "string",
            "Tags": []
        }
    ],
    "Marker": "string"
}
```

---

### 8.4 `modify-integration`

Modifies a zero-ETL integration.

**Synopsis:**
```bash
aws redshift modify-integration \
    --integration-arn <value> \
    [--integration-name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-arn` | **Yes** | string | -- | Integration ARN to modify |
| `--integration-name` | No | string | -- | New name |
| `--description` | No | string | -- | New description |

**Output Schema:**
```json
{
    "IntegrationArn": "string",
    "IntegrationName": "string",
    "SourceArn": "string",
    "TargetArn": "string",
    "Status": "string",
    "CreateTime": "timestamp",
    "Description": "string"
}
```
