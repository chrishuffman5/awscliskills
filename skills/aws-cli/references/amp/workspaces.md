# Workspaces

### 1.1 `create-workspace`

Creates a new Amazon Managed Service for Prometheus workspace.

**Synopsis:**
```bash
aws amp create-workspace \
    [--alias <value>] \
    [--client-token <value>] \
    [--kms-key-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias` | No | string | -- | Alias for the workspace |
| `--client-token` | No | string | auto-generated | Idempotency token |
| `--kms-key-arn` | No | string | -- | KMS key ARN for encryption at rest |
| `--tags` | No | map | -- | Tags as key-value pairs |

**Output Schema:**
```json
{
    "arn": "string",
    "status": {
        "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED"
    },
    "tags": {
        "string": "string"
    },
    "workspaceId": "string"
}
```

---

### 1.2 `delete-workspace`

Deletes an Amazon Managed Service for Prometheus workspace.

**Synopsis:**
```bash
aws amp delete-workspace \
    --workspace-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace to delete |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-workspace`

Describes an existing Amazon Managed Service for Prometheus workspace.

**Synopsis:**
```bash
aws amp describe-workspace \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |

**Output Schema:**
```json
{
    "workspace": {
        "alias": "string",
        "arn": "string",
        "createdAt": "timestamp",
        "kmsKeyArn": "string",
        "prometheusEndpoint": "string",
        "status": {
            "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED"
        },
        "tags": {
            "string": "string"
        },
        "workspaceId": "string"
    }
}
```

---

### 1.4 `list-workspaces`

Lists all Amazon Managed Service for Prometheus workspaces in the account. **Paginated operation.**

**Synopsis:**
```bash
aws amp list-workspaces \
    [--alias <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias` | No | string | -- | Filter by alias prefix |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "workspaces": [
        {
            "alias": "string",
            "arn": "string",
            "createdAt": "timestamp",
            "kmsKeyArn": "string",
            "status": {
                "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED"
            },
            "tags": {
                "string": "string"
            },
            "workspaceId": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-workspace-alias`

Updates the alias of an existing workspace.

**Synopsis:**
```bash
aws amp update-workspace-alias \
    --workspace-id <value> \
    [--alias <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--alias` | No | string | -- | New alias (empty string to clear) |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{}
```
