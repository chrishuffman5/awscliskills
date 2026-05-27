# Log Anomaly Detection

### 19.1 `create-log-anomaly-detector`

Creates a log anomaly detector for a log group.

**Synopsis:**
```bash
aws logs create-log-anomaly-detector \
    --log-group-arn-list <value> \
    [--detector-name <value>] \
    [--evaluation-frequency <value>] \
    [--filter-pattern <value>] \
    [--kms-key-id <value>] \
    [--anomaly-visibility-time <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-arn-list` | **Yes** | list | -- | Log group ARNs to monitor |
| `--detector-name` | No | string | -- | Detector name |
| `--evaluation-frequency` | No | string | -- | `ONE_MIN`, `FIVE_MIN`, `TEN_MIN`, `FIFTEEN_MIN`, `THIRTY_MIN`, `ONE_HOUR` |
| `--filter-pattern` | No | string | -- | Filter pattern (0-1024 chars) |
| `--kms-key-id` | No | string | -- | KMS key ARN for encryption (max 256 chars) |
| `--anomaly-visibility-time` | No | long | -- | Days anomalies remain visible (7-90) |
| `--tags` | No | map | -- | Key-value tags |

**Output Schema:**
```json
{
    "anomalyDetectorArn": "string"
}
```

---

### 19.2 `get-log-anomaly-detector`

Retrieves information about a log anomaly detector.

**Synopsis:**
```bash
aws logs get-log-anomaly-detector \
    --anomaly-detector-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | Anomaly detector ARN |

**Output Schema:**
```json
{
    "detectorName": "string",
    "logGroupArnList": ["string"],
    "evaluationFrequency": "ONE_MIN|FIVE_MIN|TEN_MIN|FIFTEEN_MIN|THIRTY_MIN|ONE_HOUR",
    "filterPattern": "string",
    "anomalyDetectorStatus": "INITIALIZING|TRAINING|ANALYZING|FAILED|DELETED|PAUSED",
    "kmsKeyId": "string",
    "creationTimeStamp": long,
    "lastModifiedTimeStamp": long,
    "anomalyVisibilityTime": long
}
```

---

### 19.3 `list-log-anomaly-detectors`

Lists log anomaly detectors. **Paginated.**

**Synopsis:**
```bash
aws logs list-log-anomaly-detectors \
    [--filter-log-group-arn <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-log-group-arn` | No | string | -- | Filter by log group ARN |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "anomalyDetectors": [
        {
            "anomalyDetectorArn": "string",
            "detectorName": "string",
            "logGroupArnList": ["string"],
            "evaluationFrequency": "string",
            "filterPattern": "string",
            "anomalyDetectorStatus": "string",
            "creationTimeStamp": long,
            "lastModifiedTimeStamp": long,
            "anomalyVisibilityTime": long
        }
    ],
    "nextToken": "string"
}
```

---

### 19.4 `update-log-anomaly-detector`

Updates a log anomaly detector.

**Synopsis:**
```bash
aws logs update-log-anomaly-detector \
    --anomaly-detector-arn <value> \
    --enabled | --no-enabled \
    [--evaluation-frequency <value>] \
    [--filter-pattern <value>] \
    [--anomaly-visibility-time <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | Anomaly detector ARN |
| `--enabled` / `--no-enabled` | **Yes** | boolean | -- | Enable or disable the detector |
| `--evaluation-frequency` | No | string | -- | `ONE_MIN`, `FIVE_MIN`, `TEN_MIN`, `FIFTEEN_MIN`, `THIRTY_MIN`, `ONE_HOUR` |
| `--filter-pattern` | No | string | -- | Filter pattern (0-1024 chars) |
| `--anomaly-visibility-time` | No | long | -- | Days anomalies remain visible (7-90) |

**Output:** None on success.

---

### 19.5 `delete-log-anomaly-detector`

Deletes a log anomaly detector.

**Synopsis:**
```bash
aws logs delete-log-anomaly-detector \
    --anomaly-detector-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | Anomaly detector ARN |

**Output:** None on success.

---

### 19.6 `list-anomalies`

Lists anomalies detected by a log anomaly detector. **Paginated.**

**Synopsis:**
```bash
aws logs list-anomalies \
    [--anomaly-detector-arn <value>] \
    [--suppression-state <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | No | string | -- | Filter by detector ARN |
| `--suppression-state` | No | string | -- | `SUPPRESSED` or `UNSUPPRESSED` |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "anomalies": [
        {
            "anomalyId": "string",
            "patternId": "string",
            "anomalyDetectorArn": "string",
            "patternString": "string",
            "firstSeen": long,
            "lastSeen": long,
            "description": "string",
            "active": true|false,
            "state": "Active|Suppressed|Baseline",
            "histogram": {"string": long},
            "logSamples": [
                {"timestamp": long, "message": "string"}
            ],
            "patternTokens": [
                {"dynamicTokenPosition": integer, "isDynamic": true|false, "tokenString": "string"}
            ],
            "logGroupArnList": ["string"],
            "suppressed": true|false,
            "suppressedDate": long,
            "suppressedUntil": long,
            "isPatternLevelSuppression": true|false
        }
    ],
    "nextToken": "string"
}
```

---

### 19.7 `update-anomaly`

Updates the suppression state of an anomaly or pattern.

**Synopsis:**
```bash
aws logs update-anomaly \
    --anomaly-detector-arn <value> \
    [--anomaly-id <value>] \
    [--pattern-id <value>] \
    [--suppression-type <value>] \
    [--suppression-period <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | Anomaly detector ARN |
| `--anomaly-id` | No | string | -- | Anomaly ID to update |
| `--pattern-id` | No | string | -- | Pattern ID to update |
| `--suppression-type` | No | string | -- | `LIMITED`, `INFINITE` |
| `--suppression-period` | No | structure | -- | `value` (integer) and `suppressionUnit` (`SECONDS`, `MINUTES`, `HOURS`) |

**Output:** None on success.

---
