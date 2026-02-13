# Alarms

### 2.1 `put-metric-alarm`

Creates or updates a metric alarm. Supports static threshold, anomaly detection, and metric math alarms.

**Synopsis:**
```bash
aws cloudwatch put-metric-alarm \
    --alarm-name <value> \
    --evaluation-periods <value> \
    --comparison-operator <value> \
    [--alarm-description <value>] \
    [--actions-enabled | --no-actions-enabled] \
    [--ok-actions <value>] \
    [--alarm-actions <value>] \
    [--insufficient-data-actions <value>] \
    [--metric-name <value>] \
    [--namespace <value>] \
    [--statistic <value>] \
    [--extended-statistic <value>] \
    [--dimensions <value>] \
    [--period <value>] \
    [--unit <value>] \
    [--datapoints-to-alarm <value>] \
    [--threshold <value>] \
    [--treat-missing-data <value>] \
    [--evaluate-low-sample-count-percentile <value>] \
    [--metrics <value>] \
    [--tags <value>] \
    [--threshold-metric-id <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | **Yes** | string | -- | Alarm name (1-255 chars, unique per Region) |
| `--evaluation-periods` | **Yes** | integer | -- | Number of periods to evaluate (min 1) |
| `--comparison-operator` | **Yes** | string | -- | `GreaterThanOrEqualToThreshold`, `GreaterThanThreshold`, `LessThanThreshold`, `LessThanOrEqualToThreshold`, `LessThanLowerOrGreaterThanUpperThreshold`, `LessThanLowerThreshold`, `GreaterThanUpperThreshold` |
| `--alarm-description` | No | string | -- | Description (0-1024 chars) |
| `--actions-enabled` | No | boolean | true | Whether actions execute on state changes |
| `--ok-actions` | No | list | -- | ARNs for OK state (max 5) |
| `--alarm-actions` | No | list | -- | ARNs for ALARM state (max 5) |
| `--insufficient-data-actions` | No | list | -- | ARNs for INSUFFICIENT_DATA state (max 5) |
| `--metric-name` | No* | string | -- | Metric name (1-255 chars). *Required if `--metrics` not specified |
| `--namespace` | No* | string | -- | Metric namespace (1-255 chars). *Required if `--metrics` not specified |
| `--statistic` | No | string | -- | `SampleCount`, `Average`, `Sum`, `Minimum`, `Maximum` |
| `--extended-statistic` | No | string | -- | Percentile statistic (e.g., `p90`) |
| `--dimensions` | No | list | -- | Metric dimensions (max 30). Shorthand: `Name=string,Value=string` |
| `--period` | No* | integer | -- | Period in seconds. *Required for static threshold alarms |
| `--unit` | No | string | -- | Unit of measure |
| `--datapoints-to-alarm` | No | integer | same as evaluation-periods | M out of N breaching datapoints to trigger alarm |
| `--threshold` | No* | double | -- | Threshold value. *Required for static threshold alarms |
| `--treat-missing-data` | No | string | `missing` | `breaching`, `notBreaching`, `ignore`, `missing` |
| `--evaluate-low-sample-count-percentile` | No | string | -- | `evaluate` or `ignore` (for percentile alarms) |
| `--metrics` | No* | list | -- | MetricDataQuery array (max 20). *Required if `--metric-name` not specified |
| `--tags` | No | list | -- | Key-value tags (max 50) |
| `--threshold-metric-id` | No | string | -- | ID of ANOMALY_DETECTION_BAND function for anomaly detection alarms |

**Output:** None on success.

---

### 2.2 `put-composite-alarm`

Creates or updates a composite alarm that uses an alarm rule expression combining other alarms.

**Synopsis:**
```bash
aws cloudwatch put-composite-alarm \
    --alarm-name <value> \
    --alarm-rule <value> \
    [--actions-enabled | --no-actions-enabled] \
    [--alarm-actions <value>] \
    [--alarm-description <value>] \
    [--insufficient-data-actions <value>] \
    [--ok-actions <value>] \
    [--tags <value>] \
    [--actions-suppressor <value>] \
    [--actions-suppressor-wait-period <value>] \
    [--actions-suppressor-extension-period <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | **Yes** | string | -- | Composite alarm name (1-255 chars, unique per Region) |
| `--alarm-rule` | **Yes** | string | -- | Rule expression using `ALARM()`, `OK()`, `INSUFFICIENT_DATA()` with AND/OR/NOT (1-10240 chars) |
| `--actions-enabled` | No | boolean | true | Whether actions execute on state changes |
| `--alarm-actions` | No | list | -- | ARNs for ALARM state (max 5) |
| `--alarm-description` | No | string | -- | Description (0-1024 chars) |
| `--insufficient-data-actions` | No | list | -- | ARNs for INSUFFICIENT_DATA state (max 5) |
| `--ok-actions` | No | list | -- | ARNs for OK state (max 5) |
| `--tags` | No | list | -- | Key-value tags (max 50) |
| `--actions-suppressor` | No | string | -- | Alarm name/ARN that suppresses actions when in ALARM state (1-1600 chars) |
| `--actions-suppressor-wait-period` | No | integer | -- | Max seconds to wait for suppressor to enter ALARM. Required if suppressor specified |
| `--actions-suppressor-extension-period` | No | integer | -- | Max seconds after suppressor exits ALARM. Required if suppressor specified |

**Output:** None on success.

---

### 2.3 `describe-alarms`

Retrieves information about alarms. **Paginated.**

**Synopsis:**
```bash
aws cloudwatch describe-alarms \
    [--alarm-names <value>] \
    [--alarm-name-prefix <value>] \
    [--alarm-types <value>] \
    [--state-value <value>] \
    [--action-prefix <value>] \
    [--children-of-alarm-name <value>] \
    [--parents-of-alarm-name <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-names` | No | list | -- | Specific alarm names (max 100) |
| `--alarm-name-prefix` | No | string | -- | Alarm name prefix filter (1-255 chars). Cannot combine with `--alarm-names` |
| `--alarm-types` | No | list | MetricAlarm only | `CompositeAlarm`, `MetricAlarm` |
| `--state-value` | No | string | -- | `OK`, `ALARM`, `INSUFFICIENT_DATA` |
| `--action-prefix` | No | string | -- | Filter by action ARN prefix (1-1024 chars) |
| `--children-of-alarm-name` | No | string | -- | Get child alarms of composite alarm (1-255 chars) |
| `--parents-of-alarm-name` | No | string | -- | Get parent composite alarms (1-255 chars) |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "MetricAlarms": [
        {
            "AlarmName": "string",
            "AlarmArn": "string",
            "AlarmDescription": "string",
            "AlarmConfigurationUpdatedTimestamp": "timestamp",
            "ActionsEnabled": true|false,
            "OKActions": ["string"],
            "AlarmActions": ["string"],
            "InsufficientDataActions": ["string"],
            "StateValue": "OK|ALARM|INSUFFICIENT_DATA",
            "StateReason": "string",
            "StateReasonData": "string",
            "StateUpdatedTimestamp": "timestamp",
            "StateTransitionedTimestamp": "timestamp",
            "MetricName": "string",
            "Namespace": "string",
            "Statistic": "SampleCount|Average|Sum|Minimum|Maximum",
            "ExtendedStatistic": "string",
            "Dimensions": [{"Name": "string", "Value": "string"}],
            "Period": integer,
            "Unit": "string",
            "EvaluationPeriods": integer,
            "DatapointsToAlarm": integer,
            "Threshold": double,
            "ComparisonOperator": "string",
            "TreatMissingData": "string",
            "EvaluateLowSampleCountPercentile": "string",
            "Metrics": [{"Id": "string", "MetricStat": {}, "Expression": "string"}],
            "ThresholdMetricId": "string",
            "EvaluationState": "PARTIAL_DATA"
        }
    ],
    "CompositeAlarms": [
        {
            "AlarmName": "string",
            "AlarmArn": "string",
            "AlarmDescription": "string",
            "AlarmConfigurationUpdatedTimestamp": "timestamp",
            "ActionsEnabled": true|false,
            "AlarmActions": ["string"],
            "InsufficientDataActions": ["string"],
            "OKActions": ["string"],
            "StateValue": "OK|ALARM|INSUFFICIENT_DATA",
            "StateReason": "string",
            "StateReasonData": "string",
            "StateUpdatedTimestamp": "timestamp",
            "StateTransitionedTimestamp": "timestamp",
            "AlarmRule": "string",
            "ActionsSuppressedBy": "WaitPeriod|ExtensionPeriod|Alarm",
            "ActionsSuppressedReason": "string",
            "ActionsSuppressor": "string",
            "ActionsSuppressorWaitPeriod": integer,
            "ActionsSuppressorExtensionPeriod": integer
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `describe-alarms-for-metric`

Retrieves all alarms configured for a specific metric.

**Synopsis:**
```bash
aws cloudwatch describe-alarms-for-metric \
    --metric-name <value> \
    --namespace <value> \
    [--statistic <value>] \
    [--extended-statistic <value>] \
    [--dimensions <value>] \
    [--period <value>] \
    [--unit <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name (1-255 chars) |
| `--namespace` | **Yes** | string | -- | Metric namespace (1-255 chars) |
| `--statistic` | No | string | -- | Statistic filter |
| `--extended-statistic` | No | string | -- | Extended statistic filter |
| `--dimensions` | No | list | -- | Dimension filter (max 30) |
| `--period` | No | integer | -- | Period filter in seconds |
| `--unit` | No | string | -- | Unit filter |

**Output Schema:**
```json
{
    "MetricAlarms": [
        {
            "AlarmName": "string",
            "AlarmArn": "string",
            "AlarmDescription": "string",
            "StateValue": "OK|ALARM|INSUFFICIENT_DATA",
            "MetricName": "string",
            "Namespace": "string",
            "Period": integer,
            "Threshold": double,
            "ComparisonOperator": "string",
            "EvaluationPeriods": integer
        }
    ]
}
```

---

### 2.5 `describe-alarm-history`

Retrieves the history for an alarm. **Paginated.**

**Synopsis:**
```bash
aws cloudwatch describe-alarm-history \
    [--alarm-name <value>] \
    [--alarm-types <value>] \
    [--history-item-type <value>] \
    [--start-date <value>] \
    [--end-date <value>] \
    [--scan-by <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | No | string | -- | Specific alarm name (1-255 chars) |
| `--alarm-types` | No | list | -- | `CompositeAlarm`, `MetricAlarm` |
| `--history-item-type` | No | string | -- | `ConfigurationUpdate`, `StateUpdate`, `Action` |
| `--start-date` | No | timestamp | -- | Start of date range |
| `--end-date` | No | timestamp | -- | End of date range |
| `--scan-by` | No | string | `TimestampDescending` | `TimestampDescending` or `TimestampAscending` |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "AlarmHistoryItems": [
        {
            "AlarmName": "string",
            "AlarmType": "CompositeAlarm|MetricAlarm",
            "Timestamp": "timestamp",
            "HistoryItemType": "ConfigurationUpdate|StateUpdate|Action",
            "HistorySummary": "string",
            "HistoryData": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `delete-alarms`

Deletes one or more alarms.

**Synopsis:**
```bash
aws cloudwatch delete-alarms \
    --alarm-names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-names` | **Yes** | list | -- | Names of alarms to delete (max 100) |

**Output:** None on success.

---

### 2.7 `set-alarm-state`

Temporarily sets the state of an alarm. Used for testing.

**Synopsis:**
```bash
aws cloudwatch set-alarm-state \
    --alarm-name <value> \
    --state-value <value> \
    --state-reason <value> \
    [--state-reason-data <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | **Yes** | string | -- | Alarm name (1-255 chars) |
| `--state-value` | **Yes** | string | -- | `OK`, `ALARM`, `INSUFFICIENT_DATA` |
| `--state-reason` | **Yes** | string | -- | Reason for state change (0-1023 chars) |
| `--state-reason-data` | No | string | -- | Reason data in JSON (0-4000 chars) |

**Output:** None on success.

---

### 2.8 `enable-alarm-actions`

Enables actions for the specified alarms.

**Synopsis:**
```bash
aws cloudwatch enable-alarm-actions \
    --alarm-names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-names` | **Yes** | list | -- | Alarm names to enable actions for (max 100) |

**Output:** None on success.

---

### 2.9 `disable-alarm-actions`

Disables actions for the specified alarms.

**Synopsis:**
```bash
aws cloudwatch disable-alarm-actions \
    --alarm-names <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-names` | **Yes** | list | -- | Alarm names to disable actions for (max 100) |

**Output:** None on success.

---

### 2.10 `describe-alarm-contributors`

Retrieves top contributors for a metric alarm with anomaly detection.

**Synopsis:**
```bash
aws cloudwatch describe-alarm-contributors \
    --alarm-name <value> \
    --start-time <value> \
    --end-time <value> \
    [--period <value>] \
    [--max-results <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | **Yes** | string | -- | Alarm name (1-255 chars) |
| `--start-time` | **Yes** | timestamp | -- | Start of time range |
| `--end-time` | **Yes** | timestamp | -- | End of time range |
| `--period` | No | integer | -- | Period in seconds |
| `--max-results` | No | integer | -- | Maximum contributors to return |

**Output Schema:**
```json
{
    "AlarmName": "string",
    "Contributors": [
        {
            "DimensionValues": ["string"],
            "ApproximateAggregateValue": double,
            "Datapoints": [
                {
                    "Timestamp": "timestamp",
                    "ApproximateValue": double
                }
            ]
        }
    ],
    "TotalContributors": integer
}
```

---
