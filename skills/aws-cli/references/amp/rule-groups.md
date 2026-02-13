# Rule Groups

### 3.1 `create-rule-groups-namespace`

Creates a rule groups namespace within a workspace. Use this to upload Prometheus recording and alerting rules.

**Synopsis:**
```bash
aws amp create-rule-groups-namespace \
    --workspace-id <value> \
    --name <value> \
    --data <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--name` | **Yes** | string | -- | Name of the rule groups namespace |
| `--data` | **Yes** | blob | -- | Rule groups data (YAML, base64-encoded or `fileb://`) |
| `--client-token` | No | string | auto-generated | Idempotency token |
| `--tags` | No | map | -- | Tags as key-value pairs |

**Output Schema:**
```json
{
    "arn": "string",
    "name": "string",
    "status": {
        "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED|UPDATE_FAILED",
        "statusReason": "string"
    },
    "tags": {
        "string": "string"
    }
}
```

---

### 3.2 `delete-rule-groups-namespace`

Deletes a rule groups namespace from a workspace.

**Synopsis:**
```bash
aws amp delete-rule-groups-namespace \
    --workspace-id <value> \
    --name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--name` | **Yes** | string | -- | Name of the rule groups namespace |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{}
```

---

### 3.3 `describe-rule-groups-namespace`

Describes a rule groups namespace.

**Synopsis:**
```bash
aws amp describe-rule-groups-namespace \
    --workspace-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--name` | **Yes** | string | -- | Name of the rule groups namespace |

**Output Schema:**
```json
{
    "ruleGroupsNamespace": {
        "arn": "string",
        "createdAt": "timestamp",
        "data": "blob",
        "modifiedAt": "timestamp",
        "name": "string",
        "status": {
            "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED|UPDATE_FAILED",
            "statusReason": "string"
        },
        "tags": {
            "string": "string"
        }
    }
}
```

---

### 3.4 `list-rule-groups-namespaces`

Lists rule groups namespaces within a workspace. **Paginated operation.**

**Synopsis:**
```bash
aws amp list-rule-groups-namespaces \
    --workspace-id <value> \
    [--name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--name` | No | string | -- | Filter by name prefix |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ruleGroupsNamespaces": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "modifiedAt": "timestamp",
            "name": "string",
            "status": {
                "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED|UPDATE_FAILED",
                "statusReason": "string"
            },
            "tags": {
                "string": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `put-rule-groups-namespace`

Updates a rule groups namespace. Replaces the existing rule groups data.

**Synopsis:**
```bash
aws amp put-rule-groups-namespace \
    --workspace-id <value> \
    --name <value> \
    --data <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--name` | **Yes** | string | -- | Name of the rule groups namespace |
| `--data` | **Yes** | blob | -- | New rule groups data (YAML, base64-encoded or `fileb://`) |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "arn": "string",
    "name": "string",
    "status": {
        "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED|UPDATE_FAILED",
        "statusReason": "string"
    },
    "tags": {
        "string": "string"
    }
}
```
