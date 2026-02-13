# Groups

### 1.1 `create-group`

Creates a resource group with the specified name and description. You can optionally include either a resource query or a service configuration.

**Synopsis:**
```bash
aws resource-groups create-group \
    --name <value> \
    [--description <value>] \
    [--resource-query <value>] \
    [--tags <value>] \
    [--configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the resource group (1-300 chars: letters, numbers, hyphens, periods, underscores) |
| `--description` | No | string | -- | Description of the resource group (max 1024 chars) |
| `--resource-query` | No | structure | None | Resource query defining group membership. Shorthand: `Type=string,Query=string` |
| `--tags` | No | map | None | Tags for the group. Shorthand: `KeyName1=string,KeyName2=string` |
| `--configuration` | No | list | None | Service configuration for the group |

**Resource Query Structure:**
```json
{
    "Type": "TAG_FILTERS_1_0|CLOUDFORMATION_STACK_1_0",
    "Query": "string"
}
```

**Tag Filter Query Example:**
```json
{
    "ResourceTypeFilters": ["AWS::EC2::Instance", "AWS::S3::Bucket"],
    "TagFilters": [
        {
            "Key": "Environment",
            "Values": ["Production"]
        }
    ]
}
```

**CloudFormation Stack Query Example:**
```json
{
    "ResourceTypeFilters": ["AWS::AllSupported"],
    "StackIdentifier": "arn:aws:cloudformation:us-east-1:123456789012:stack/my-stack/guid"
}
```

**Output Schema:**
```json
{
    "Group": {
        "GroupArn": "string",
        "Name": "string",
        "Description": "string"
    },
    "ResourceQuery": {
        "Type": "TAG_FILTERS_1_0|CLOUDFORMATION_STACK_1_0",
        "Query": "string"
    },
    "Tags": {
        "string": "string"
    },
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
        "ProposedConfiguration": [],
        "Status": "UPDATING|UPDATE_COMPLETE|UPDATE_FAILED"
    }
}
```

---

### 1.2 `get-group`

Returns information about a specified resource group.

**Synopsis:**
```bash
aws resource-groups get-group \
    [--group-name <value>] \
    [--group <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | -- | Name of the resource group (deprecated, use `--group`) |
| `--group` | No | string | -- | Name or ARN of the resource group |

**Output Schema:**
```json
{
    "Group": {
        "GroupArn": "string",
        "Name": "string",
        "Description": "string"
    }
}
```

---

### 1.3 `list-groups`

Returns a list of existing resource groups. **Paginated operation.**

**Synopsis:**
```bash
aws resource-groups list-groups \
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
| `--filters` | No | list | None | Filter groups. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:**
- `resource-type` - Filter by resource type (e.g., `AWS::EC2::Instance`)
- `configuration-type` - Filter by configuration type

**Output Schema:**
```json
{
    "GroupIdentifiers": [
        {
            "GroupName": "string",
            "GroupArn": "string",
            "Description": "string"
        }
    ],
    "Groups": [
        {
            "GroupArn": "string",
            "Name": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-group`

Updates the description of an existing group.

**Synopsis:**
```bash
aws resource-groups update-group \
    [--group-name <value>] \
    [--group <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | -- | Name of the group (deprecated, use `--group`) |
| `--group` | No | string | -- | Name or ARN of the group |
| `--description` | No | string | -- | Updated description |

**Output Schema:**
```json
{
    "Group": {
        "GroupArn": "string",
        "Name": "string",
        "Description": "string"
    }
}
```

---

### 1.5 `delete-group`

Deletes a specified resource group.

**Synopsis:**
```bash
aws resource-groups delete-group \
    [--group-name <value>] \
    [--group <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | -- | Name of the group (deprecated, use `--group`) |
| `--group` | No | string | -- | Name or ARN of the group to delete |

**Output Schema:**
```json
{
    "Group": {
        "GroupArn": "string",
        "Name": "string",
        "Description": "string"
    }
}
```

---

### 1.6 `list-group-resources`

Returns a list of resource ARNs that are members of a specified group. **Paginated operation.**

**Synopsis:**
```bash
aws resource-groups list-group-resources \
    [--group-name <value>] \
    [--group <value>] \
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
| `--group-name` | No | string | -- | Name of the group (deprecated, use `--group`) |
| `--group` | No | string | -- | Name or ARN of the group |
| `--filters` | No | list | None | Filters. Shorthand: `Name=resource-type,Values=string,string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Resources": [
        {
            "Identifier": {
                "ResourceArn": "string",
                "ResourceType": "string"
            },
            "Status": {
                "Name": "PENDING"
            }
        }
    ],
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
