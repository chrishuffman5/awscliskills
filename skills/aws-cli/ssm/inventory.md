# Inventory

### 8.1 `put-inventory`

Submits inventory data for a managed instance. Used by the SSM Agent to report installed applications, network configuration, and other system data.

**Synopsis:**
```bash
aws ssm put-inventory \
    --instance-id <value> \
    --items <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID |
| `--items` | **Yes** | list | -- | Inventory items to submit |

**Inventory Item Structure:**
```json
[
    {
        "TypeName": "string",
        "SchemaVersion": "string",
        "CaptureTime": "string",
        "ContentHash": "string",
        "Content": [
            {
                "key": "value"
            }
        ],
        "Context": {
            "key": "value"
        }
    }
]
```

**Output Schema:**
```json
{
    "Message": "string"
}
```

---

### 8.2 `get-inventory`

Queries inventory data across managed instances. **Paginated operation.**

**Synopsis:**
```bash
aws ssm get-inventory \
    [--filters <value>] \
    [--aggregators <value>] \
    [--result-attributes <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Inventory filters |
| `--aggregators` | No | list | None | Aggregation expressions |
| `--result-attributes` | No | list | None | Result attributes to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
[
    {
        "Key": "string",
        "Values": ["string"],
        "Type": "Equal|NotEqual|BeginWith|LessThan|GreaterThan|Exists"
    }
]
```

**Output Schema:**
```json
{
    "Entities": [
        {
            "Id": "string",
            "Data": {
                "TypeName": {
                    "TypeName": "string",
                    "SchemaVersion": "string",
                    "CaptureTime": "string",
                    "ContentHash": "string",
                    "Content": []
                }
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 8.3 `get-inventory-schema`

Returns the schema for available inventory types. **Paginated operation.**

**Synopsis:**
```bash
aws ssm get-inventory-schema \
    [--type-name <value>] \
    [--aggregator | --no-aggregator] \
    [--sub-type | --no-sub-type] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type-name` | No | string | None | Specific inventory type (e.g. `AWS:Application`) |
| `--aggregator` | No | boolean | false | Return aggregator schemas |
| `--sub-type` | No | boolean | false | Return sub-type schemas |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Schemas": [
        {
            "TypeName": "string",
            "Version": "string",
            "Attributes": [
                {
                    "Name": "string",
                    "DataType": "string|number"
                }
            ],
            "DisplayName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.4 `list-inventory-entries`

Lists inventory entries for a specific instance and inventory type.

**Synopsis:**
```bash
aws ssm list-inventory-entries \
    --instance-id <value> \
    --type-name <value> \
    [--filters <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID |
| `--type-name` | **Yes** | string | -- | Inventory type (e.g. `AWS:Application`) |
| `--filters` | No | list | None | Inventory filters |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results to return |

**Output Schema:**
```json
{
    "TypeName": "string",
    "InstanceId": "string",
    "SchemaVersion": "string",
    "CaptureTime": "string",
    "Entries": [
        {
            "key": "value"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `delete-inventory`

Deletes a custom inventory type and all associated data.

**Synopsis:**
```bash
aws ssm delete-inventory \
    --type-name <value> \
    --schema-delete-option <value> \
    [--dry-run | --no-dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type-name` | **Yes** | string | -- | Custom inventory type name |
| `--schema-delete-option` | **Yes** | string | -- | Delete option: `DisableSchema` or `DeleteSchema` |
| `--dry-run` | No | boolean | false | Preview the deletion without executing |

**Output Schema:**
```json
{
    "DeletionId": "string",
    "TypeName": "string",
    "DeletionSummary": {
        "TotalCount": "integer",
        "RemainingCount": "integer",
        "SummaryItems": [
            {
                "Version": "string",
                "Count": "integer",
                "RemainingCount": "integer"
            }
        ]
    }
}
```
