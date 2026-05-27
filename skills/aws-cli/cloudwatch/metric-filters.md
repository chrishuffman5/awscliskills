# Metric Filters

### 11.1 `put-metric-filter`

Creates or updates a metric filter that extracts metric data from log events.

**Synopsis:**
```bash
aws logs put-metric-filter \
    --log-group-name <value> \
    --filter-name <value> \
    --filter-pattern <value> \
    --metric-transformations <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--filter-name` | **Yes** | string | -- | Metric filter name (1-512 chars). Pattern: `[^:*]*` |
| `--filter-pattern` | **Yes** | string | -- | Filter pattern (0-1024 chars). See Filter and Pattern Syntax |
| `--metric-transformations` | **Yes** | list | -- | Metric transformation (1 item). Structure below |

**MetricTransformation structure:**
```json
{
    "metricName": "string",
    "metricNamespace": "string",
    "metricValue": "string",
    "defaultValue": double,
    "dimensions": {"string": "string"},
    "unit": "Seconds|Bytes|Count|Percent|None|..."
}
```

**Output:** None on success.

---

### 11.2 `describe-metric-filters`

Lists metric filters for a log group. **Paginated.**

**Synopsis:**
```bash
aws logs describe-metric-filters \
    [--log-group-name <value>] \
    [--filter-name-prefix <value>] \
    [--metric-name <value>] \
    [--metric-namespace <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | No | string | -- | Log group name (1-512 chars) |
| `--filter-name-prefix` | No | string | -- | Filter name prefix (1-512 chars) |
| `--metric-name` | No | string | -- | Metric name to filter by (max 255 chars) |
| `--metric-namespace` | No | string | -- | Metric namespace to filter by (max 255 chars) |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "metricFilters": [
        {
            "filterName": "string",
            "filterPattern": "string",
            "metricTransformations": [
                {
                    "metricName": "string",
                    "metricNamespace": "string",
                    "metricValue": "string",
                    "defaultValue": double,
                    "dimensions": {"string": "string"},
                    "unit": "string"
                }
            ],
            "creationTime": long,
            "logGroupName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 11.3 `delete-metric-filter`

Deletes a metric filter.

**Synopsis:**
```bash
aws logs delete-metric-filter \
    --log-group-name <value> \
    --filter-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--filter-name` | **Yes** | string | -- | Metric filter name (1-512 chars) |

**Output:** None on success.

---

### 11.4 `test-metric-filter`

Tests a filter pattern against sample log event messages.

**Synopsis:**
```bash
aws logs test-metric-filter \
    --filter-pattern <value> \
    --log-event-messages <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-pattern` | **Yes** | string | -- | Filter pattern to test (0-1024 chars) |
| `--log-event-messages` | **Yes** | list | -- | Log event messages to test against (1-50) |

**Output Schema:**
```json
{
    "matches": [
        {
            "eventNumber": long,
            "eventMessage": "string",
            "extractedValues": {"string": "string"}
        }
    ]
}
```

---
