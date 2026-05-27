# Permissions

### 3.1 `create-permission`

Creates a customer-managed permission for a specified resource type.

**Synopsis:**
```bash
aws ram create-permission \
    --name <value> \
    --resource-type <value> \
    --policy-template <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Permission name (1-36 chars, unique per region) |
| `--resource-type` | **Yes** | string | -- | Resource type in `service:resource` format (e.g., `ec2:Subnet`) |
| `--policy-template` | **Yes** | string | -- | JSON IAM policy with `Effect` (ALLOW only), `Action`, and optional `Condition` |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list(structure) | None | Tags. Structure: `key=string,value=string` |

**Output Schema:**
```json
{
    "permission": {
        "arn": "string",
        "version": "string",
        "defaultVersion": "boolean",
        "name": "string",
        "resourceType": "string",
        "status": "string",
        "creationTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "isResourceTypeDefault": "boolean",
        "permissionType": "CUSTOMER_MANAGED|AWS_MANAGED",
        "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD",
        "tags": [
            {
                "key": "string",
                "value": "string"
            }
        ]
    },
    "clientToken": "string"
}
```

---

### 3.2 `create-permission-version`

Creates a new version of an existing customer-managed permission.

**Synopsis:**
```bash
aws ram create-permission-version \
    --permission-arn <value> \
    --policy-template <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--permission-arn` | **Yes** | string | -- | ARN of the permission to create a version for |
| `--policy-template` | **Yes** | string | -- | JSON IAM policy for the new version |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "permission": {
        "arn": "string",
        "version": "string",
        "defaultVersion": "boolean",
        "name": "string",
        "resourceType": "string",
        "permission": "string",
        "creationTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "isResourceTypeDefault": "boolean",
        "permissionType": "CUSTOMER_MANAGED|AWS_MANAGED",
        "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD",
        "status": "ATTACHABLE|UNATTACHABLE|DELETING|DELETED",
        "tags": []
    },
    "clientToken": "string"
}
```

---

### 3.3 `delete-permission`

Deletes a customer-managed permission.

**Synopsis:**
```bash
aws ram delete-permission \
    --permission-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--permission-arn` | **Yes** | string | -- | ARN of the permission to delete |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "returnValue": "boolean",
    "clientToken": "string",
    "permissionStatus": "ATTACHABLE|UNATTACHABLE|DELETING|DELETED"
}
```

---

### 3.4 `delete-permission-version`

Deletes a specific version of a customer-managed permission.

**Synopsis:**
```bash
aws ram delete-permission-version \
    --permission-arn <value> \
    --permission-version <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--permission-arn` | **Yes** | string | -- | ARN of the permission |
| `--permission-version` | **Yes** | integer | -- | Version number to delete |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "returnValue": "boolean",
    "clientToken": "string",
    "permissionStatus": "ATTACHABLE|UNATTACHABLE|DELETING|DELETED"
}
```

---

### 3.5 `get-permission`

Retrieves the details of a specific permission version.

**Synopsis:**
```bash
aws ram get-permission \
    --permission-arn <value> \
    [--permission-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--permission-arn` | **Yes** | string | -- | ARN of the permission |
| `--permission-version` | No | integer | default version | Specific version to retrieve |

**Output Schema:**
```json
{
    "permission": {
        "arn": "string",
        "version": "string",
        "defaultVersion": "boolean",
        "name": "string",
        "resourceType": "string",
        "permission": "string",
        "creationTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "isResourceTypeDefault": "boolean",
        "permissionType": "CUSTOMER_MANAGED|AWS_MANAGED",
        "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD",
        "status": "ATTACHABLE|UNATTACHABLE|DELETING|DELETED",
        "tags": [
            {
                "key": "string",
                "value": "string"
            }
        ]
    }
}
```

---

### 3.6 `list-permissions`

Lists all permissions available in RAM. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-permissions \
    [--resource-type <value>] \
    [--permission-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | No | string | None | Filter by resource type |
| `--permission-type` | No | string | None | `ALL`, `AWS_MANAGED`, `CUSTOMER_MANAGED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "permissions": [
        {
            "arn": "string",
            "version": "string",
            "defaultVersion": "boolean",
            "name": "string",
            "resourceType": "string",
            "status": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "isResourceTypeDefault": "boolean",
            "permissionType": "CUSTOMER_MANAGED|AWS_MANAGED",
            "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD",
            "tags": []
        }
    ],
    "nextToken": "string"
}
```

---

### 3.7 `list-permission-versions`

Lists the versions of a permission. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-permission-versions \
    --permission-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--permission-arn` | **Yes** | string | -- | ARN of the permission |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "permissions": [
        {
            "arn": "string",
            "version": "string",
            "defaultVersion": "boolean",
            "name": "string",
            "resourceType": "string",
            "status": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "isResourceTypeDefault": "boolean",
            "permissionType": "CUSTOMER_MANAGED|AWS_MANAGED",
            "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD",
            "tags": []
        }
    ],
    "nextToken": "string"
}
```

---

### 3.8 `list-permission-associations`

Lists associations for a specific permission. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-permission-associations \
    --permission-arn <value> \
    [--permission-version <value>] \
    [--association-status <value>] \
    [--resource-type <value>] \
    [--feature-set <value>] \
    [--default-version | --no-default-version] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--permission-arn` | **Yes** | string | -- | ARN of the permission |
| `--permission-version` | No | integer | None | Filter by version |
| `--association-status` | No | string | None | Filter by association status |
| `--resource-type` | No | string | None | Filter by resource type |
| `--feature-set` | No | string | None | Filter by feature set |
| `--default-version` | No | boolean | None | Filter by default version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "permissions": [
        {
            "arn": "string",
            "permissionVersion": "string",
            "defaultVersion": "boolean",
            "resourceType": "string",
            "status": "string",
            "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD",
            "lastUpdatedTime": "timestamp",
            "resourceShareArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.9 `list-resource-share-permissions`

Lists the permissions associated with a resource share. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-resource-share-permissions \
    --resource-share-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "permissions": [
        {
            "arn": "string",
            "version": "string",
            "defaultVersion": "boolean",
            "name": "string",
            "resourceType": "string",
            "status": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "isResourceTypeDefault": "boolean",
            "permissionType": "CUSTOMER_MANAGED|AWS_MANAGED",
            "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD",
            "tags": []
        }
    ],
    "nextToken": "string"
}
```

---

### 3.10 `associate-resource-share-permission`

Associates a permission with a resource share. Replaces any existing permission of the same resource type.

**Synopsis:**
```bash
aws ram associate-resource-share-permission \
    --resource-share-arn <value> \
    --permission-arn <value> \
    [--replace | --no-replace] \
    [--client-token <value>] \
    [--permission-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share |
| `--permission-arn` | **Yes** | string | -- | ARN of the permission to associate |
| `--replace` | No | boolean | false | Replace existing permission of the same resource type |
| `--client-token` | No | string | None | Idempotency token |
| `--permission-version` | No | integer | None | Specific version to associate |

**Output Schema:**
```json
{
    "returnValue": "boolean",
    "clientToken": "string"
}
```

---

### 3.11 `disassociate-resource-share-permission`

Disassociates a permission from a resource share.

**Synopsis:**
```bash
aws ram disassociate-resource-share-permission \
    --resource-share-arn <value> \
    --permission-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share |
| `--permission-arn` | **Yes** | string | -- | ARN of the permission to disassociate |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "returnValue": "boolean",
    "clientToken": "string"
}
```

---

### 3.12 `replace-permission-associations`

Replaces all resource shares using one permission with a different permission.

**Synopsis:**
```bash
aws ram replace-permission-associations \
    --from-permission-arn <value> \
    --from-permission-version <value> \
    --to-permission-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--from-permission-arn` | **Yes** | string | -- | ARN of the permission to replace |
| `--from-permission-version` | **Yes** | integer | -- | Version of the permission to replace |
| `--to-permission-arn` | **Yes** | string | -- | ARN of the replacement permission |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "replacePermissionAssociationsWork": {
        "id": "string",
        "fromPermissionArn": "string",
        "fromPermissionVersion": "string",
        "toPermissionArn": "string",
        "toPermissionVersion": "string",
        "status": "IN_PROGRESS|COMPLETED|FAILED",
        "statusMessage": "string",
        "creationTime": "timestamp",
        "lastUpdatedTime": "timestamp"
    },
    "clientToken": "string"
}
```

---

### 3.13 `list-replace-permission-associations-work`

Lists replacement work for permission associations. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-replace-permission-associations-work \
    [--work-ids <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-ids` | No | list(string) | None | Filter by work IDs |
| `--status` | No | string | None | Filter by status: `IN_PROGRESS`, `COMPLETED`, `FAILED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "replacePermissionAssociationsWorks": [
        {
            "id": "string",
            "fromPermissionArn": "string",
            "fromPermissionVersion": "string",
            "toPermissionArn": "string",
            "toPermissionVersion": "string",
            "status": "IN_PROGRESS|COMPLETED|FAILED",
            "statusMessage": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.14 `set-default-permission-version`

Sets the default version for a customer-managed permission.

**Synopsis:**
```bash
aws ram set-default-permission-version \
    --permission-arn <value> \
    --permission-version <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--permission-arn` | **Yes** | string | -- | ARN of the permission |
| `--permission-version` | **Yes** | integer | -- | Version to set as default |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "returnValue": "boolean",
    "clientToken": "string"
}
```

---

### 3.15 `promote-permission-created-from-policy`

Promotes a permission created from a resource-based policy to a standard customer-managed permission.

**Synopsis:**
```bash
aws ram promote-permission-created-from-policy \
    --permission-arn <value> \
    --name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--permission-arn` | **Yes** | string | -- | ARN of the permission to promote |
| `--name` | **Yes** | string | -- | Name for the promoted permission |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "permission": {
        "arn": "string",
        "version": "string",
        "defaultVersion": "boolean",
        "name": "string",
        "resourceType": "string",
        "status": "string",
        "creationTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "isResourceTypeDefault": "boolean",
        "permissionType": "CUSTOMER_MANAGED|AWS_MANAGED",
        "featureSet": "CREATED_FROM_POLICY|PROMOTING_TO_STANDARD|STANDARD",
        "tags": []
    },
    "clientToken": "string"
}
```
