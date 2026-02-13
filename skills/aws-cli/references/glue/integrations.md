# Integrations

### 16.1 `create-integration`

Creates a zero-ETL integration.

**Synopsis:**
```bash
aws glue create-integration \
    --integration-name <value> \
    --source-arn <value> \
    --target-arn <value> \
    [--description <value>] \
    [--data-filter <value>] \
    [--kms-key-id <value>] \
    [--additional-encryption-context <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-name` | **Yes** | string | -- | Integration name |
| `--source-arn` | **Yes** | string | -- | Source resource ARN |
| `--target-arn` | **Yes** | string | -- | Target resource ARN |
| `--description` | No | string | -- | Description |
| `--data-filter` | No | string | -- | Data filter expression |
| `--kms-key-id` | No | string | -- | KMS key ID for encryption |
| `--additional-encryption-context` | No | map | -- | Additional encryption context |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "SourceArn": "string",
    "TargetArn": "string",
    "IntegrationName": "string",
    "Description": "string",
    "IntegrationArn": "string",
    "KmsKeyId": "string",
    "AdditionalEncryptionContext": {},
    "Tags": [],
    "Status": "CREATING|ACTIVE|MODIFYING|FAILED|DELETING|SYNCING|NEEDS_ATTENTION",
    "CreateTime": "timestamp",
    "Errors": [],
    "DataFilter": "string"
}
```

---

### 16.2 `delete-integration`

Deletes a zero-ETL integration.

**Synopsis:**
```bash
aws glue delete-integration \
    --integration-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-identifier` | **Yes** | string | -- | Integration ARN |

**Output Schema:**
```json
{
    "SourceArn": "string",
    "TargetArn": "string",
    "IntegrationName": "string",
    "IntegrationArn": "string",
    "Status": "DELETING",
    "CreateTime": "timestamp"
}
```

---

### 16.3 `get-integration`

Retrieves integration details.

**Synopsis:**
```bash
aws glue get-integration \
    --integration-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-identifier` | **Yes** | string | -- | Integration ARN |

**Output Schema:**
```json
{
    "SourceArn": "string",
    "TargetArn": "string",
    "IntegrationName": "string",
    "Description": "string",
    "IntegrationArn": "string",
    "KmsKeyId": "string",
    "AdditionalEncryptionContext": {},
    "Tags": [],
    "Status": "CREATING|ACTIVE|MODIFYING|FAILED|DELETING|SYNCING|NEEDS_ATTENTION",
    "CreateTime": "timestamp",
    "Errors": [],
    "DataFilter": "string"
}
```

---

### 16.4 `describe-integrations`

Lists integrations. **Paginated operation.**

**Synopsis:**
```bash
aws glue describe-integrations \
    [--integration-identifier <value>] \
    [--marker <value>] \
    [--max-records <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-identifier` | No | string | -- | Filter by integration ARN |
| `--marker` | No | string | -- | Pagination token |
| `--max-records` | No | integer | -- | Maximum results |
| `--filters` | No | list | -- | Filters (JSON) |

**Output Schema:**
```json
{
    "Integrations": ["<Integration structure>"],
    "Marker": "string"
}
```

---

### 16.5 `modify-integration`

Modifies a zero-ETL integration.

**Synopsis:**
```bash
aws glue modify-integration \
    --integration-identifier <value> \
    [--description <value>] \
    [--data-filter <value>] \
    [--integration-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-identifier` | **Yes** | string | -- | Integration ARN |
| `--description` | No | string | -- | Updated description |
| `--data-filter` | No | string | -- | Updated data filter |
| `--integration-name` | No | string | -- | Updated name |

**Output Schema:**
```json
{
    "SourceArn": "string",
    "TargetArn": "string",
    "IntegrationName": "string",
    "IntegrationArn": "string",
    "Status": "string",
    "CreateTime": "timestamp"
}
```

---

### 16.6 `create-integration-resource-property`

Creates integration resource properties.

**Synopsis:**
```bash
aws glue create-integration-resource-property \
    --resource-arn <value> \
    [--source-processing-properties <value>] \
    [--target-processing-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--source-processing-properties` | No | structure | -- | Source processing config (JSON) |
| `--target-processing-properties` | No | structure | -- | Target processing config (JSON) |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "SourceProcessingProperties": {},
    "TargetProcessingProperties": {}
}
```

---

### 16.7 `get-integration-resource-property`

Retrieves integration resource properties.

**Synopsis:**
```bash
aws glue get-integration-resource-property \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "SourceProcessingProperties": {},
    "TargetProcessingProperties": {}
}
```

---

### 16.8 `update-integration-resource-property`

Updates integration resource properties.

**Synopsis:**
```bash
aws glue update-integration-resource-property \
    --resource-arn <value> \
    [--source-processing-properties <value>] \
    [--target-processing-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--source-processing-properties` | No | structure | -- | Updated source processing config |
| `--target-processing-properties` | No | structure | -- | Updated target processing config |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "SourceProcessingProperties": {},
    "TargetProcessingProperties": {}
}
```

---

### 16.9 `create-integration-table-properties`

Creates integration table properties.

**Synopsis:**
```bash
aws glue create-integration-table-properties \
    --resource-arn <value> \
    --table-name <value> \
    [--source-table-config <value>] \
    [--target-table-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--table-name` | **Yes** | string | -- | Table name |
| `--source-table-config` | No | structure | -- | Source table config (JSON) |
| `--target-table-config` | No | structure | -- | Target table config (JSON) |

No output on success.

---

### 16.10 `get-integration-table-properties`

Retrieves integration table properties.

**Synopsis:**
```bash
aws glue get-integration-table-properties \
    --resource-arn <value> \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--table-name` | **Yes** | string | -- | Table name |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "TableName": "string",
    "SourceTableConfig": {},
    "TargetTableConfig": {}
}
```

---

### 16.11 `update-integration-table-properties`

Updates integration table properties.

**Synopsis:**
```bash
aws glue update-integration-table-properties \
    --resource-arn <value> \
    --table-name <value> \
    [--source-table-config <value>] \
    [--target-table-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--table-name` | **Yes** | string | -- | Table name |
| `--source-table-config` | No | structure | -- | Updated source table config |
| `--target-table-config` | No | structure | -- | Updated target table config |

No output on success.

---

### 16.12 `describe-inbound-integrations`

Describes inbound integrations for a target resource.

**Synopsis:**
```bash
aws glue describe-inbound-integrations \
    [--integration-arn <value>] \
    [--target-arn <value>] \
    [--marker <value>] \
    [--max-records <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-arn` | No | string | -- | Filter by integration ARN |
| `--target-arn` | No | string | -- | Filter by target ARN |
| `--marker` | No | string | -- | Pagination token |
| `--max-records` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "InboundIntegrations": [
        {
            "SourceArn": "string",
            "TargetArn": "string",
            "IntegrationArn": "string",
            "Status": "CREATING|ACTIVE|MODIFYING|FAILED|DELETING|SYNCING|NEEDS_ATTENTION",
            "CreateTime": "timestamp",
            "Errors": []
        }
    ],
    "Marker": "string"
}
```
