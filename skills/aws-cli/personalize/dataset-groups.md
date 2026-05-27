# Dataset Groups

### 1.1 `create-dataset-group`

Creates a dataset group, a container for datasets, solutions, and campaigns. Optionally specify a domain for Domain dataset groups.

**Synopsis:**
```bash
aws personalize create-dataset-group \
    --name <value> \
    [--role-arn <value>] \
    [--kms-key-arn <value>] \
    [--domain <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Dataset group name (1-63 chars) |
| `--role-arn` | No | string | None | IAM role ARN for KMS key access |
| `--kms-key-arn` | No | string | None | KMS key ARN for dataset encryption |
| `--domain` | No | string | None | Domain: `ECOMMERCE` or `VIDEO_ON_DEMAND` |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `tagKey=string,tagValue=string ...` |

**Output Schema:**
```json
{
    "datasetGroupArn": "string",
    "domain": "ECOMMERCE|VIDEO_ON_DEMAND"
}
```

---

### 1.2 `describe-dataset-group`

Describes a dataset group.

**Synopsis:**
```bash
aws personalize describe-dataset-group \
    --dataset-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the dataset group |

**Output Schema:**
```json
{
    "datasetGroup": {
        "name": "string",
        "datasetGroupArn": "string",
        "status": "string",
        "roleArn": "string",
        "kmsKeyArn": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "failureReason": "string",
        "domain": "ECOMMERCE|VIDEO_ON_DEMAND"
    }
}
```

---

### 1.3 `list-dataset-groups`

Lists all dataset groups in the account. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-dataset-groups \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "datasetGroups": [
        {
            "name": "string",
            "datasetGroupArn": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string",
            "domain": "ECOMMERCE|VIDEO_ON_DEMAND"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `delete-dataset-group`

Deletes a dataset group. Must delete all associated campaigns, solutions, event trackers, and datasets first.

**Synopsis:**
```bash
aws personalize delete-dataset-group \
    --dataset-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the dataset group to delete |

**Output:** None
