# Resource Sets

### 4.1 `put-resource-set`

Creates or updates a resource set. Resource sets group resources for use in Firewall Manager policies.

**Synopsis:**
```bash
aws fms put-resource-set \
    --resource-set <value> \
    [--tag-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-set` | **Yes** | structure | -- | Resource set details (see structure below) |
| `--tag-list` | No | list | None | Tags (max 200) |

**Resource Set Structure:**
```json
{
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "UpdateToken": "string",
    "ResourceTypeList": ["string"],
    "LastUpdateTime": "timestamp",
    "ResourceSetStatus": "ACTIVE|OUT_OF_ADMIN_SCOPE"
}
```

Required fields: `Name`, `ResourceTypeList`

**Output Schema:**
```json
{
    "ResourceSet": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "UpdateToken": "string",
        "ResourceTypeList": ["string"],
        "LastUpdateTime": "timestamp",
        "ResourceSetStatus": "ACTIVE|OUT_OF_ADMIN_SCOPE"
    },
    "ResourceSetArn": "string"
}
```

---

### 4.2 `get-resource-set`

Returns the details of a resource set.

**Synopsis:**
```bash
aws fms get-resource-set \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Resource set ID (22 chars) |

**Output Schema:**
```json
{
    "ResourceSet": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "UpdateToken": "string",
        "ResourceTypeList": ["string"],
        "LastUpdateTime": "timestamp",
        "ResourceSetStatus": "ACTIVE|OUT_OF_ADMIN_SCOPE"
    },
    "ResourceSetArn": "string"
}
```

---

### 4.3 `delete-resource-set`

Deletes a resource set.

**Synopsis:**
```bash
aws fms delete-resource-set \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Resource set ID to delete |

**Output Schema:** Empty on success.

---

### 4.4 `list-resource-sets`

Returns a list of all resource sets. **Paginated.**

**Synopsis:**
```bash
aws fms list-resource-sets \
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
    "ResourceSets": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "LastUpdateTime": "timestamp",
            "ResourceSetStatus": "ACTIVE|OUT_OF_ADMIN_SCOPE"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `list-resource-set-resources`

Returns resources in a resource set. **Paginated.**

**Synopsis:**
```bash
aws fms list-resource-set-resources \
    --identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Resource set ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Items": [
        {
            "URI": "string",
            "AccountId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.6 `batch-associate-resource`

Associates resources with a resource set.

**Synopsis:**
```bash
aws fms batch-associate-resource \
    --resource-set-identifier <value> \
    --items <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-set-identifier` | **Yes** | string | -- | Resource set ID |
| `--items` | **Yes** | list(string) | -- | Resource URIs to associate |

**Output Schema:**
```json
{
    "ResourceSetIdentifier": "string",
    "FailedItems": [
        {
            "URI": "string",
            "Reason": "NOT_VALID_ARN|NOT_VALID_PARTITION|NOT_VALID_REGION|NOT_VALID_SERVICE|NOT_VALID_RESOURCE_TYPE|NOT_VALID_ACCOUNT_ID"
        }
    ]
}
```

---

### 4.7 `batch-disassociate-resource`

Disassociates resources from a resource set.

**Synopsis:**
```bash
aws fms batch-disassociate-resource \
    --resource-set-identifier <value> \
    --items <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-set-identifier` | **Yes** | string | -- | Resource set ID |
| `--items` | **Yes** | list(string) | -- | Resource URIs to disassociate |

**Output Schema:**
```json
{
    "ResourceSetIdentifier": "string",
    "FailedItems": [
        {
            "URI": "string",
            "Reason": "NOT_VALID_ARN|NOT_VALID_PARTITION|NOT_VALID_REGION|NOT_VALID_SERVICE|NOT_VALID_RESOURCE_TYPE|NOT_VALID_ACCOUNT_ID"
        }
    ]
}
```
