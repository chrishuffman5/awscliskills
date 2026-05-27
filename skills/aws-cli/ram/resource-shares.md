# Resource Shares

### 1.1 `create-resource-share`

Creates a resource share. You can provide a list of resources and principals to associate with the share.

**Synopsis:**
```bash
aws ram create-resource-share \
    --name <value> \
    [--resource-arns <value>] \
    [--principals <value>] \
    [--tags <value>] \
    [--allow-external-principals | --no-allow-external-principals] \
    [--client-token <value>] \
    [--permission-arns <value>] \
    [--sources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the resource share |
| `--resource-arns` | No | list(string) | None | ARNs of resources to associate |
| `--principals` | No | list(string) | None | Principals to associate (account IDs, Organization ARNs, OU ARNs, IAM role/user ARNs) |
| `--tags` | No | list(structure) | None | Tags. Structure: `key=string,value=string` |
| `--allow-external-principals` | No | boolean | true | Allow principals outside your organization |
| `--client-token` | No | string | None | Idempotency token |
| `--permission-arns` | No | list(string) | None | ARNs of RAM permissions to associate |
| `--sources` | No | list(string) | None | Source constraints for service principal access |

**Output Schema:**
```json
{
    "resourceShare": {
        "resourceShareArn": "string",
        "name": "string",
        "owningAccountId": "string",
        "allowExternalPrincipals": "boolean",
        "status": "PENDING|ACTIVE|FAILED|DELETING|DELETED",
        "statusMessage": "string",
        "tags": [
            {
                "key": "string",
                "value": "string"
            }
        ],
        "creationTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD"
    },
    "clientToken": "string"
}
```

---

### 1.2 `update-resource-share`

Updates the specified resource share.

**Synopsis:**
```bash
aws ram update-resource-share \
    --resource-share-arn <value> \
    [--name <value>] \
    [--allow-external-principals | --no-allow-external-principals] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share to update |
| `--name` | No | string | None | New name for the resource share |
| `--allow-external-principals` | No | boolean | None | Whether external principals are allowed |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "resourceShare": {
        "resourceShareArn": "string",
        "name": "string",
        "owningAccountId": "string",
        "allowExternalPrincipals": "boolean",
        "status": "PENDING|ACTIVE|FAILED|DELETING|DELETED",
        "statusMessage": "string",
        "tags": [],
        "creationTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD"
    },
    "clientToken": "string"
}
```

---

### 1.3 `delete-resource-share`

Deletes the specified resource share.

**Synopsis:**
```bash
aws ram delete-resource-share \
    --resource-share-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share to delete |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "returnValue": "boolean",
    "clientToken": "string"
}
```

---

### 1.4 `get-resource-shares`

Gets the resource shares owned by you or shared with you. **Paginated operation.**

**Synopsis:**
```bash
aws ram get-resource-shares \
    --resource-owner <value> \
    [--name <value>] \
    [--tag-filters <value>] \
    [--resource-share-arns <value>] \
    [--resource-share-status <value>] \
    [--permission-arn <value>] \
    [--permission-version <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-owner` | **Yes** | string | -- | `SELF` or `OTHER-ACCOUNTS` |
| `--name` | No | string | None | Filter by resource share name |
| `--tag-filters` | No | list(structure) | None | Filter by tags. Structure: `tagKey=string,tagValues=string,string` |
| `--resource-share-arns` | No | list(string) | None | Filter by specific ARNs |
| `--resource-share-status` | No | string | None | Filter by status: `PENDING`, `ACTIVE`, `FAILED`, `DELETING`, `DELETED` |
| `--permission-arn` | No | string | None | Filter by permission ARN |
| `--permission-version` | No | integer | None | Filter by permission version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resourceShares": [
        {
            "resourceShareArn": "string",
            "name": "string",
            "owningAccountId": "string",
            "allowExternalPrincipals": "boolean",
            "status": "PENDING|ACTIVE|FAILED|DELETING|DELETED",
            "statusMessage": "string",
            "tags": [
                {
                    "key": "string",
                    "value": "string"
                }
            ],
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `associate-resource-share`

Adds resources or principals to a resource share.

**Synopsis:**
```bash
aws ram associate-resource-share \
    --resource-share-arn <value> \
    [--resource-arns <value>] \
    [--principals <value>] \
    [--client-token <value>] \
    [--sources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share |
| `--resource-arns` | No | list(string) | None | ARNs of resources to add |
| `--principals` | No | list(string) | None | Principals to add |
| `--client-token` | No | string | None | Idempotency token |
| `--sources` | No | list(string) | None | Source constraints |

**Output Schema:**
```json
{
    "resourceShareAssociations": [
        {
            "resourceShareArn": "string",
            "resourceShareName": "string",
            "associatedEntity": "string",
            "associationType": "PRINCIPAL|RESOURCE|SOURCE",
            "status": "ASSOCIATING|ASSOCIATED|FAILED|DISASSOCIATING|DISASSOCIATED|SUSPENDED|SUSPENDING|RESTORING",
            "statusMessage": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "external": "boolean"
        }
    ],
    "clientToken": "string"
}
```

---

### 1.6 `disassociate-resource-share`

Removes resources or principals from a resource share.

**Synopsis:**
```bash
aws ram disassociate-resource-share \
    --resource-share-arn <value> \
    [--resource-arns <value>] \
    [--principals <value>] \
    [--client-token <value>] \
    [--sources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share |
| `--resource-arns` | No | list(string) | None | ARNs of resources to remove |
| `--principals` | No | list(string) | None | Principals to remove |
| `--client-token` | No | string | None | Idempotency token |
| `--sources` | No | list(string) | None | Source constraints |

**Output Schema:**
```json
{
    "resourceShareAssociations": [
        {
            "resourceShareArn": "string",
            "resourceShareName": "string",
            "associatedEntity": "string",
            "associationType": "PRINCIPAL|RESOURCE|SOURCE",
            "status": "ASSOCIATING|ASSOCIATED|FAILED|DISASSOCIATING|DISASSOCIATED|SUSPENDED|SUSPENDING|RESTORING",
            "statusMessage": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "external": "boolean"
        }
    ],
    "clientToken": "string"
}
```

---

### 1.7 `get-resource-share-associations`

Gets the associations for a resource share. **Paginated operation.**

**Synopsis:**
```bash
aws ram get-resource-share-associations \
    --association-type <value> \
    [--resource-share-arns <value>] \
    [--resource-arn <value>] \
    [--principal <value>] \
    [--association-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-type` | **Yes** | string | -- | `PRINCIPAL` or `RESOURCE` |
| `--resource-share-arns` | No | list(string) | None | Filter by resource share ARNs |
| `--resource-arn` | No | string | None | Filter by resource ARN |
| `--principal` | No | string | None | Filter by principal |
| `--association-status` | No | string | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resourceShareAssociations": [
        {
            "resourceShareArn": "string",
            "resourceShareName": "string",
            "associatedEntity": "string",
            "associationType": "PRINCIPAL|RESOURCE|SOURCE",
            "status": "ASSOCIATING|ASSOCIATED|FAILED|DISASSOCIATING|DISASSOCIATED|SUSPENDED|SUSPENDING|RESTORING",
            "statusMessage": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "external": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.8 `list-resources`

Lists shared resources. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-resources \
    --resource-owner <value> \
    [--principal <value>] \
    [--resource-type <value>] \
    [--resource-arns <value>] \
    [--resource-share-arns <value>] \
    [--resource-region-scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-owner` | **Yes** | string | -- | `SELF` or `OTHER-ACCOUNTS` |
| `--principal` | No | string | None | Filter by principal |
| `--resource-type` | No | string | None | Filter by resource type (e.g., `ec2:Subnet`) |
| `--resource-arns` | No | list(string) | None | Filter by resource ARNs |
| `--resource-share-arns` | No | list(string) | None | Filter by resource share ARNs |
| `--resource-region-scope` | No | string | None | `ALL`, `REGIONAL`, `GLOBAL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resources": [
        {
            "arn": "string",
            "type": "string",
            "resourceShareArn": "string",
            "resourceGroupArn": "string",
            "status": "AVAILABLE|ZONAL_RESOURCE_INACCESSIBLE|LIMIT_EXCEEDED|UNAVAILABLE|PENDING",
            "statusMessage": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "resourceRegionScope": "REGIONAL|GLOBAL"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.9 `list-principals`

Lists principals that have access to shared resources. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-principals \
    --resource-owner <value> \
    [--resource-arn <value>] \
    [--principals <value>] \
    [--resource-type <value>] \
    [--resource-share-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-owner` | **Yes** | string | -- | `SELF` or `OTHER-ACCOUNTS` |
| `--resource-arn` | No | string | None | Filter by resource ARN |
| `--principals` | No | list(string) | None | Filter by specific principals |
| `--resource-type` | No | string | None | Filter by resource type |
| `--resource-share-arns` | No | list(string) | None | Filter by resource share ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "principals": [
        {
            "id": "string",
            "resourceShareArn": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "external": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.10 `list-resource-types`

Lists the shareable resource types. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-resource-types \
    [--resource-region-scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-region-scope` | No | string | None | `ALL`, `REGIONAL`, `GLOBAL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resourceTypes": [
        {
            "resourceType": "string",
            "serviceName": "string",
            "resourceRegionScope": "REGIONAL|GLOBAL"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.11 `get-resource-policies`

Gets the resource-based policies for shared resources. **Paginated operation.**

**Synopsis:**
```bash
aws ram get-resource-policies \
    --resource-arns <value> \
    [--principal <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arns` | **Yes** | list(string) | -- | ARNs of resources to get policies for |
| `--principal` | No | string | None | Filter by principal |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "policies": ["string"],
    "nextToken": "string"
}
```

---

### 1.12 `promote-resource-share-created-from-policy`

Promotes a resource share created from a resource-based policy to a standard RAM resource share.

**Synopsis:**
```bash
aws ram promote-resource-share-created-from-policy \
    --resource-share-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share to promote |

**Output Schema:**
```json
{
    "returnValue": "boolean"
}
```

---

### 1.13 `enable-sharing-with-aws-organization`

Enables resource sharing within your AWS Organization. Must be called from the management account.

**Synopsis:**
```bash
aws ram enable-sharing-with-aws-organization \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**
```json
{
    "returnValue": "boolean"
}
```
