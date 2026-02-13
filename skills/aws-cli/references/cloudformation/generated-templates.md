# Generated Templates

### 6.1 `create-generated-template`

Creates a template from existing resources discovered via resource scanning.

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
| `--generated-template-name` | **Yes** | string | -- | Name of the generated template |
| `--resources` | No | list | None | Resources to include. JSON: `[{"ResourceType":"string","LogicalResourceId":"string","ResourceIdentifier":{"key":"value"}}]` |
| `--template-configuration` | No | structure | None | Configuration options. Shorthand: `DeletionPolicy=DELETE\|RETAIN,UpdateReplacePolicy=DELETE\|RETAIN` |

**Output Schema:**
```json
{
    "GeneratedTemplateId": "string"
}
```

---

### 6.2 `delete-generated-template`

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
| `--generated-template-name` | **Yes** | string | -- | Name or ARN of the generated template |

**Output:** No output on success.

---

### 6.3 `describe-generated-template`

Describes a generated template, including its status and resource details.

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
| `--generated-template-name` | **Yes** | string | -- | Name or ARN of the generated template |

**Output Schema:**
```json
{
    "GeneratedTemplateId": "string",
    "GeneratedTemplateName": "string",
    "Resources": [
        {
            "ResourceType": "string",
            "LogicalResourceId": "string",
            "ResourceIdentifier": {
                "key": "value"
            },
            "ResourceStatus": "PENDING|IN_PROGRESS|FAILED|COMPLETE",
            "ResourceStatusReason": "string",
            "Warnings": [
                {
                    "Type": "MUTUALLY_EXCLUSIVE_PROPERTIES|UNSUPPORTED_PROPERTIES|MUTUALLY_EXCLUSIVE_TYPES",
                    "Properties": [
                        {
                            "PropertyPath": "string",
                            "Required": true|false,
                            "Description": "string"
                        }
                    ]
                }
            ]
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
        "DeletionPolicy": "DELETE|RETAIN",
        "UpdateReplacePolicy": "DELETE|RETAIN"
    },
    "TotalWarnings": "integer"
}
```

---

### 6.4 `get-generated-template`

Retrieves the generated template body.

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
| `--generated-template-name` | **Yes** | string | -- | Name or ARN of the generated template |
| `--format` | No | string | `JSON` | Output format: `JSON` or `YAML` |

**Output Schema:**
```json
{
    "Status": "CREATE_PENDING|UPDATE_PENDING|DELETE_PENDING|CREATE_IN_PROGRESS|UPDATE_IN_PROGRESS|DELETE_IN_PROGRESS|FAILED|COMPLETE",
    "TemplateBody": "string"
}
```

---

### 6.5 `list-generated-templates`

Lists generated templates. **Paginated operation.**

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

---

### 6.6 `update-generated-template`

Updates a generated template by adding, removing, or modifying resources.

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
| `--generated-template-name` | **Yes** | string | -- | Name or ARN of the generated template |
| `--new-generated-template-name` | No | string | None | New name for the template |
| `--add-resources` | No | list | None | Resources to add |
| `--remove-resources` | No | list(string) | None | Logical resource IDs to remove |
| `--refresh-all-resources` | No | boolean | false | Refresh all resources in the template |
| `--template-configuration` | No | structure | None | Updated configuration |

**Output Schema:**
```json
{
    "GeneratedTemplateId": "string"
}
```
