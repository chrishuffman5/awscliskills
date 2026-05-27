# Data Tables

### 22.1 `create-data-table`

Creates a data table for the specified instance.

**Synopsis:**
```bash
aws connect create-data-table \
    --instance-id <value> \
    --name <value> \
    --time-zone <value> \
    --value-lock-level <value> \
    --status <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Table name (1-127 chars) |
| `--time-zone` | **Yes** | string | -- | IANA time zone |
| `--value-lock-level` | **Yes** | string | -- | `NONE`, `DATA_TABLE`, `PRIMARY_VALUE`, `ATTRIBUTE`, `VALUE` |
| `--status` | **Yes** | string | -- | `PUBLISHED` or `SAVED` |
| `--description` | No | string | None | Description (0-250 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string",
    "LockVersion": {
        "DataTable": "string",
        "Attribute": "string",
        "PrimaryValues": "string",
        "Value": "string"
    }
}
```

---

### 22.2 `describe-data-table`

Describes a data table.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-table-id` | **Yes** | string | -- | Data table ID |

**Output Schema:**
```json
{
    "DataTable": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "TimeZone": "string",
        "ValueLockLevel": "string",
        "Status": "PUBLISHED|SAVED",
        "Tags": { "key": "value" },
        "LockVersion": {},
        "LastModifiedTime": "timestamp",
        "CreatedTime": "timestamp"
    }
}
```

---

### 22.3 `list-data-tables`

Lists data tables. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

---

### 22.4 `update-data-table-metadata`

Updates data table metadata (name, description).

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-table-id` | **Yes** | string | -- | Data table ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |

**Output:** None

---

### 22.5 `delete-data-table`

Deletes a data table.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-table-id` | **Yes** | string | -- | Data table ID |

**Output:** None

---

### 22.6 `search-data-tables`

Searches data tables. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-criteria` | No | structure | None | Search criteria |

---

### 22.7 `create-data-table-attribute`

Creates an attribute (column) in a data table.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-table-id` | **Yes** | string | -- | Data table ID |
| `--attribute-name` | **Yes** | string | -- | Attribute name |
| `--attribute-type` | **Yes** | string | -- | Attribute data type |

---

### 22.8-22.11 Attribute Commands

`describe-data-table-attribute`, `list-data-table-attributes`, `update-data-table-attribute`, `delete-data-table-attribute` manage data table attributes. All require `--instance-id` and `--data-table-id`.

---

### 22.12-22.14 Primary Value Commands

`list-data-table-primary-values`, `update-data-table-primary-values` manage primary values (rows) in data tables. Require `--instance-id` and `--data-table-id`.

---

### 22.15-22.19 Value Commands

`list-data-table-values`, `batch-create-data-table-value`, `batch-describe-data-table-value`, `batch-update-data-table-value`, `batch-delete-data-table-value` manage individual cell values. Require `--instance-id` and `--data-table-id`.

**batch-create-data-table-value output:**
```json
{
    "SuccessfulRequests": [ { "PrimaryValue": "string", "AttributeName": "string" } ],
    "FailedRequests": [ { "PrimaryValue": "string", "AttributeName": "string", "FailureCode": "string", "FailureMessage": "string" } ]
}
```

---

### 22.20 `evaluate-data-table-values`

Evaluates expressions against data table values.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-table-id` | **Yes** | string | -- | Data table ID |
| `--expression` | **Yes** | string | -- | Expression to evaluate |

**Output Schema:**
```json
{
    "Result": "string"
}
```
