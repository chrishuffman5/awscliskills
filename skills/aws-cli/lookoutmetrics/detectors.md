# Detectors

### 1.1 `create-anomaly-detector`

Creates an anomaly detector.

**Synopsis:**
```bash
aws lookoutmetrics create-anomaly-detector \
    --anomaly-detector-name <value> \
    --anomaly-detector-config <value> \
    [--anomaly-detector-description <value>] \
    [--kms-key-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-name` | **Yes** | string | -- | Detector name (1-63 chars) |
| `--anomaly-detector-config` | **Yes** | structure | -- | Detector config. Shorthand: `AnomalyDetectorFrequency=PT1H` |
| `--anomaly-detector-description` | No | string | -- | Description of the detector |
| `--kms-key-arn` | No | string | -- | KMS key ARN for encryption |
| `--tags` | No | map | -- | Tags as key=value pairs |

**Anomaly Detector Config Structure:**
```json
{
    "AnomalyDetectorFrequency": "P1D|PT1H|PT10M|PT5M"
}
```

**Output Schema:**
```json
{
    "AnomalyDetectorArn": "string"
}
```

---

### 1.2 `describe-anomaly-detector`

Describes an anomaly detector.

**Synopsis:**
```bash
aws lookoutmetrics describe-anomaly-detector \
    --anomaly-detector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |

**Output Schema:**
```json
{
    "AnomalyDetectorArn": "string",
    "AnomalyDetectorName": "string",
    "AnomalyDetectorDescription": "string",
    "AnomalyDetectorConfig": {
        "AnomalyDetectorFrequency": "P1D|PT1H|PT10M|PT5M"
    },
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "Status": "ACTIVE|ACTIVATING|INACTIVE|DEACTIVATED|DEACTIVATING|LEARNING|BACK_TEST_ACTIVATING|BACK_TEST_ACTIVE|BACK_TEST_COMPLETE|FAILED|DELETING",
    "FailureReason": "string",
    "FailureType": "string",
    "KmsKeyArn": "string"
}
```

---

### 1.3 `list-anomaly-detectors`

Lists anomaly detectors in the current region. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutmetrics list-anomaly-detectors \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | -- | Max items to return |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "AnomalyDetectorSummaryList": [
        {
            "AnomalyDetectorArn": "string",
            "AnomalyDetectorName": "string",
            "AnomalyDetectorDescription": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp",
            "Status": "string",
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-anomaly-detector`

Updates an anomaly detector.

**Synopsis:**
```bash
aws lookoutmetrics update-anomaly-detector \
    --anomaly-detector-arn <value> \
    [--anomaly-detector-description <value>] \
    [--anomaly-detector-config <value>] \
    [--kms-key-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--anomaly-detector-description` | No | string | -- | Updated description |
| `--anomaly-detector-config` | No | structure | -- | Updated config |
| `--kms-key-arn` | No | string | -- | Updated KMS key ARN |

**Output Schema:**
```json
{
    "AnomalyDetectorArn": "string"
}
```

---

### 1.5 `delete-anomaly-detector`

Deletes an anomaly detector and all associated resources.

**Synopsis:**
```bash
aws lookoutmetrics delete-anomaly-detector \
    --anomaly-detector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector to delete |

**Output:** None (HTTP 200 on success)

---

### 1.6 `activate-anomaly-detector`

Activates an anomaly detector to begin running.

**Synopsis:**
```bash
aws lookoutmetrics activate-anomaly-detector \
    --anomaly-detector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector to activate |

**Output:** None (HTTP 200 on success)

---

### 1.7 `deactivate-anomaly-detector`

Deactivates an anomaly detector.

**Synopsis:**
```bash
aws lookoutmetrics deactivate-anomaly-detector \
    --anomaly-detector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector to deactivate |

**Output:** None (HTTP 200 on success)

---

### 1.8 `back-test-anomaly-detector`

Runs a backtest for anomaly detection on historical data.

**Synopsis:**
```bash
aws lookoutmetrics back-test-anomaly-detector \
    --anomaly-detector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |

**Output:** None (HTTP 200 on success)

---

### 1.9 `describe-anomaly-detection-executions`

Returns information about the status of anomaly detection executions. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutmetrics describe-anomaly-detection-executions \
    --anomaly-detector-arn <value> \
    [--timestamp <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--timestamp` | No | string | -- | Filter by timestamp |
| `--max-results` | No | integer | -- | Max items to return |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "ExecutionList": [
        {
            "Timestamp": "string",
            "Status": "PENDING|IN_PROGRESS|COMPLETED|FAILED|FAILED_TO_SCHEDULE",
            "FailureReason": "string"
        }
    ],
    "NextToken": "string"
}
```
