# Queries & Configuration

### 2.1 `get-group-query`

Retrieves the resource query associated with a specified resource group.

**Synopsis:**
```bash
aws resource-groups get-group-query \
    [--group-name <value>] \
    [--group <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | -- | Name of the group (deprecated, use `--group`) |
| `--group` | No | string | -- | Name or ARN of the resource group |

**Output Schema:**
```json
{
    "GroupQuery": {
        "GroupName": "string",
        "ResourceQuery": {
            "Type": "TAG_FILTERS_1_0|CLOUDFORMATION_STACK_1_0",
            "Query": "string"
        }
    }
}
```

---

### 2.2 `update-group-query`

Updates the resource query of a group.

**Synopsis:**
```bash
aws resource-groups update-group-query \
    [--group-name <value>] \
    [--group <value>] \
    --resource-query <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | -- | Name of the group (deprecated, use `--group`) |
| `--group` | No | string | -- | Name or ARN of the resource group |
| `--resource-query` | **Yes** | structure | -- | Updated resource query. Shorthand: `Type=string,Query=string` |

**Output Schema:**
```json
{
    "GroupQuery": {
        "GroupName": "string",
        "ResourceQuery": {
            "Type": "TAG_FILTERS_1_0|CLOUDFORMATION_STACK_1_0",
            "Query": "string"
        }
    }
}
```

---

### 2.3 `search-resources`

Returns a list of AWS resource identifiers that match the specified query. The resources must be tagged or associated with a CloudFormation stack. **Paginated operation.**

**Synopsis:**
```bash
aws resource-groups search-resources \
    --resource-query <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-query` | **Yes** | structure | -- | Resource query. Shorthand: `Type=string,Query=string` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceIdentifiers": [
        {
            "ResourceArn": "string",
            "ResourceType": "string"
        }
    ],
    "NextToken": "string",
    "QueryErrors": [
        {
            "ErrorCode": "CLOUDFORMATION_STACK_INACTIVE|CLOUDFORMATION_STACK_NOT_EXISTING|CLOUDFORMATION_STACK_UNASSUMABLE_ROLE|RESOURCE_TYPE_NOT_SUPPORTED",
            "Message": "string"
        }
    ]
}
```

---

### 2.4 `get-group-configuration`

Retrieves the service configuration associated with a specified resource group.

**Synopsis:**
```bash
aws resource-groups get-group-configuration \
    [--group <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group` | No | string | -- | Name or ARN of the resource group |

**Output Schema:**
```json
{
    "GroupConfiguration": {
        "Configuration": [
            {
                "Type": "string",
                "Parameters": [
                    {
                        "Name": "string",
                        "Values": ["string"]
                    }
                ]
            }
        ],
        "ProposedConfiguration": [
            {
                "Type": "string",
                "Parameters": [
                    {
                        "Name": "string",
                        "Values": ["string"]
                    }
                ]
            }
        ],
        "Status": "UPDATING|UPDATE_COMPLETE|UPDATE_FAILED",
        "FailureReason": "string"
    }
}
```

---

### 2.5 `put-group-configuration`

Attaches a service configuration to the specified group. This creates or replaces the current group configuration.

**Synopsis:**
```bash
aws resource-groups put-group-configuration \
    [--group <value>] \
    [--configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group` | No | string | -- | Name or ARN of the resource group |
| `--configuration` | No | list | None | Service configuration items |

**Configuration Item Structure:**
```json
[
    {
        "Type": "string",
        "Parameters": [
            {
                "Name": "string",
                "Values": ["string"]
            }
        ]
    }
]
```

**Output Schema:**
```json
{}
```

---

### 2.6 `group-resources`

Adds specified resources to a specified group. Only resources that are not already members of the group are added.

**Synopsis:**
```bash
aws resource-groups group-resources \
    --group <value> \
    --resource-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group` | **Yes** | string | -- | Name or ARN of the resource group |
| `--resource-arns` | **Yes** | list(string) | -- | List of resource ARNs to add to the group |

**Output Schema:**
```json
{
    "Succeeded": ["string"],
    "Failed": [
        {
            "ResourceArn": "string",
            "ErrorMessage": "string",
            "ErrorCode": "string"
        }
    ],
    "Pending": [
        {
            "ResourceArn": "string"
        }
    ]
}
```

---

### 2.7 `ungroup-resources`

Removes specified resources from a specified group. The resources are not deleted, only removed from the group.

**Synopsis:**
```bash
aws resource-groups ungroup-resources \
    --group <value> \
    --resource-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group` | **Yes** | string | -- | Name or ARN of the resource group |
| `--resource-arns` | **Yes** | list(string) | -- | List of resource ARNs to remove from the group |

**Output Schema:**
```json
{
    "Succeeded": ["string"],
    "Failed": [
        {
            "ResourceArn": "string",
            "ErrorMessage": "string",
            "ErrorCode": "string"
        }
    ],
    "Pending": [
        {
            "ResourceArn": "string"
        }
    ]
}
```

---

### 2.8 `list-grouping-statuses`

Returns the status of grouping and ungrouping requests. **Paginated operation.**

**Synopsis:**
```bash
aws resource-groups list-grouping-statuses \
    --group <value> \
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
| `--group` | **Yes** | string | -- | Name or ARN of the resource group |
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:**
- `status` -- Filter by status: `SUCCESS`, `FAILED`, `IN_PROGRESS`, `SKIPPED`
- `resource-arn` -- Filter by resource ARN

**Output Schema:**
```json
{
    "Group": "string",
    "GroupingStatuses": [
        {
            "ResourceArn": "string",
            "Action": "GROUP|UNGROUP",
            "Status": "SUCCESS|FAILED|IN_PROGRESS|SKIPPED",
            "ErrorMessage": "string",
            "ErrorCode": "string",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
