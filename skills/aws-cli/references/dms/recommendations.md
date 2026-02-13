# Recommendations

DMS recommendations provide right-sizing guidance for replication instances and target database engines.

### 12.1 `batch-start-recommendations`

Starts batch recommendations for multiple source databases.

**Synopsis:**
```bash
aws dms batch-start-recommendations \
    [--data <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data` | No | list | -- | List of recommendation request entries |

**Data Entry Structure:**
```json
[
    {
        "DatabaseId": "string",
        "Settings": {
            "InstanceSizingType": "string",
            "WorkloadType": "string"
        }
    }
]
```

**Output Schema:**
```json
{
    "ErrorEntries": [
        {
            "DatabaseId": "string",
            "Message": "string",
            "Code": "string"
        }
    ]
}
```

---

### 12.2 `start-recommendations`

Starts recommendations for a single source database.

**Synopsis:**
```bash
aws dms start-recommendations \
    --database-id <value> \
    --settings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-id` | **Yes** | string | -- | Database ID from Fleet Advisor |
| `--settings` | **Yes** | structure | -- | Settings: `InstanceSizingType`, `WorkloadType` |

**Output Schema:** None (HTTP 200 on success).

---

### 12.3 `describe-recommendations`

Returns a paginated list of target engine recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-recommendations \
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
| `--filters` | No | list | -- | Filters: `database-id`, `status` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Recommendations": [
        {
            "DatabaseId": "string",
            "EngineName": "string",
            "CreatedDate": "string",
            "Status": "string",
            "Preferred": "boolean",
            "Settings": {
                "InstanceSizingType": "string",
                "WorkloadType": "string"
            },
            "Data": {
                "RdsEngine": {
                    "RequirementsToTarget": {},
                    "TargetConfiguration": {}
                }
            }
        }
    ]
}
```

---

### 12.4 `describe-recommendation-limitations`

Returns a paginated list of limitations for recommendations for a given migration task. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-recommendation-limitations \
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
| `--filters` | No | list | -- | Filters: `database-id` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Limitations": [
        {
            "DatabaseId": "string",
            "EngineName": "string",
            "Name": "string",
            "Description": "string",
            "Impact": "string",
            "Type": "string"
        }
    ]
}
```
