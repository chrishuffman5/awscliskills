# Filters

### 3.1 `create-filter`

Creates a filter using the specified finding criteria.

**Synopsis:**
```bash
aws guardduty create-filter \
    --detector-id <value> \
    --name <value> \
    [--description <value>] \
    [--action <value>] \
    [--rank <value>] \
    --finding-criteria <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--name` | **Yes** | string | -- | Filter name (3-64 chars; alphanumeric, period, underscore, dash) |
| `--description` | No | string | None | Filter description (0-512 chars) |
| `--action` | No | string | `NOOP` | Action for matching findings: `NOOP` or `ARCHIVE` |
| `--rank` | No | integer | None | Filter rank/priority (1-100) |
| `--finding-criteria` | **Yes** | structure | -- | Criteria for filtering findings |
| `--client-token` | No | string | None | Idempotency token (0-64 chars) |
| `--tags` | No | map | None | Tags to add (max 200) |

**Finding Criteria Structure:**
```json
{
    "Criterion": {
        "string": {
            "Eq": ["string"],
            "Neq": ["string"],
            "Gt": "integer",
            "Gte": "integer",
            "Lt": "integer",
            "Lte": "integer",
            "Equals": ["string"],
            "NotEquals": ["string"],
            "GreaterThan": "long",
            "GreaterThanOrEqual": "long",
            "LessThan": "long",
            "LessThanOrEqual": "long"
        }
    }
}
```

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 3.2 `delete-filter`

Deletes the filter specified by the filter name.

**Synopsis:**
```bash
aws guardduty delete-filter \
    --detector-id <value> \
    --filter-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--filter-name` | **Yes** | string | -- | Name of the filter to delete |

**Output:** None (HTTP 200 on success)

---

### 3.3 `get-filter`

Returns the details of the filter specified by the filter name.

**Synopsis:**
```bash
aws guardduty get-filter \
    --detector-id <value> \
    --filter-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--filter-name` | **Yes** | string | -- | Name of the filter to retrieve |

**Output Schema:**
```json
{
    "Name": "string",
    "Description": "string",
    "Action": "NOOP|ARCHIVE",
    "Rank": "integer",
    "FindingCriteria": {
        "Criterion": {
            "string": {
                "Eq": ["string"],
                "Neq": ["string"],
                "Gt": "integer",
                "Gte": "integer",
                "Lt": "integer",
                "Lte": "integer",
                "Equals": ["string"],
                "NotEquals": ["string"],
                "GreaterThan": "long",
                "GreaterThanOrEqual": "long",
                "LessThan": "long",
                "LessThanOrEqual": "long"
            }
        }
    },
    "Tags": {
        "string": "string"
    }
}
```

---

### 3.4 `list-filters`

Returns a paginated list of the current filters. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-filters \
    --detector-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (1-50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FilterNames": ["string"],
    "NextToken": "string"
}
```

---

### 3.5 `update-filter`

Updates the filter specified by the filter name.

**Synopsis:**
```bash
aws guardduty update-filter \
    --detector-id <value> \
    --filter-name <value> \
    [--description <value>] \
    [--action <value>] \
    [--rank <value>] \
    [--finding-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--filter-name` | **Yes** | string | -- | Name of the filter to update |
| `--description` | No | string | None | New filter description |
| `--action` | No | string | None | New action: `NOOP` or `ARCHIVE` |
| `--rank` | No | integer | None | New filter rank (1-100) |
| `--finding-criteria` | No | structure | None | New finding criteria |

**Output Schema:**
```json
{
    "Name": "string"
}
```
