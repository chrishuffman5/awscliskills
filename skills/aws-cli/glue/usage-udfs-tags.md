# Usage, UDFs & Tags

## Resource Policies

### 20.1 `get-resource-policies`

Lists all resource policies. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-resource-policies \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "GetResourcePoliciesResponseList": [
        {
            "PolicyInJson": "string",
            "PolicyHash": "string",
            "CreateTime": "timestamp",
            "UpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 20.2 `get-resource-policy`

Retrieves a resource policy.

**Synopsis:**
```bash
aws glue get-resource-policy \
    [--resource-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | No | string | -- | Resource ARN (defaults to account-level catalog policy) |

**Output Schema:**
```json
{
    "PolicyInJson": "string",
    "PolicyHash": "string",
    "CreateTime": "timestamp",
    "UpdateTime": "timestamp"
}
```

---

### 20.3 `put-resource-policy`

Sets a resource policy on the Data Catalog.

**Synopsis:**
```bash
aws glue put-resource-policy \
    --policy-in-json <value> \
    [--resource-arn <value>] \
    [--policy-hash-condition <value>] \
    [--policy-exists-condition <value>] \
    [--enable-hybrid <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-in-json` | **Yes** | string | -- | IAM policy document (JSON string) |
| `--resource-arn` | No | string | -- | Resource ARN |
| `--policy-hash-condition` | No | string | -- | Hash for optimistic locking |
| `--policy-exists-condition` | No | string | -- | `MUST_EXIST`, `NOT_EXIST`, `NONE` |
| `--enable-hybrid` | No | string | -- | `TRUE` or `FALSE` |

**Output Schema:**
```json
{
    "PolicyHash": "string"
}
```

---

### 20.4 `delete-resource-policy`

Deletes a resource policy.

**Synopsis:**
```bash
aws glue delete-resource-policy \
    [--policy-hash-condition <value>] \
    [--resource-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-hash-condition` | No | string | -- | Hash for optimistic locking |
| `--resource-arn` | No | string | -- | Resource ARN |

No output on success.

---

## User-Defined Functions (UDFs)

### 20.5 `get-user-defined-function`

Retrieves a user-defined function.

**Synopsis:**
```bash
aws glue get-user-defined-function \
    --database-name <value> \
    --function-name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--function-name` | **Yes** | string | -- | Function name |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "UserDefinedFunction": {
        "FunctionName": "string",
        "DatabaseName": "string",
        "ClassName": "string",
        "OwnerName": "string",
        "OwnerType": "USER|ROLE|GROUP",
        "CreateTime": "timestamp",
        "ResourceUris": [
            {
                "ResourceType": "JAR|FILE|ARCHIVE",
                "Uri": "string"
            }
        ],
        "CatalogId": "string"
    }
}
```

---

### 20.6 `get-user-defined-functions`

Retrieves user-defined functions. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-user-defined-functions \
    --pattern <value> \
    [--catalog-id <value>] \
    [--database-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pattern` | **Yes** | string | -- | Function name pattern (supports wildcards) |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--database-name` | No | string | -- | Filter by database |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "UserDefinedFunctions": ["<UserDefinedFunction structure>"],
    "NextToken": "string"
}
```

---

### 20.7 `create-user-defined-function`

Creates a user-defined function.

**Synopsis:**
```bash
aws glue create-user-defined-function \
    --database-name <value> \
    --function-input <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--function-input` | **Yes** | structure | -- | Function definition (JSON). Must include FunctionName, ClassName, OwnerName, OwnerType |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 20.8 `update-user-defined-function`

Updates a user-defined function.

**Synopsis:**
```bash
aws glue update-user-defined-function \
    --database-name <value> \
    --function-name <value> \
    --function-input <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--function-name` | **Yes** | string | -- | Function name |
| `--function-input` | **Yes** | structure | -- | Updated function definition (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 20.9 `delete-user-defined-function`

Deletes a user-defined function.

**Synopsis:**
```bash
aws glue delete-user-defined-function \
    --database-name <value> \
    --function-name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--function-name` | **Yes** | string | -- | Function name |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

## Tags

### 20.10 `tag-resource`

Adds tags to a Glue resource.

**Synopsis:**
```bash
aws glue tag-resource \
    --resource-arn <value> \
    --tags-to-add <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags-to-add` | **Yes** | map | -- | Tags as JSON |

No output on success.

---

### 20.11 `untag-resource`

Removes tags from a Glue resource.

**Synopsis:**
```bash
aws glue untag-resource \
    --resource-arn <value> \
    --tags-to-remove <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags-to-remove` | **Yes** | list(string) | -- | Tag keys to remove |

No output on success.

---

### 20.12 `get-tags`

Lists tags for a Glue resource.

**Synopsis:**
```bash
aws glue get-tags \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": {
        "key": "value"
    }
}
```
