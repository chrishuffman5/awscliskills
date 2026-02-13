# Resource Profiles

### 9.1 `get-resource-profile`

Retrieves the sensitivity profile for a resource (S3 bucket).

**Synopsis:**
```bash
aws macie2 get-resource-profile \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the S3 bucket resource |

**Output Schema:**
```json
{
    "profileUpdatedAt": "timestamp",
    "sensitivityScore": "integer",
    "sensitivityScoreOverridden": "boolean",
    "statistics": {
        "totalBytesClassified": "long",
        "totalDetections": "long",
        "totalDetectionsSuppressed": "long",
        "totalItemsClassified": "long",
        "totalItemsSensitive": "long",
        "totalItemsSkipped": "long",
        "totalItemsSkippedInvalidEncryption": "long",
        "totalItemsSkippedInvalidKms": "long",
        "totalItemsSkippedPermissionDenied": "long"
    }
}
```

---

### 9.2 `list-resource-profile-artifacts`

Lists the artifacts (S3 objects) that were analyzed during automated discovery for a resource. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-resource-profile-artifacts \
    --resource-arn <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the S3 bucket resource |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "artifacts": [
        {
            "arn": "string",
            "classificationResultStatus": "string",
            "sensitive": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.3 `list-resource-profile-detections`

Lists detections found during automated discovery for a resource. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-resource-profile-detections \
    --resource-arn <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the S3 bucket resource |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "detections": [
        {
            "arn": "string",
            "count": "long",
            "id": "string",
            "name": "string",
            "suppressed": "boolean",
            "type": "CUSTOM|MANAGED"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.4 `update-resource-profile`

Updates the sensitivity score for a resource.

**Synopsis:**
```bash
aws macie2 update-resource-profile \
    --resource-arn <value> \
    [--sensitivity-score-override <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the S3 bucket resource |
| `--sensitivity-score-override` | No | integer | None | Manually set sensitivity score (-1 to remove override) |

**Output:** None (HTTP 200 on success)

---

### 9.5 `update-resource-profile-detections`

Updates the sensitivity status (suppressed/unsuppressed) for detections in a resource profile.

**Synopsis:**
```bash
aws macie2 update-resource-profile-detections \
    --resource-arn <value> \
    [--suppress-data-identifiers <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the S3 bucket resource |
| `--suppress-data-identifiers` | No | list | None | Data identifiers to suppress/unsuppress |

**Suppress Data Identifiers Structure:**
```json
[
    {
        "id": "string",
        "type": "CUSTOM|MANAGED"
    }
]
```

**Output:** None (HTTP 200 on success)
