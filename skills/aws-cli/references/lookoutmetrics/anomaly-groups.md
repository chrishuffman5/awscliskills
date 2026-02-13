# Anomaly Groups

### 4.1 `get-anomaly-group`

Returns details about a group of anomalous metrics.

**Synopsis:**
```bash
aws lookoutmetrics get-anomaly-group \
    --anomaly-group-id <value> \
    --anomaly-detector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-group-id` | **Yes** | string | -- | ID of the anomaly group |
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |

**Output Schema:**
```json
{
    "AnomalyGroup": {
        "StartTime": "string",
        "EndTime": "string",
        "AnomalyGroupId": "string",
        "AnomalyGroupScore": "double",
        "PrimaryMetricName": "string",
        "MetricLevelImpactList": [
            {
                "MetricName": "string",
                "NumTimeSeries": "integer",
                "ContributionMatrix": {
                    "DimensionContributionList": [
                        {
                            "DimensionName": "string",
                            "DimensionValueContributionList": [
                                {
                                    "DimensionValue": "string",
                                    "ContributionScore": "double"
                                }
                            ]
                        }
                    ]
                }
            }
        ]
    }
}
```

---

### 4.2 `list-anomaly-group-summaries`

Lists anomaly group summaries for a detector. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutmetrics list-anomaly-group-summaries \
    --anomaly-detector-arn <value> \
    --sensitivity-threshold <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--sensitivity-threshold` | **Yes** | integer | -- | Sensitivity threshold (0-100) |
| `--max-results` | No | integer | -- | Max items to return |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "AnomalyGroupSummaryList": [
        {
            "StartTime": "string",
            "EndTime": "string",
            "AnomalyGroupId": "string",
            "AnomalyGroupScore": "double",
            "PrimaryMetricName": "string"
        }
    ],
    "AnomalyGroupStatistics": {
        "EvaluationStartDate": "string",
        "TotalCount": "integer",
        "ItemizedMetricStatsList": [
            {
                "MetricName": "string",
                "OccurrenceCount": "integer"
            }
        ]
    },
    "NextToken": "string"
}
```

---

### 4.3 `list-anomaly-group-time-series`

Lists time series in an anomaly group for a specific metric. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutmetrics list-anomaly-group-time-series \
    --anomaly-detector-arn <value> \
    --anomaly-group-id <value> \
    --metric-name <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--anomaly-group-id` | **Yes** | string | -- | ID of the anomaly group |
| `--metric-name` | **Yes** | string | -- | Name of the metric |
| `--max-results` | No | integer | -- | Max items to return |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "AnomalyGroupId": "string",
    "MetricName": "string",
    "TimestampList": ["string"],
    "TimeSeriesList": [
        {
            "TimeSeriesId": "string",
            "DimensionList": [
                {
                    "DimensionName": "string",
                    "DimensionValue": "string"
                }
            ],
            "MetricValueList": ["double"]
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `list-anomaly-group-related-metrics`

Lists metrics that are potential causes or effects of an anomaly group. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutmetrics list-anomaly-group-related-metrics \
    --anomaly-detector-arn <value> \
    --anomaly-group-id <value> \
    [--relationship-type-filter <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--anomaly-group-id` | **Yes** | string | -- | ID of the anomaly group |
| `--relationship-type-filter` | No | string | -- | Filter by relationship type: `CAUSE_OF_INPUT_ANOMALY_GROUP`, `EFFECT_OF_INPUT_ANOMALY_GROUP` |
| `--max-results` | No | integer | -- | Max items to return |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "InterMetricImpactList": [
        {
            "MetricName": "string",
            "AnomalyGroupId": "string",
            "RelationshipType": "CAUSE_OF_INPUT_ANOMALY_GROUP|EFFECT_OF_INPUT_ANOMALY_GROUP",
            "ContributionPercentage": "double"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `put-feedback`

Submits feedback for an anomalous metric to improve future detection accuracy.

**Synopsis:**
```bash
aws lookoutmetrics put-feedback \
    --anomaly-detector-arn <value> \
    --anomaly-group-time-series-feedback <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--anomaly-group-time-series-feedback` | **Yes** | structure | -- | Feedback. Shorthand: `AnomalyGroupId=string,TimeSeriesId=string,IsAnomaly=boolean` |

**Feedback Structure:**
```json
{
    "AnomalyGroupId": "string",
    "TimeSeriesId": "string",
    "IsAnomaly": true
}
```

**Output:** None (HTTP 200 on success)

---

### 4.6 `get-feedback`

Gets feedback for an anomaly group. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutmetrics get-feedback \
    --anomaly-detector-arn <value> \
    --anomaly-group-time-series-feedback <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--anomaly-group-time-series-feedback` | **Yes** | structure | -- | Anomaly group info. Shorthand: `AnomalyGroupId=string` |
| `--max-results` | No | integer | -- | Max items to return |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "AnomalyGroupTimeSeriesFeedback": [
        {
            "TimeSeriesId": "string",
            "IsAnomaly": "boolean"
        }
    ],
    "NextToken": "string"
}
```
