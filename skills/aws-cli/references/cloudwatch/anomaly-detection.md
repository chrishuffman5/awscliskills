# Anomaly Detection

### 4.1 `put-anomaly-detector`

Creates or updates an anomaly detection model for a CloudWatch metric.

**Synopsis:**
```bash
aws cloudwatch put-anomaly-detector \
    [--namespace <value>] \
    [--metric-name <value>] \
    [--dimensions <value>] \
    [--stat <value>] \
    [--configuration <value>] \
    [--metric-characteristics <value>] \
    [--single-metric-anomaly-detector <value>] \
    [--metric-math-anomaly-detector <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace` | No* | string | -- | Metric namespace (1-255 chars). *Use either individual params or `--single-metric-anomaly-detector` |
| `--metric-name` | No* | string | -- | Metric name (1-255 chars) |
| `--dimensions` | No | list | -- | Metric dimensions (max 30) |
| `--stat` | No* | string | -- | Statistic for the model (max 50 chars) |
| `--configuration` | No | structure | -- | Training configuration: `ExcludedTimeRanges`, `MetricTimezone` |
| `--metric-characteristics` | No | structure | -- | `PeriodicSpikes=true|false` |
| `--single-metric-anomaly-detector` | No | structure | -- | Single metric detector definition. Cannot combine with `--namespace`/`--metric-name`/`--stat` |
| `--metric-math-anomaly-detector` | No | structure | -- | Metric math detector with MetricDataQueries. Cannot combine with single metric params |

**Output:** None on success.

---

### 4.2 `describe-anomaly-detectors`

Lists anomaly detection models. **Paginated.**

**Synopsis:**
```bash
aws cloudwatch describe-anomaly-detectors \
    [--namespace <value>] \
    [--metric-name <value>] \
    [--dimensions <value>] \
    [--anomaly-detector-types <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace` | No | string | -- | Filter by namespace (1-255 chars) |
| `--metric-name` | No | string | -- | Filter by metric name (1-255 chars) |
| `--dimensions` | No | list | -- | Filter by dimensions (max 30) |
| `--anomaly-detector-types` | No | list | -- | `SINGLE_METRIC`, `METRIC_MATH` |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "AnomalyDetectors": [
        {
            "Namespace": "string",
            "MetricName": "string",
            "Dimensions": [{"Name": "string", "Value": "string"}],
            "Stat": "string",
            "Configuration": {
                "ExcludedTimeRanges": [
                    {"StartTime": "timestamp", "EndTime": "timestamp"}
                ],
                "MetricTimezone": "string"
            },
            "StateValue": "PENDING_TRAINING|TRAINED_INSUFFICIENT_DATA|TRAINED",
            "MetricCharacteristics": {"PeriodicSpikes": true|false},
            "SingleMetricAnomalyDetector": {
                "AccountId": "string",
                "Namespace": "string",
                "MetricName": "string",
                "Dimensions": [{"Name": "string", "Value": "string"}],
                "Stat": "string"
            },
            "MetricMathAnomalyDetector": {
                "MetricDataQueries": [{"Id": "string", "MetricStat": {}, "Expression": "string"}]
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 4.3 `delete-anomaly-detector`

Deletes an anomaly detection model.

**Synopsis:**
```bash
aws cloudwatch delete-anomaly-detector \
    [--namespace <value>] \
    [--metric-name <value>] \
    [--dimensions <value>] \
    [--stat <value>] \
    [--single-metric-anomaly-detector <value>] \
    [--metric-math-anomaly-detector <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace` | No* | string | -- | Metric namespace. *Use either individual params or detector structure |
| `--metric-name` | No* | string | -- | Metric name |
| `--dimensions` | No | list | -- | Metric dimensions |
| `--stat` | No* | string | -- | Statistic |
| `--single-metric-anomaly-detector` | No | structure | -- | Single metric detector to delete |
| `--metric-math-anomaly-detector` | No | structure | -- | Metric math detector to delete |

**Output:** None on success.

---
