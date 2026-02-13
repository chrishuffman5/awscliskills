# Generated Templates

### 6.1 `create-generated-template`

Creates a generated template (IaC generator) from existing resources identified by a resource scan.

**Synopsis:**
```bash
aws cloudformation create-generated-template \
    --generated-template-name <value> \
    [--resources <value>] \
    [--template-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--generated-template-name` | **Yes** | string | -- | Name for the generated template |
| `--resources` | No | list | None | Resources to include. JSON: `[{"ResourceType":"string","LogicalResourceId":"string","ResourceIdentifier":{"key":"value"}}]` |
| `--template-configuration` | No | structure | None | Template configuration. Shorthand: `DeletionPolicy=DELETE\|RETAIN\|SNAPSHOT,UpdateReplacePolicy=DELETE\|RETAIN\|SNAPSHOT` |

**Output Schema:**
```json
{
    "GeneratedTemplateId": "string"
}
```

---

### 6.2 `update-generated-template`

Updates a generated template. Use to add or remove resources, or change the template configuration.

**Synopsis:**
```bash
aws cloudformation update-generated-template \
    --generated-template-name <value> \
    [--new-generated-template-name <value>] \
    [--add-resources <value>] \
    [--remove-resources <value>] \
    [--refresh-all-resources | --no-refresh-all-resources] \
    [--template-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--generated-template-name` | **Yes** | string | -- | Name or ID of the generated template |
| `--new-generated-template-name` | No | string | None | New name for the template |
| `--add-resources` | No | list | None | Resources to add |
| `--remove-resources` | No | list(string) | None | Logical IDs of resources to remove |
| `--refresh-all-resources` | No | boolean | false | Refresh all resource data from the live environment |
| `--template-configuration` | No | structure | None | Updated template configuration |

**Output Schema:**
```json
{
    "GeneratedTemplateId": "string"
}
```

---

### 6.3 `delete-generated-template`

Deletes a generated template.

**Synopsis:**
```bash
aws cloudformation delete-generated-template \
    --generated-template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--generated-template-name` | **Yes** | string | -- | Name or ID of the generated template |

**Output:** No output on success.

---

### 6.4 `describe-generated-template`

Describes a generated template, including its status, resources, and configuration.

**Synopsis:**
```bash
aws cloudformation describe-generated-template \
    --generated-template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--generated-template-name` | **Yes** | string | -- | Name or ID of the generated template |

**Output Schema:**
```json
{
    "GeneratedTemplateId": "string",
    "GeneratedTemplateName": "string",
    "Resources": [
        {
            "LogicalResourceId": "string",
            "ResourceType": "string",
            "ResourceIdentifier": {
                "key": "value"
            },
            "ResourceStatus": "PENDING|IN_PROGRESS|FAILED|COMPLETE",
            "ResourceStatusReason": "string"
        }
    ],
    "Status": "CREATE_PENDING|UPDATE_PENDING|DELETE_PENDING|CREATE_IN_PROGRESS|UPDATE_IN_PROGRESS|DELETE_IN_PROGRESS|FAILED|COMPLETE",
    "StatusReason": "string",
    "CreationTime": "timestamp",
    "LastUpdatedTime": "timestamp",
    "Progress": {
        "ResourcesSucceeded": "integer",
        "ResourcesFailed": "integer",
        "ResourcesProcessing": "integer",
        "ResourcesPending": "integer"
    },
    "StackId": "string",
    "TemplateConfiguration": {
        "DeletionPolicy": "DELETE|RETAIN|SNAPSHOT",
        "UpdateReplacePolicy": "DELETE|RETAIN|SNAPSHOT"
    },
    "TotalWarnings": "integer"
}
```

---

### 6.5 `get-generated-template`

Retrieves the template body for a generated template.

**Synopsis:**
```bash
aws cloudformation get-generated-template \
    --generated-template-name <value> \
    [--format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--generated-template-name` | **Yes** | string | -- | Name or ID of the generated template |
| `--format` | No | string | `JSON` | Output format: `JSON` or `YAML` |

**Output Schema:**
```json
{
    "Status": "CREATE_PENDING|UPDATE_PENDING|DELETE_PENDING|CREATE_IN_PROGRESS|UPDATE_IN_PROGRESS|DELETE_IN_PROGRESS|FAILED|COMPLETE",
    "TemplateBody": "string"
}
```

---

### 6.6 `list-generated-templates`

Lists generated templates in the account. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-generated-templates \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Summaries": [
        {
            "GeneratedTemplateId": "string",
            "GeneratedTemplateName": "string",
            "Status": "string",
            "StatusReason": "string",
            "CreationTime": "timestamp",
            "LastUpdatedTime": "timestamp",
            "NumberOfResources": "integer"
        }
    ],
    "NextToken": "string"
}
```
