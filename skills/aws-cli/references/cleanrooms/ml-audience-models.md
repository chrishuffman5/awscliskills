# ML Audience Models

> Commands in this file use the `aws cleanroomsml` namespace.

## 10.1 `create-audience-model`

Creates an audience model from a training dataset.

**Synopsis:**
```bash
aws cleanroomsml create-audience-model \
    --name <value> \
    --training-data-arn <value> \
    [--description <value>] \
    [--kms-key-arn <value>] \
    [--training-data-start-time <value>] \
    [--training-data-end-time <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Audience model name |
| `--training-data-arn` | **Yes** | string | -- | Training dataset ARN |
| `--description` | No | string | None | Description |
| `--kms-key-arn` | No | string | None | KMS key for encryption |
| `--training-data-start-time` | No | timestamp | None | Training data start time filter |
| `--training-data-end-time` | No | timestamp | None | Training data end time filter |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "audienceModelArn": "string"
}
```

---

## 10.2 `delete-audience-model`

Deletes an audience model.

**Synopsis:**
```bash
aws cleanroomsml delete-audience-model \
    --audience-model-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--audience-model-arn` | **Yes** | string | -- | Audience model ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 10.3 `get-audience-model`

Returns details for an audience model.

**Synopsis:**
```bash
aws cleanroomsml get-audience-model \
    --audience-model-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--audience-model-arn` | **Yes** | string | -- | Audience model ARN |

**Output Schema:**
```json
{
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "trainingDataStartTime": "timestamp",
    "trainingDataEndTime": "timestamp",
    "audienceModelArn": "string",
    "name": "string",
    "trainingDatasetArn": "string",
    "status": "CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE|DELETE_PENDING|DELETE_IN_PROGRESS|DELETE_FAILED",
    "statusDetails": {
        "statusCode": "string",
        "message": "string"
    },
    "kmsKeyArn": "string",
    "tags": { "string": "string" },
    "description": "string"
}
```

---

## 10.4 `list-audience-models`

Lists audience models. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-audience-models \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "audienceModels": [
        {
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "audienceModelArn": "string",
            "name": "string",
            "trainingDatasetArn": "string",
            "status": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 10.5 `create-configured-audience-model`

Creates a configured audience model that defines how to generate audiences.

**Synopsis:**
```bash
aws cleanroomsml create-configured-audience-model \
    --name <value> \
    --audience-model-arn <value> \
    --output-config <value> \
    --shared-audience-metrics <value> \
    [--description <value>] \
    [--min-matching-seed-size <value>] \
    [--audience-size-config <value>] \
    [--child-resource-tag-on-create-policy <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name |
| `--audience-model-arn` | **Yes** | string | -- | Audience model ARN |
| `--output-config` | **Yes** | structure | -- | Output configuration (S3 destination) |
| `--shared-audience-metrics` | **Yes** | list(string) | -- | Shared metrics: `ALL`, `NONE` |
| `--description` | No | string | None | Description |
| `--min-matching-seed-size` | No | integer | None | Minimum seed audience size |
| `--audience-size-config` | No | structure | None | Audience size configuration |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "configuredAudienceModelArn": "string"
}
```

---

## 10.6 `delete-configured-audience-model`

Deletes a configured audience model.

**Synopsis:**
```bash
aws cleanroomsml delete-configured-audience-model \
    --configured-audience-model-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-audience-model-arn` | **Yes** | string | -- | Configured audience model ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 10.7 `get-configured-audience-model`

Returns details for a configured audience model.

**Synopsis:**
```bash
aws cleanroomsml get-configured-audience-model \
    --configured-audience-model-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-audience-model-arn` | **Yes** | string | -- | Configured audience model ARN |

**Output Schema:**
```json
{
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "configuredAudienceModelArn": "string",
    "name": "string",
    "audienceModelArn": "string",
    "outputConfig": {
        "destination": {
            "s3Destination": {
                "s3Uri": "string"
            }
        },
        "roleArn": "string"
    },
    "description": "string",
    "status": "ACTIVE",
    "sharedAudienceMetrics": ["string"],
    "minMatchingSeedSize": "integer",
    "audienceSizeConfig": {
        "audienceSizeType": "ABSOLUTE|PERCENTAGE",
        "audienceSizeBins": ["integer"]
    },
    "tags": { "string": "string" },
    "childResourceTagOnCreatePolicy": "FROM_PARENT_RESOURCE|NONE"
}
```

---

## 10.8 `list-configured-audience-models`

Lists configured audience models. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-configured-audience-models \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "configuredAudienceModels": [
        {
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "name": "string",
            "audienceModelArn": "string",
            "outputConfig": {},
            "description": "string",
            "configuredAudienceModelArn": "string",
            "status": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 10.9 `update-configured-audience-model`

Updates a configured audience model.

**Synopsis:**
```bash
aws cleanroomsml update-configured-audience-model \
    --configured-audience-model-arn <value> \
    [--output-config <value>] \
    [--audience-model-arn <value>] \
    [--shared-audience-metrics <value>] \
    [--min-matching-seed-size <value>] \
    [--audience-size-config <value>] \
    [--description <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-audience-model-arn` | **Yes** | string | -- | Configured audience model ARN |
| `--output-config` | No | structure | None | Updated output configuration |
| `--audience-model-arn` | No | string | None | Updated audience model ARN |
| `--shared-audience-metrics` | No | list(string) | None | Updated shared metrics |
| `--min-matching-seed-size` | No | integer | None | Updated minimum seed size |
| `--audience-size-config` | No | structure | None | Updated audience size config |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "configuredAudienceModelArn": "string"
}
```
