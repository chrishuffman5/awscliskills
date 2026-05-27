# Configuration

### 14.1 `put-default-encryption-configuration`

Sets the default encryption configuration for the AWS account in the current region.

**Synopsis:**
```bash
aws iotsitewise put-default-encryption-configuration \
    --encryption-type <value> \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--encryption-type` | **Yes** | string | -- | `SITEWISE_DEFAULT_ENCRYPTION` or `KMS_BASED_ENCRYPTION` |
| `--kms-key-id` | Conditional | string | None | KMS key ID (required for `KMS_BASED_ENCRYPTION`) |

**Output Schema:**
```json
{
    "encryptionType": "SITEWISE_DEFAULT_ENCRYPTION|KMS_BASED_ENCRYPTION",
    "kmsKeyArn": "string",
    "configurationStatus": {
        "state": "ACTIVE|UPDATE_IN_PROGRESS|UPDATE_FAILED",
        "error": {
            "code": "VALIDATION_ERROR|INTERNAL_FAILURE",
            "message": "string"
        }
    }
}
```

---

### 14.2 `describe-default-encryption-configuration`

Describes the default encryption configuration for the AWS account.

**Synopsis:**
```bash
aws iotsitewise describe-default-encryption-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "encryptionType": "SITEWISE_DEFAULT_ENCRYPTION|KMS_BASED_ENCRYPTION",
    "kmsKeyArn": "string",
    "configurationStatus": {
        "state": "ACTIVE|UPDATE_IN_PROGRESS|UPDATE_FAILED",
        "error": {}
    }
}
```

---

### 14.3 `put-storage-configuration`

Configures storage settings including hot tier, cold tier (S3), and warm tier.

**Synopsis:**
```bash
aws iotsitewise put-storage-configuration \
    --storage-type <value> \
    [--multi-layer-storage <value>] \
    [--disassociated-data-storage <value>] \
    [--retention-period <value>] \
    [--warm-tier <value>] \
    [--warm-tier-retention-period <value>] \
    [--disallow-ingest-null-nan | --no-disallow-ingest-null-nan] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--storage-type` | **Yes** | string | -- | `SITEWISE_DEFAULT_STORAGE` or `MULTI_LAYER_STORAGE` |
| `--multi-layer-storage` | Conditional | structure | None | S3 cold tier config (required for `MULTI_LAYER_STORAGE`) |
| `--disassociated-data-storage` | No | string | None | `ENABLED` or `DISABLED` |
| `--retention-period` | No | structure | None | Hot tier retention period |
| `--warm-tier` | No | string | None | `ENABLED` or `DISABLED` |
| `--warm-tier-retention-period` | No | structure | None | Warm tier retention period |
| `--disallow-ingest-null-nan` | No | boolean | false | Disallow NULL/NaN ingestion |

**Multi-Layer Storage Structure:**
```json
{
    "customerManagedS3Storage": {
        "s3ResourceArn": "string",
        "roleArn": "string"
    }
}
```

**Retention Period Structure:**
```json
{
    "numberOfDays": "integer",
    "unlimited": "boolean"
}
```

**Output Schema:**
```json
{
    "storageType": "SITEWISE_DEFAULT_STORAGE|MULTI_LAYER_STORAGE",
    "multiLayerStorage": {
        "customerManagedS3Storage": {
            "s3ResourceArn": "string",
            "roleArn": "string"
        }
    },
    "disassociatedDataStorage": "ENABLED|DISABLED",
    "retentionPeriod": {"numberOfDays": "integer", "unlimited": "boolean"},
    "configurationStatus": {
        "state": "ACTIVE|UPDATE_IN_PROGRESS|UPDATE_FAILED",
        "error": {}
    },
    "warmTier": "ENABLED|DISABLED",
    "warmTierRetentionPeriod": {"numberOfDays": "integer", "unlimited": "boolean"},
    "disallowIngestNullNaN": "boolean"
}
```

---

### 14.4 `describe-storage-configuration`

Describes the storage configuration.

**Synopsis:**
```bash
aws iotsitewise describe-storage-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "storageType": "SITEWISE_DEFAULT_STORAGE|MULTI_LAYER_STORAGE",
    "multiLayerStorage": {},
    "disassociatedDataStorage": "ENABLED|DISABLED",
    "retentionPeriod": {"numberOfDays": "integer", "unlimited": "boolean"},
    "configurationStatus": {"state": "string", "error": {}},
    "lastUpdateDate": "timestamp",
    "warmTier": "ENABLED|DISABLED",
    "warmTierRetentionPeriod": {},
    "disallowIngestNullNaN": "boolean"
}
```

---

### 14.5 `put-logging-options`

Sets the logging options for IoT SiteWise.

**Synopsis:**
```bash
aws iotsitewise put-logging-options \
    --logging-options <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--logging-options` | **Yes** | structure | -- | Logging configuration |

**Logging Options Structure:**
```json
{
    "level": "ERROR|WARN|INFO|DEBUG|DISABLED"
}
```

**Output:** None

---

### 14.6 `describe-logging-options`

Describes the logging options.

**Synopsis:**
```bash
aws iotsitewise describe-logging-options \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "loggingOptions": {
        "level": "ERROR|WARN|INFO|DEBUG|DISABLED"
    }
}
```
