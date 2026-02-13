# Billing Views

### 1.1 `create-billing-view`

Creates a custom billing view with data filters and source views.

**Synopsis:**
```bash
aws billing create-billing-view \
    --name <value> \
    --source-views <value> \
    [--description <value>] \
    [--data-filter-expression <value>] \
    [--client-token <value>] \
    [--resource-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Billing view name (1-128 chars) |
| `--source-views` | **Yes** | list(string) | -- | Source billing view ARNs (1-10 items) |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--data-filter-expression` | No | structure | None | Filter by LINKED_ACCOUNT, Tags, CostCategories, or timeRange |
| `--client-token` | No | string | None | Idempotency token |
| `--resource-tags` | No | list | None | Tags for the billing view (max 200) |

**Data Filter Expression Structure:**
```json
{
    "dimensions": {
        "key": "LINKED_ACCOUNT",
        "values": ["string"]
    },
    "tags": {
        "key": "string",
        "values": ["string"]
    },
    "costCategories": {
        "key": "string",
        "values": ["string"]
    },
    "timeRange": {
        "beginDateInclusive": "timestamp",
        "endDateInclusive": "timestamp"
    }
}
```

**Output Schema:**
```json
{
    "arn": "string",
    "createdAt": "timestamp"
}
```

---

### 1.2 `delete-billing-view`

Deletes the specified billing view.

**Synopsis:**
```bash
aws billing delete-billing-view \
    --arn <value> \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the billing view to delete |
| `--force` | No | boolean | false | Force deletion even if derived resources exist |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 1.3 `get-billing-view`

Returns metadata and configuration for the specified billing view.

**Synopsis:**
```bash
aws billing get-billing-view \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the billing view |

**Output Schema:**
```json
{
    "billingView": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "billingViewType": "PRIMARY|BILLING_GROUP|CUSTOM|BILLING_TRANSFER|BILLING_TRANSFER_SHOWBACK",
        "ownerAccountId": "string",
        "sourceAccountId": "string",
        "dataFilterExpression": {
            "dimensions": {
                "key": "LINKED_ACCOUNT",
                "values": ["string"]
            },
            "tags": {
                "key": "string",
                "values": ["string"]
            },
            "costCategories": {
                "key": "string",
                "values": ["string"]
            },
            "timeRange": {
                "beginDateInclusive": "timestamp",
                "endDateInclusive": "timestamp"
            }
        },
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "derivedViewCount": "integer",
        "sourceViewCount": "integer",
        "viewDefinitionLastUpdatedAt": "timestamp",
        "healthStatus": {
            "statusCode": "HEALTHY|UNHEALTHY|CREATING|UPDATING",
            "statusReasons": ["string"]
        }
    }
}
```

---

### 1.4 `list-billing-views`

Lists billing views with optional filters. **Paginated operation.**

**Synopsis:**
```bash
aws billing list-billing-views \
    [--active-time-range <value>] \
    [--arns <value>] \
    [--billing-view-types <value>] \
    [--names <value>] \
    [--owner-account-id <value>] \
    [--source-account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--active-time-range` | No | structure | None | Time range (within one calendar month). Shorthand: `activeAfterInclusive=timestamp,activeBeforeInclusive=timestamp` |
| `--arns` | No | list(string) | None | Filter by billing view ARNs (max 10) |
| `--billing-view-types` | No | list(string) | None | Filter by type: `PRIMARY`, `BILLING_GROUP`, `CUSTOM`, `BILLING_TRANSFER`, `BILLING_TRANSFER_SHOWBACK` |
| `--names` | No | list | None | Filter by name with search option (`STARTS_WITH`) |
| `--owner-account-id` | No | string | None | Filter by owner account ID (12 digits) |
| `--source-account-id` | No | string | None | Filter by source account ID (12 digits) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "billingViews": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "ownerAccountId": "string",
            "sourceAccountId": "string",
            "billingViewType": "PRIMARY|BILLING_GROUP|CUSTOM|BILLING_TRANSFER|BILLING_TRANSFER_SHOWBACK",
            "healthStatus": {
                "statusCode": "HEALTHY|UNHEALTHY|CREATING|UPDATING",
                "statusReasons": ["string"]
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-billing-view`

Updates a billing view's name, description, or data filter expression.

**Synopsis:**
```bash
aws billing update-billing-view \
    --arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--data-filter-expression <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the billing view to update |
| `--name` | No | string | None | New name (1-128 chars) |
| `--description` | No | string | None | New description (max 1024 chars) |
| `--data-filter-expression` | No | structure | None | New filter expression |

**Output Schema:**
```json
{
    "arn": "string",
    "updatedAt": "timestamp"
}
```

---

### 1.6 `associate-source-views`

Associates source billing views with an existing billing view.

**Synopsis:**
```bash
aws billing associate-source-views \
    --arn <value> \
    --source-views <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the billing view |
| `--source-views` | **Yes** | list(string) | -- | Source billing view ARNs to associate (1-10 items) |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 1.7 `disassociate-source-views`

Removes source billing views from an existing billing view.

**Synopsis:**
```bash
aws billing disassociate-source-views \
    --arn <value> \
    --source-views <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the billing view |
| `--source-views` | **Yes** | list(string) | -- | Source billing view ARNs to disassociate (1-10 items) |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 1.8 `list-source-views-for-billing-view`

Lists source views associated with a billing view. **Paginated operation.**

**Synopsis:**
```bash
aws billing list-source-views-for-billing-view \
    --arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the billing view |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "sourceViews": ["string"],
    "nextToken": "string"
}
```

---

### 1.9 `get-resource-policy`

Gets the resource-based policy attached to a billing view.

**Synopsis:**
```bash
aws billing get-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the billing view resource |

**Output Schema:**
```json
{
    "resourceArn": "string",
    "policy": "string"
}
```

| Field | Description |
|-------|-------------|
| `resourceArn` | ARN of the billing view resource |
| `policy` | The resource-based policy document in JSON format |
