# Dashboards

### 3.1 `put-dashboard`

Creates or updates a dashboard. If a dashboard with the name does not exist, a new one is created.

**Synopsis:**
```bash
aws cloudwatch put-dashboard \
    --dashboard-name <value> \
    --dashboard-body <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dashboard-name` | **Yes** | string | -- | Dashboard name (max 255 chars). Valid: A-Z, a-z, 0-9, `-`, `_` |
| `--dashboard-body` | **Yes** | string | -- | Dashboard configuration as JSON string. See Dashboard Body Structure and Syntax |

**Output Schema:**
```json
{
    "DashboardValidationMessages": [
        {
            "DataPath": "string",
            "Message": "string"
        }
    ]
}
```

---

### 3.2 `get-dashboard`

Retrieves a dashboard's details including its body JSON.

**Synopsis:**
```bash
aws cloudwatch get-dashboard \
    --dashboard-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dashboard-name` | **Yes** | string | -- | Dashboard name |

**Output Schema:**
```json
{
    "DashboardArn": "string",
    "DashboardBody": "string",
    "DashboardName": "string"
}
```

---

### 3.3 `list-dashboards`

Lists dashboards. **Paginated.**

**Synopsis:**
```bash
aws cloudwatch list-dashboards \
    [--dashboard-name-prefix <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dashboard-name-prefix` | No | string | -- | Filter by name prefix |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "DashboardEntries": [
        {
            "DashboardName": "string",
            "DashboardArn": "string",
            "LastModified": "timestamp",
            "Size": long
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `delete-dashboards`

Deletes one or more dashboards.

**Synopsis:**
```bash
aws cloudwatch delete-dashboards \
    --dashboard-names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dashboard-names` | **Yes** | list | -- | Names of dashboards to delete |

**Output:** None on success.

---
