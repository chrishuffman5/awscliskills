# Insight Rules

### 5.1 `put-insight-rule`

Creates or updates a Contributor Insights rule.

**Synopsis:**
```bash
aws cloudwatch put-insight-rule \
    --rule-name <value> \
    --rule-definition <value> \
    [--rule-state <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Rule name (1-128 chars) |
| `--rule-definition` | **Yes** | string | -- | JSON rule definition |
| `--rule-state` | No | string | -- | `ENABLED` or `DISABLED` |
| `--tags` | No | list | -- | Key-value tags |

**Output:** None on success.

---

### 5.2 `describe-insight-rules`

Lists Contributor Insights rules. **Paginated.**

**Synopsis:**
```bash
aws cloudwatch describe-insight-rules \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "InsightRules": [
        {
            "Name": "string",
            "State": "string",
            "Schema": "string",
            "Definition": "string",
            "ManagedRule": true|false
        }
    ],
    "NextToken": "string"
}
```

---

### 5.3 `get-insight-rule-report`

Returns data collected by a Contributor Insights rule.

**Synopsis:**
```bash
aws cloudwatch get-insight-rule-report \
    --rule-name <value> \
    --start-time <value> \
    --end-time <value> \
    --period <value> \
    [--max-contributor-count <value>] \
    [--metrics <value>] \
    [--order-by <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Rule name (1-128 chars) |
| `--start-time` | **Yes** | timestamp | -- | Start of time range |
| `--end-time` | **Yes** | timestamp | -- | End of time range |
| `--period` | **Yes** | integer | -- | Period in seconds (min 1) |
| `--max-contributor-count` | No | integer | -- | Max contributors to include |
| `--metrics` | No | list | -- | Metrics to return |
| `--order-by` | No | string | -- | Ordering metric |

**Output Schema:**
```json
{
    "KeyLabels": ["string"],
    "AggregationStatistic": "string",
    "AggregateValue": double,
    "ApproximateUniqueCount": long,
    "Contributors": [
        {
            "Keys": ["string"],
            "ApproximateAggregateValue": double,
            "Datapoints": [
                {
                    "Timestamp": "timestamp",
                    "ApproximateValue": double
                }
            ]
        }
    ],
    "MetricDatapoints": [
        {
            "Timestamp": "timestamp",
            "UniqueContributors": double,
            "MaxContributorValue": double,
            "SampleCount": double,
            "Average": double,
            "Sum": double,
            "Minimum": double,
            "Maximum": double
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `delete-insight-rules`

Deletes one or more Contributor Insights rules.

**Synopsis:**
```bash
aws cloudwatch delete-insight-rules \
    --rule-names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-names` | **Yes** | list | -- | Names of rules to delete |

**Output Schema:**
```json
{
    "Failures": [
        {
            "FailureResource": "string",
            "ExceptionType": "string",
            "FailureCode": "string",
            "FailureDescription": "string"
        }
    ]
}
```

---

### 5.5 `enable-insight-rules`

Enables one or more Contributor Insights rules.

**Synopsis:**
```bash
aws cloudwatch enable-insight-rules \
    --rule-names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-names` | **Yes** | list | -- | Rule names to enable |

**Output Schema:**
```json
{
    "Failures": [
        {
            "FailureResource": "string",
            "ExceptionType": "string",
            "FailureCode": "string",
            "FailureDescription": "string"
        }
    ]
}
```

---

### 5.6 `disable-insight-rules`

Disables one or more Contributor Insights rules.

**Synopsis:**
```bash
aws cloudwatch disable-insight-rules \
    --rule-names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-names` | **Yes** | list | -- | Rule names to disable |

**Output Schema:**
```json
{
    "Failures": [
        {
            "FailureResource": "string",
            "ExceptionType": "string",
            "FailureCode": "string",
            "FailureDescription": "string"
        }
    ]
}
```

---
