# Provisioned Throughput

### `create-provisioned-model-throughput`

Creates dedicated throughput for a base or custom model with a specified number of model units.

**Synopsis:**
```bash
aws bedrock create-provisioned-model-throughput \
    --provisioned-model-name <value> \
    --model-id <value> \
    --model-units <value> \
    [--client-request-token <value>] \
    [--commitment-duration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-model-name` | **Yes** | string | -- | Name for the provisioned throughput (1-63 chars). Pattern: `([0-9a-zA-Z][_-]?)+` |
| `--model-id` | **Yes** | string | -- | Model ID or ARN to provision throughput for (1-2048 chars) |
| `--model-units` | **Yes** | integer | -- | Number of model units to allocate (min: 1) |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |
| `--commitment-duration` | No | string | None | Commitment duration: `OneMonth`, `SixMonths`. Omit for no commitment |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `key=string,value=string` |

**Output Schema:**
```json
{
    "provisionedModelArn": "string"
}
```

---

### `get-provisioned-model-throughput`

Gets details of a provisioned throughput.

**Synopsis:**
```bash
aws bedrock get-provisioned-model-throughput \
    --provisioned-model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-model-id` | **Yes** | string | -- | Provisioned throughput name or ARN |

**Output Schema:**
```json
{
    "modelUnits": "integer",
    "desiredModelUnits": "integer",
    "provisionedModelName": "string",
    "provisionedModelArn": "string",
    "modelArn": "string",
    "desiredModelArn": "string",
    "foundationModelArn": "string",
    "status": "Creating|InService|Updating|Failed",
    "creationTime": "timestamp",
    "lastModifiedTime": "timestamp",
    "failureMessage": "string",
    "commitmentDuration": "OneMonth|SixMonths",
    "commitmentExpirationTime": "timestamp"
}
```

---

### `list-provisioned-model-throughputs`

Lists provisioned throughputs in the account. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-provisioned-model-throughputs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--status-equals <value>] \
    [--model-arn-equals <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creation-time-after` | No | timestamp | None | Filter by creation time |
| `--creation-time-before` | No | timestamp | None | Filter by creation time |
| `--status-equals` | No | string | None | Filter: `Creating`, `InService`, `Updating`, `Failed` |
| `--model-arn-equals` | No | string | None | Filter by model ARN |
| `--name-contains` | No | string | None | Filter by name substring |
| `--sort-by` | No | string | None | Sort field: `CreationTime` |
| `--sort-order` | No | string | None | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "nextToken": "string",
    "provisionedModelSummaries": [
        {
            "provisionedModelName": "string",
            "provisionedModelArn": "string",
            "modelArn": "string",
            "desiredModelArn": "string",
            "foundationModelArn": "string",
            "modelUnits": "integer",
            "desiredModelUnits": "integer",
            "status": "Creating|InService|Updating|Failed",
            "commitmentDuration": "OneMonth|SixMonths",
            "commitmentExpirationTime": "timestamp",
            "creationTime": "timestamp",
            "lastModifiedTime": "timestamp"
        }
    ]
}
```

---

### `update-provisioned-model-throughput`

Updates a provisioned throughput (model units or model association).

**Synopsis:**
```bash
aws bedrock update-provisioned-model-throughput \
    --provisioned-model-id <value> \
    [--desired-provisioned-model-name <value>] \
    [--desired-model-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-model-id` | **Yes** | string | -- | Provisioned throughput name or ARN |
| `--desired-provisioned-model-name` | No | string | None | New name for the provisioned throughput |
| `--desired-model-id` | No | string | None | New model ID or ARN to associate |

**Output:** None (HTTP 200 on success)

---

### `delete-provisioned-model-throughput`

Deletes a provisioned throughput. Cannot delete if a commitment is active.

**Synopsis:**
```bash
aws bedrock delete-provisioned-model-throughput \
    --provisioned-model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-model-id` | **Yes** | string | -- | Provisioned throughput name or ARN |

**Output:** None (HTTP 200 on success)
