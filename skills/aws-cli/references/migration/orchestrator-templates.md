# Orchestrator Templates

These commands use the `migrationhuborchestrator` service namespace. They manage migration workflow templates and plugins.

## Templates

### 13.1 `create-template`

Creates a migration workflow template.

**Synopsis:**
```bash
aws migrationhuborchestrator create-template \
    --template-name <value> \
    --template-source <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name (1-128 chars) |
| `--template-source` | **Yes** | structure | -- | Source of the template (existing workflow ID) |
| `--description` | No | string | None | Description (max 250 chars) |
| `--client-token` | No | string | None | Client token |
| `--tags` | No | map | None | Tags |

**Template Source Structure:**
```json
{
    "workflowId": "string"
}
```

**Output Schema:**
```json
{
    "templateId": "string",
    "templateArn": "string",
    "tags": {"key": "value"}
}
```

---

### 13.2 `get-template`

Gets details of a migration workflow template.

**Synopsis:**
```bash
aws migrationhuborchestrator get-template \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Template ID |

**Output Schema:**
```json
{
    "id": "string",
    "templateArn": "string",
    "name": "string",
    "description": "string",
    "inputs": [
        {
            "inputName": "string",
            "dataType": "STRING|INTEGER|STRINGLIST|STRINGMAP",
            "required": true|false
        }
    ],
    "tools": [
        {"name": "string", "url": "string"}
    ],
    "creationTime": "timestamp",
    "owner": "string",
    "status": "CREATED|READY|PENDING_CREATION|CREATING|CREATION_FAILED",
    "statusMessage": "string",
    "templateClass": "A2C|MGN|SAP_MULTI|SQL_EC2|SQL_RDS|VMIE",
    "tags": {"key": "value"}
}
```

---

### 13.3 `list-templates`

Lists migration workflow templates. **Paginated.**

**Synopsis:**
```bash
aws migrationhuborchestrator list-templates \
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
| `--name` | No | string | None | Filter by template name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "templateSummary": [
        {
            "id": "string",
            "name": "string",
            "arn": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 13.4 `update-template`

Updates a migration workflow template.

**Synopsis:**
```bash
aws migrationhuborchestrator update-template \
    --id <value> \
    [--template-name <value>] \
    [--template-description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Template ID |
| `--template-name` | No | string | None | Updated name |
| `--template-description` | No | string | None | Updated description |
| `--client-token` | No | string | None | Client token |

**Output Schema:**
```json
{
    "templateId": "string",
    "templateArn": "string",
    "tags": {"key": "value"}
}
```

---

### 13.5 `delete-template`

Deletes a migration workflow template.

**Synopsis:**
```bash
aws migrationhuborchestrator delete-template \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Template ID |

**Output:** None

---

## Template Steps & Step Groups

### 13.6 `get-template-step`

Gets details of a template step.

**Synopsis:**
```bash
aws migrationhuborchestrator get-template-step \
    --id <value> \
    --template-id <value> \
    --step-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Step ID |
| `--template-id` | **Yes** | string | -- | Template ID |
| `--step-group-id` | **Yes** | string | -- | Step group ID |

**Output Schema:**
```json
{
    "id": "string",
    "stepGroupId": "string",
    "templateId": "string",
    "name": "string",
    "description": "string",
    "stepActionType": "MANUAL|AUTOMATED",
    "creationTime": "string",
    "previous": ["string"],
    "next": ["string"],
    "outputs": [
        {
            "name": "string",
            "dataType": "STRING|INTEGER|STRINGLIST|STRINGMAP",
            "required": true|false
        }
    ],
    "stepAutomationConfiguration": {
        "scriptLocationS3Bucket": "string",
        "scriptLocationS3Key": {"linux": "string", "windows": "string"},
        "command": {"linux": "string", "windows": "string"},
        "runEnvironment": "AWS|ONPREMISE",
        "targetType": "SINGLE|ALL|NONE"
    }
}
```

---

### 13.7 `list-template-steps`

Lists steps in a template step group. **Paginated.**

**Synopsis:**
```bash
aws migrationhuborchestrator list-template-steps \
    --template-id <value> \
    --step-group-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-id` | **Yes** | string | -- | Template ID |
| `--step-group-id` | **Yes** | string | -- | Step group ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "templateStepSummaryList": [
        {
            "id": "string",
            "stepGroupId": "string",
            "templateId": "string",
            "name": "string",
            "stepActionType": "MANUAL|AUTOMATED",
            "targetType": "SINGLE|ALL|NONE",
            "owner": "AWS_MANAGED|CUSTOM",
            "previous": ["string"],
            "next": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 13.8 `get-template-step-group`

Gets details of a template step group.

**Synopsis:**
```bash
aws migrationhuborchestrator get-template-step-group \
    --template-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-id` | **Yes** | string | -- | Template ID |
| `--id` | **Yes** | string | -- | Step group ID |

**Output Schema:**
```json
{
    "templateId": "string",
    "id": "string",
    "name": "string",
    "description": "string",
    "status": "AWAITING_DEPENDENCIES|READY|IN_PROGRESS|COMPLETED|FAILED|PAUSED|PAUSING|USER_ATTENTION_REQUIRED",
    "creationTime": "timestamp",
    "lastModifiedTime": "timestamp",
    "tools": [
        {"name": "string", "url": "string"}
    ],
    "previous": ["string"],
    "next": ["string"]
}
```

---

### 13.9 `list-template-step-groups`

Lists step groups in a template. **Paginated.**

**Synopsis:**
```bash
aws migrationhuborchestrator list-template-step-groups \
    --template-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-id` | **Yes** | string | -- | Template ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "templateStepGroupSummary": [
        {
            "id": "string",
            "name": "string",
            "previous": ["string"],
            "next": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

## Plugins

### 13.10 `list-plugins`

Lists orchestrator plugins. **Paginated.**

**Synopsis:**
```bash
aws migrationhuborchestrator list-plugins \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "plugins": [
        {
            "pluginId": "string",
            "hostname": "string",
            "status": "HEALTHY|UNHEALTHY",
            "ipAddress": "string",
            "version": "string",
            "registeredTime": "string"
        }
    ],
    "nextToken": "string"
}
```
