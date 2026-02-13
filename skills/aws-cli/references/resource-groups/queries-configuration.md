# Queries & Configuration

## Queries

### 2.1 `get-group-query`

Retrieves the resource query associated with the specified resource group.

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
| `--group` | No | string | -- | Name or ARN of the group |

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
| `--group` | No | string | -- | Name or ARN of the group |
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

Returns a list of AWS resource identifiers that match the specified query. **Paginated operation.**

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
| `--starting-token` | No | string | None | Pagination token |
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

## Configuration

### 2.4 `get-group-configuration`

Retrieves the service configuration associated with the specified resource group.

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
| `--group` | No | string | -- | Name or ARN of the group |

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

Attaches a service configuration to the specified group.

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
| `--group` | No | string | -- | Name or ARN of the group |
| `--configuration` | No | list | None | Service configuration items |

**Configuration Item Structure:**
```json
[
    {
        "Type": "AWS::ResourceGroups::Generic",
        "Parameters": [
            {
                "Name": "allowed-resource-types",
                "Values": ["AWS::EC2::Host"]
            }
        ]
    },
    {
        "Type": "AWS::EC2::HostManagement",
        "Parameters": [
            {
                "Name": "auto-allocate-host",
                "Values": ["true"]
            },
            {
                "Name": "auto-release-host",
                "Values": ["true"]
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

Adds specified resources to a group. Works only with groups that have no resource query (manually managed groups).

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
| `--group` | **Yes** | string | -- | Name or ARN of the group |
| `--resource-arns` | **Yes** | list(string) | -- | List of resource ARNs to add |

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

Removes specified resources from a group. Works only with groups that have no resource query (manually managed groups).

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
| `--group` | **Yes** | string | -- | Name or ARN of the group |
| `--resource-arns` | **Yes** | list(string) | -- | List of resource ARNs to remove |

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
