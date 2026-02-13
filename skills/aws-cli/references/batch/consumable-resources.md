# Consumable Resources

### 6.1 `create-consumable-resource`

Creates a consumable resource for use with AWS Batch jobs.

**Synopsis:**
```bash
aws batch create-consumable-resource \
    --consumable-resource-name <value> \
    --total-quantity <value> \
    [--resource-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--consumable-resource-name` | **Yes** | string | -- | Name for the consumable resource |
| `--total-quantity` | **Yes** | long | -- | Total quantity available |
| `--resource-type` | No | string | None | Resource type identifier |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "consumableResourceName": "string",
    "consumableResourceArn": "string"
}
```

---

### 6.2 `update-consumable-resource`

Updates a consumable resource.

**Synopsis:**
```bash
aws batch update-consumable-resource \
    --consumable-resource <value> \
    --operation <value> \
    --quantity <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--consumable-resource` | **Yes** | string | -- | Consumable resource name or ARN |
| `--operation` | **Yes** | string | -- | Operation: `SET`, `ADD`, `REMOVE` |
| `--quantity` | **Yes** | long | -- | Quantity to set, add, or remove |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "consumableResourceName": "string",
    "consumableResourceArn": "string",
    "totalQuantity": "long",
    "inUseQuantity": "long",
    "availableQuantity": "long"
}
```

---

### 6.3 `delete-consumable-resource`

Deletes a consumable resource.

**Synopsis:**
```bash
aws batch delete-consumable-resource \
    --consumable-resource <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--consumable-resource` | **Yes** | string | -- | Consumable resource name or ARN |

**Output Schema:**
```json
{}
```

---

### 6.4 `describe-consumable-resource`

Describes a consumable resource.

**Synopsis:**
```bash
aws batch describe-consumable-resource \
    --consumable-resource <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--consumable-resource` | **Yes** | string | -- | Consumable resource name or ARN |

**Output Schema:**
```json
{
    "consumableResourceName": "string",
    "consumableResourceArn": "string",
    "totalQuantity": "long",
    "inUseQuantity": "long",
    "availableQuantity": "long",
    "resourceType": "string",
    "createdAt": "long",
    "tags": {}
}
```

---

### 6.5 `list-consumable-resources`

Lists consumable resources. **Paginated operation.**

**Synopsis:**
```bash
aws batch list-consumable-resources \
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
| `--filters` | No | list | None | Filters. Shorthand: `name=string,values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "consumableResources": [
        {
            "consumableResourceName": "string",
            "consumableResourceArn": "string",
            "totalQuantity": "long",
            "inUseQuantity": "long",
            "availableQuantity": "long",
            "resourceType": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.6 `list-jobs-by-consumable-resource`

Lists jobs that use a specific consumable resource. **Paginated operation.**

**Synopsis:**
```bash
aws batch list-jobs-by-consumable-resource \
    --consumable-resource <value> \
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
| `--consumable-resource` | **Yes** | string | -- | Consumable resource name or ARN |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "jobs": [
        {
            "jobArn": "string",
            "jobId": "string",
            "jobName": "string",
            "jobQueue": "string",
            "status": "SUBMITTED|PENDING|RUNNABLE|STARTING|RUNNING|SUCCEEDED|FAILED",
            "quantity": "long",
            "statusReason": "string",
            "startedAt": "long",
            "createdAt": "long"
        }
    ],
    "nextToken": "string"
}
```
