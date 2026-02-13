# Metric Streams

### 6.1 `put-metric-stream`

Creates or updates a metric stream to send metrics to a Kinesis Data Firehose delivery stream.

**Synopsis:**
```bash
aws cloudwatch put-metric-stream \
    --name <value> \
    --firehose-arn <value> \
    --role-arn <value> \
    --output-format <value> \
    [--include-filters <value>] \
    [--exclude-filters <value>] \
    [--tags <value>] \
    [--statistics-configurations <value>] \
    [--include-linked-accounts-metrics | --no-include-linked-accounts-metrics]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Stream name (1-255 chars). Valid: A-Z, a-z, 0-9, `-`, `_` |
| `--firehose-arn` | **Yes** | string | -- | ARN of Kinesis Data Firehose delivery stream (1-1024 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with Firehose put permissions (1-1024 chars) |
| `--output-format` | **Yes** | string | -- | `json`, `opentelemetry0.7`, `opentelemetry1.0` |
| `--include-filters` | No | list | -- | Include only specified namespaces/metrics. Cannot combine with `--exclude-filters` |
| `--exclude-filters` | No | list | -- | Exclude specified namespaces/metrics. Cannot combine with `--include-filters` |
| `--tags` | No | list | -- | Key-value tags (max 50). Only for new streams |
| `--statistics-configurations` | No | list | -- | Additional statistics to stream (max 100, up to 20 stats each) |
| `--include-linked-accounts-metrics` | No | boolean | false | Include metrics from linked source accounts |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 6.2 `get-metric-stream`

Returns information about a metric stream.

**Synopsis:**
```bash
aws cloudwatch get-metric-stream \
    --name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Metric stream name (1-255 chars) |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "FirehoseArn": "string",
    "RoleArn": "string",
    "State": "string",
    "CreationDate": "timestamp",
    "LastUpdateDate": "timestamp",
    "OutputFormat": "json|opentelemetry0.7|opentelemetry1.0",
    "IncludeFilters": [{"Namespace": "string", "MetricNames": ["string"]}],
    "ExcludeFilters": [{"Namespace": "string", "MetricNames": ["string"]}],
    "StatisticsConfigurations": [
        {
            "IncludeMetrics": [{"Namespace": "string", "MetricName": "string"}],
            "AdditionalStatistics": ["string"]
        }
    ],
    "IncludeLinkedAccountsMetrics": true|false
}
```

---

### 6.3 `list-metric-streams`

Lists metric streams. **Paginated.**

**Synopsis:**
```bash
aws cloudwatch list-metric-streams \
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
    "Entries": [
        {
            "Arn": "string",
            "CreationDate": "timestamp",
            "LastUpdateDate": "timestamp",
            "Name": "string",
            "FirehoseArn": "string",
            "State": "string",
            "OutputFormat": "json|opentelemetry0.7|opentelemetry1.0"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `delete-metric-stream`

Deletes a metric stream.

**Synopsis:**
```bash
aws cloudwatch delete-metric-stream \
    --name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Metric stream name to delete (1-255 chars) |

**Output:** None on success.

---

### 6.5 `start-metric-streams`

Starts streaming for one or more stopped metric streams.

**Synopsis:**
```bash
aws cloudwatch start-metric-streams \
    --names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list | -- | Names of metric streams to start |

**Output:** None on success.

---

### 6.6 `stop-metric-streams`

Stops streaming for one or more metric streams.

**Synopsis:**
```bash
aws cloudwatch stop-metric-streams \
    --names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list | -- | Names of metric streams to stop |

**Output:** None on success.

---
