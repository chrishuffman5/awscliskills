# Adapters

### 3.1 `create-adapter`

Creates a custom adapter for fine-tuning document analysis on specific document types.

**Synopsis:**
```bash
aws textract create-adapter \
    --adapter-name <value> \
    --feature-types <value> \
    [--client-request-token <value>] \
    [--description <value>] \
    [--auto-update <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--adapter-name` | **Yes** | string | -- | Adapter name (1-128 chars, pattern: `[a-zA-Z0-9-_]+`) |
| `--feature-types` | **Yes** | list(string) | -- | Feature types: `TABLES`, `FORMS`, `QUERIES`, `SIGNATURES`, `LAYOUT` |
| `--client-request-token` | No | string | None | Idempotent token (1-64 chars) |
| `--description` | No | string | None | Adapter description (1-256 chars) |
| `--auto-update` | No | string | `DISABLED` | Auto-update control: `ENABLED`, `DISABLED` |
| `--tags` | No | map | None | Key-value tags (max 200 tags) |

**Output Schema:**
```json
{
    "AdapterId": "string (12-1011 chars)"
}
```

---

### 3.2 `create-adapter-version`

Creates a new version of an adapter by training it with a labeled dataset.

**Synopsis:**
```bash
aws textract create-adapter-version \
    --adapter-id <value> \
    --dataset-config <value> \
    --output-config <value> \
    [--client-request-token <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--adapter-id` | **Yes** | string | -- | Adapter ID to create a version for (12-1011 chars) |
| `--dataset-config` | **Yes** | structure | -- | Training dataset configuration |
| `--output-config` | **Yes** | structure | -- | S3 bucket for training output |
| `--client-request-token` | No | string | None | Idempotent token (1-64 chars) |
| `--kms-key-id` | No | string | None | KMS key for encryption (1-2048 chars) |
| `--tags` | No | map | None | Key-value tags (max 200 tags) |

**DatasetConfig Structure:**
```json
{
    "ManifestS3Object": {
        "Bucket": "string (3-255 chars)",
        "Name": "string (1-1024 chars)",
        "Version": "string (1-1024 chars, optional)"
    }
}
```

**OutputConfig Structure:**
```json
{
    "S3Bucket": "string (3-255 chars)",
    "S3Prefix": "string (1-1024 chars, optional)"
}
```

**Output Schema:**
```json
{
    "AdapterId": "string (12-1011 chars)",
    "AdapterVersion": "string (1-128 chars)"
}
```

---

### 3.3 `delete-adapter`

Deletes an adapter. All versions of the adapter are also deleted.

**Synopsis:**
```bash
aws textract delete-adapter \
    --adapter-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--adapter-id` | **Yes** | string | -- | Adapter ID to delete (12-1011 chars) |

**Output:** None

---

### 3.4 `delete-adapter-version`

Deletes a specific version of an adapter.

**Synopsis:**
```bash
aws textract delete-adapter-version \
    --adapter-id <value> \
    --adapter-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--adapter-id` | **Yes** | string | -- | Adapter ID (12-1011 chars) |
| `--adapter-version` | **Yes** | string | -- | Adapter version to delete (1-128 chars) |

**Output:** None

---

### 3.5 `get-adapter`

Gets information about a specific adapter.

**Synopsis:**
```bash
aws textract get-adapter \
    --adapter-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--adapter-id` | **Yes** | string | -- | Adapter ID (12-1011 chars) |

**Output Schema:**
```json
{
    "AdapterId": "string",
    "AdapterName": "string",
    "CreationTime": "timestamp",
    "Description": "string",
    "FeatureTypes": ["TABLES|FORMS|QUERIES|SIGNATURES|LAYOUT"],
    "AutoUpdate": "ENABLED|DISABLED",
    "Tags": {
        "key": "value"
    }
}
```

---

### 3.6 `get-adapter-version`

Gets information about a specific adapter version, including training metrics.

**Synopsis:**
```bash
aws textract get-adapter-version \
    --adapter-id <value> \
    --adapter-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--adapter-id` | **Yes** | string | -- | Adapter ID (12-1011 chars) |
| `--adapter-version` | **Yes** | string | -- | Adapter version (1-128 chars) |

**Output Schema:**
```json
{
    "AdapterId": "string",
    "AdapterVersion": "string",
    "CreationTime": "timestamp",
    "FeatureTypes": ["TABLES|FORMS|QUERIES|SIGNATURES|LAYOUT"],
    "Status": "ACTIVE|AT_RISK|DEPRECATED|CREATION_ERROR|CREATION_IN_PROGRESS",
    "StatusMessage": "string",
    "DatasetConfig": {
        "ManifestS3Object": {
            "Bucket": "string",
            "Name": "string",
            "Version": "string"
        }
    },
    "KMSKeyId": "string",
    "OutputConfig": {
        "S3Bucket": "string",
        "S3Prefix": "string"
    },
    "EvaluationMetrics": [
        {
            "Baseline": {
                "F1Score": "float",
                "Precision": "float",
                "Recall": "float"
            },
            "AdapterVersion": {
                "F1Score": "float",
                "Precision": "float",
                "Recall": "float"
            },
            "FeatureType": "TABLES|FORMS|QUERIES|SIGNATURES|LAYOUT"
        }
    ],
    "Tags": {
        "key": "value"
    }
}
```

---

### 3.7 `list-adapters`

Lists all adapters that match the specified criteria. **Paginated operation.**

**Synopsis:**
```bash
aws textract list-adapters \
    [--after-creation-time <value>] \
    [--before-creation-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--after-creation-time` | No | timestamp | None | Only return adapters created after this time |
| `--before-creation-time` | No | timestamp | None | Only return adapters created before this time |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Adapters": [
        {
            "AdapterId": "string",
            "AdapterName": "string",
            "CreationTime": "timestamp",
            "FeatureTypes": ["TABLES|FORMS|QUERIES|SIGNATURES|LAYOUT"]
        }
    ],
    "NextToken": "string"
}
```

---

### 3.8 `list-adapter-versions`

Lists all versions of adapters, optionally filtered by adapter ID. **Paginated operation.**

**Synopsis:**
```bash
aws textract list-adapter-versions \
    [--adapter-id <value>] \
    [--after-creation-time <value>] \
    [--before-creation-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--adapter-id` | No | string | None | Filter by adapter ID (12-1011 chars) |
| `--after-creation-time` | No | timestamp | None | Only return versions created after this time |
| `--before-creation-time` | No | timestamp | None | Only return versions created before this time |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AdapterVersions": [
        {
            "AdapterId": "string",
            "AdapterVersion": "string",
            "CreationTime": "timestamp",
            "FeatureTypes": ["TABLES|FORMS|QUERIES|SIGNATURES|LAYOUT"],
            "Status": "ACTIVE|AT_RISK|DEPRECATED|CREATION_ERROR|CREATION_IN_PROGRESS",
            "StatusMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.9 `update-adapter`

Updates the name, description, or auto-update setting of an adapter. Feature types cannot be changed.

**Synopsis:**
```bash
aws textract update-adapter \
    --adapter-id <value> \
    [--description <value>] \
    [--adapter-name <value>] \
    [--auto-update <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--adapter-id` | **Yes** | string | -- | Adapter ID to update (12-1011 chars) |
| `--description` | No | string | None | New description (1-256 chars) |
| `--adapter-name` | No | string | None | New name (1-128 chars, pattern: `[a-zA-Z0-9-_]+`) |
| `--auto-update` | No | string | None | Auto-update: `ENABLED`, `DISABLED` |

**Output Schema:**
```json
{
    "AdapterId": "string",
    "AdapterName": "string",
    "CreationTime": "timestamp",
    "Description": "string",
    "FeatureTypes": ["TABLES|FORMS|QUERIES|SIGNATURES|LAYOUT"],
    "AutoUpdate": "ENABLED|DISABLED"
}
```
