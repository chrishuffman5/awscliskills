# Alerts

### 3.1 `create-alert`

Creates an alert for an anomaly detector. Alerts notify via SNS or Lambda when anomalies are detected.

**Synopsis:**
```bash
aws lookoutmetrics create-alert \
    --alert-name <value> \
    --anomaly-detector-arn <value> \
    --action <value> \
    [--alert-sensitivity-threshold <value>] \
    [--alert-description <value>] \
    [--alert-filters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alert-name` | **Yes** | string | -- | Alert name (min 1 char) |
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the anomaly detector |
| `--action` | **Yes** | structure | -- | Alert action (SNS or Lambda config, JSON) |
| `--alert-sensitivity-threshold` | No | integer | -- | Sensitivity threshold (0-100) |
| `--alert-description` | No | string | -- | Description |
| `--alert-filters` | No | structure | -- | Filters for metrics and dimensions (JSON) |
| `--tags` | No | map | -- | Tags as key=value pairs |

**Action Structure (one of SNS or Lambda):**
```json
{
    "SNSConfiguration": {
        "RoleArn": "string",
        "SnsTopicArn": "string",
        "SnsFormat": "JSON|LONG_TEXT|SHORT_TEXT"
    },
    "LambdaConfiguration": {
        "RoleArn": "string",
        "LambdaArn": "string"
    }
}
```

**Alert Filters Structure:**
```json
{
    "MetricList": ["string"],
    "DimensionFilterList": [
        {
            "Name": "string",
            "FilterList": [
                {
                    "DimensionValue": "string",
                    "FilterOperation": "EQUALS"
                }
            ]
        }
    ]
}
```

**Output Schema:**
```json
{
    "AlertArn": "string"
}
```

---

### 3.2 `describe-alert`

Describes an alert.

**Synopsis:**
```bash
aws lookoutmetrics describe-alert \
    --alert-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alert-arn` | **Yes** | string | -- | ARN of the alert |

**Output Schema:**
```json
{
    "Alert": {
        "Action": {
            "SNSConfiguration": {},
            "LambdaConfiguration": {}
        },
        "AlertDescription": "string",
        "AlertArn": "string",
        "AnomalyDetectorArn": "string",
        "AlertName": "string",
        "AlertSensitivityThreshold": "integer",
        "AlertType": "SNS|LAMBDA",
        "AlertStatus": "ACTIVE|INACTIVE",
        "AlertFilters": {},
        "CreationTime": "timestamp",
        "LastModificationTime": "timestamp"
    }
}
```

---

### 3.3 `list-alerts`

Lists alerts for a detector. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutmetrics list-alerts \
    [--anomaly-detector-arn <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | No | string | -- | Filter by detector ARN |
| `--max-results` | No | integer | -- | Max items to return |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "AlertSummaryList": [
        {
            "AlertArn": "string",
            "AnomalyDetectorArn": "string",
            "AlertName": "string",
            "AlertSensitivityThreshold": "integer",
            "AlertType": "SNS|LAMBDA",
            "AlertStatus": "ACTIVE|INACTIVE",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp",
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-alert`

Updates an existing alert.

**Synopsis:**
```bash
aws lookoutmetrics update-alert \
    --alert-arn <value> \
    [--alert-description <value>] \
    [--alert-sensitivity-threshold <value>] \
    [--action <value>] \
    [--alert-filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alert-arn` | **Yes** | string | -- | ARN of the alert to update |
| `--alert-description` | No | string | -- | Updated description |
| `--alert-sensitivity-threshold` | No | integer | -- | Updated sensitivity threshold (0-100) |
| `--action` | No | structure | -- | Updated action config (JSON) |
| `--alert-filters` | No | structure | -- | Updated filters (JSON) |

**Output Schema:**
```json
{
    "AlertArn": "string"
}
```

---

### 3.5 `delete-alert`

Deletes an alert.

**Synopsis:**
```bash
aws lookoutmetrics delete-alert \
    --alert-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alert-arn` | **Yes** | string | -- | ARN of the alert to delete |

**Output:** None (HTTP 200 on success)
