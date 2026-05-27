# Monitors

### 5.1 `create-monitor`

Creates a predictor monitor to track performance over time. Only works with AutoPredictors.

**Synopsis:**
```bash
aws forecast create-monitor \
    --monitor-name <value> \
    --resource-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name (1-63 chars) |
| `--resource-arn` | **Yes** | string | -- | Predictor ARN to monitor |
| `--tags` | No | list | None | Tags: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "MonitorArn": "string"
}
```

---

### 5.2 `describe-monitor`

Gets properties of a predictor monitor.

**Synopsis:**
```bash
aws forecast describe-monitor \
    --monitor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-arn` | **Yes** | string | -- | Monitor ARN |

**Output Schema:**
```json
{
    "MonitorName": "string",
    "MonitorArn": "string",
    "ResourceArn": "string",
    "Status": "string",
    "LastEvaluationTime": "timestamp",
    "LastEvaluationState": "string",
    "Baseline": {
        "PredictorBaseline": {
            "BaselineMetrics": [
                {
                    "Name": "string",
                    "Value": "double"
                }
            ]
        }
    },
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "EstimatedEvaluationTimeRemainingInMinutes": "long"
}
```

---

### 5.3 `list-monitors`

Lists predictor monitors. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-monitors \
    [--next-token <value>] \
    [--max-results <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "Monitors": [
        {
            "MonitorArn": "string",
            "MonitorName": "string",
            "ResourceArn": "string",
            "Status": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `list-monitor-evaluations`

Lists monitor evaluation results. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-monitor-evaluations \
    --monitor-arn <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-arn` | **Yes** | string | -- | Monitor ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "PredictorMonitorEvaluations": [
        {
            "ResourceArn": "string",
            "MonitorArn": "string",
            "EvaluationTime": "timestamp",
            "EvaluationState": "string",
            "WindowStartDatetime": "timestamp",
            "WindowEndDatetime": "timestamp",
            "PredictorEvent": {
                "Detail": "string",
                "Datetime": "timestamp"
            },
            "MonitorDataSource": {
                "DatasetImportJobArn": "string",
                "ForecastArn": "string",
                "PredictorArn": "string"
            },
            "MetricResults": [
                {
                    "MetricName": "string",
                    "MetricValue": "double"
                }
            ],
            "NumItemsEvaluated": "long",
            "Message": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `delete-monitor`

Deletes a predictor monitor.

**Synopsis:**
```bash
aws forecast delete-monitor \
    --monitor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-arn` | **Yes** | string | -- | Monitor ARN |

**Output:** None
