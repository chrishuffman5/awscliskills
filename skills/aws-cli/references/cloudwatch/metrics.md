# Metrics

### 1.1 `put-metric-data`

Publishes metric data points to CloudWatch. Up to 1000 metrics per call.

**Synopsis:**
```bash
aws cloudwatch put-metric-data \
    --namespace <value> \
    [--metric-data <value>] \
    [--metric-name <value>] \
    [--timestamp <value>] \
    [--unit <value>] \
    [--value <value>] \
    [--dimensions <value>] \
    [--statistic-values <value>] \
    [--storage-resolution <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace` | **Yes** | string | -- | Namespace for the metric data (1-255 chars). Cannot begin with `AWS/`. Pattern: `[^:].*` |
| `--metric-data` | No | list | -- | Array of MetricDatum structures (max 1000). Use for structured input |
| `--metric-name` | No | string | -- | Name of the metric (1-255 chars). Shorthand alternative to `--metric-data` |
| `--timestamp` | No | timestamp | current time | Timestamp for the data point |
| `--unit` | No | string | None | Unit of measure: `Seconds`, `Microseconds`, `Milliseconds`, `Bytes`, `Kilobytes`, `Megabytes`, `Gigabytes`, `Terabytes`, `Bits`, `Kilobits`, `Megabits`, `Gigabits`, `Terabits`, `Percent`, `Count`, `Bytes/Second`, `Kilobytes/Second`, `Megabytes/Second`, `Gigabytes/Second`, `Terabytes/Second`, `Bits/Second`, `Kilobits/Second`, `Megabits/Second`, `Gigabits/Second`, `Terabits/Second`, `Count/Second`, `None` |
| `--value` | No | double | -- | Numeric metric value. Range: -2^360 to 2^360 |
| `--dimensions` | No | string | -- | Name=Value pairs (max 30). Example: `InstanceID=i-123,InstanceType=m1.small` |
| `--statistic-values` | No | string | -- | Pre-aggregated stats: `SampleCount=N,Sum=N,Minimum=N,Maximum=N` |
| `--storage-resolution` | No | integer | 60 | `1` for high-resolution (sub-minute), `60` for standard (1-minute) |

**Output:** None on success.

---

### 1.2 `get-metric-data`

Retrieves metric values using MetricDataQuery structures. Supports math expressions and Metrics Insights queries. **Paginated.**

**Synopsis:**
```bash
aws cloudwatch get-metric-data \
    --metric-data-queries <value> \
    --start-time <value> \
    --end-time <value> \
    [--scan-by <value>] \
    [--label-options <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-data-queries` | **Yes** | list | -- | MetricDataQuery structures (max 500). Each specifies a metric, math expression, or Metrics Insights query |
| `--start-time` | **Yes** | timestamp | -- | Earliest data to return (inclusive). Rounded based on age |
| `--end-time` | **Yes** | timestamp | -- | Latest data to return (exclusive) |
| `--scan-by` | No | string | `TimestampDescending` | `TimestampDescending` (newest first) or `TimestampAscending` (oldest first) |
| `--label-options` | No | structure | -- | Timezone for labels. Format: `Timezone=+/-HHMM` |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token from previous call |
| `--page-size` | No | integer | -- | Items per API call |

**MetricDataQuery structure:**
```json
{
    "Id": "string",
    "MetricStat": {
        "Metric": {
            "Namespace": "string",
            "MetricName": "string",
            "Dimensions": [{"Name": "string", "Value": "string"}]
        },
        "Period": integer,
        "Stat": "string",
        "Unit": "string"
    },
    "Expression": "string",
    "Label": "string",
    "ReturnData": true|false,
    "Period": integer,
    "AccountId": "string"
}
```

**Output Schema:**
```json
{
    "MetricDataResults": [
        {
            "Id": "string",
            "Label": "string",
            "Timestamps": ["timestamp"],
            "Values": [double],
            "StatusCode": "Complete|PartialData|InternalError|Forbidden",
            "Messages": [{"Code": "string", "Value": "string"}]
        }
    ],
    "NextToken": "string",
    "Messages": [{"Code": "string", "Value": "string"}]
}
```

---

### 1.3 `get-metric-statistics`

Retrieves statistics for a specific metric. For more flexible queries, use `get-metric-data`.

**Synopsis:**
```bash
aws cloudwatch get-metric-statistics \
    --namespace <value> \
    --metric-name <value> \
    --start-time <value> \
    --end-time <value> \
    --period <value> \
    [--dimensions <value>] \
    [--statistics <value>] \
    [--extended-statistics <value>] \
    [--unit <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace` | **Yes** | string | -- | Metric namespace (1-255 chars) |
| `--metric-name` | **Yes** | string | -- | Metric name (1-255 chars) |
| `--start-time` | **Yes** | timestamp | -- | Start of data range (inclusive). ISO 8601 UTC |
| `--end-time` | **Yes** | timestamp | -- | End of data range (exclusive). ISO 8601 UTC |
| `--period` | **Yes** | integer | -- | Granularity in seconds. Must be multiple of 60 (or 1/5/10/20/30/60 for high-res) |
| `--dimensions` | No | list | -- | Dimensions to filter (max 30). Shorthand: `Name=string,Value=string` |
| `--statistics` | No | list | -- | Statistics to return (1-5): `SampleCount`, `Average`, `Sum`, `Minimum`, `Maximum` |
| `--extended-statistics` | No | list | -- | Percentile statistics (1-10): e.g., `p90`, `p99.5` |
| `--unit` | No | string | -- | Unit filter. Only data matching this unit is returned |

**Output Schema:**
```json
{
    "Label": "string",
    "Datapoints": [
        {
            "Timestamp": "timestamp",
            "SampleCount": double,
            "Average": double,
            "Sum": double,
            "Minimum": double,
            "Maximum": double,
            "Unit": "string",
            "ExtendedStatistics": {"string": double}
        }
    ]
}
```

---

### 1.4 `list-metrics`

Lists available metrics. **Paginated.**

**Synopsis:**
```bash
aws cloudwatch list-metrics \
    [--namespace <value>] \
    [--metric-name <value>] \
    [--dimensions <value>] \
    [--recently-active <value>] \
    [--include-linked-accounts | --no-include-linked-accounts] \
    [--owning-account <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace` | No | string | -- | Filter by namespace (exact match, 1-255 chars) |
| `--metric-name` | No | string | -- | Filter by metric name (exact match, 1-255 chars) |
| `--dimensions` | No | list | -- | Filter by dimensions (max 10). `Name` required, `Value` optional |
| `--recently-active` | No | string | -- | Set to `PT3H` to show only metrics with data in past 3 hours |
| `--include-linked-accounts` | No | boolean | false | Include metrics from linked source accounts |
| `--owning-account` | No | string | -- | Return metrics from specific source account only |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "Metrics": [
        {
            "Namespace": "string",
            "MetricName": "string",
            "Dimensions": [{"Name": "string", "Value": "string"}]
        }
    ],
    "NextToken": "string",
    "OwningAccounts": ["string"]
}
```

---

### 1.5 `get-metric-widget-image`

Retrieves a snapshot graph of CloudWatch metrics as a PNG image.

**Synopsis:**
```bash
aws cloudwatch get-metric-widget-image \
    --metric-widget <value> \
    [--output-format <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-widget` | **Yes** | string | -- | JSON string defining the metric widget (same format as dashboard widget) |
| `--output-format` | No | string | `png` | Image format: `png` |

**Output Schema:**
```json
{
    "MetricWidgetImage": "blob"
}
```

---
