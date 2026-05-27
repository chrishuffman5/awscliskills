# Metrics

### 2.1 `batch-create-rum-metric-definitions`

Creates multiple extended or custom metric definitions for an app monitor.

**Synopsis:**
```bash
aws rum batch-create-rum-metric-definitions \
    --app-monitor-name <value> \
    --destination <value> \
    --metric-definitions <value> \
    [--destination-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-monitor-name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--destination` | **Yes** | string | -- | `CloudWatch` or `Evidently` |
| `--metric-definitions` | **Yes** | list | -- | Metric definitions (max 200) |
| `--destination-arn` | No | string | None | Evidently experiment ARN (required if destination is Evidently) |

**MetricDefinitions structure:**
```json
[
    {
        "Name": "string",
        "ValueKey": "string",
        "UnitLabel": "string",
        "DimensionKeys": {
            "metadata.browserName": "BrowserName",
            "metadata.countryCode": "CountryCode"
        },
        "EventPattern": "string",
        "Namespace": "string"
    }
]
```

**Extended metric names:** `PerformanceNavigationDuration`, `PerformanceResourceDuration`, `NavigationSatisfiedTransaction`, `NavigationToleratedTransaction`, `NavigationFrustratedTransaction`, `WebVitalsCumulativeLayoutShift`, `WebVitalsFirstInputDelay`, `WebVitalsLargestContentfulPaint`, `JsErrorCount`, `HttpErrorCount`, `SessionCount`, `PageViewCount`, `Http4xxCount`, `Http5xxCount`

**Valid DimensionKeys:** `metadata.pageId` -> `PageId`, `metadata.browserName` -> `BrowserName`, `metadata.deviceType` -> `DeviceType`, `metadata.osName` -> `OSName`, `metadata.countryCode` -> `CountryCode`, `event_details.fileType` -> `FileType`

**Output Schema:**
```json
{
    "Errors": [
        {
            "MetricDefinition": {},
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ],
    "MetricDefinitions": [
        {
            "MetricDefinitionId": "string",
            "Name": "string",
            "ValueKey": "string",
            "UnitLabel": "string",
            "DimensionKeys": {},
            "EventPattern": "string",
            "Namespace": "string"
        }
    ]
}
```

---

### 2.2 `batch-delete-rum-metric-definitions`

Deletes multiple metric definitions from an app monitor.

**Synopsis:**
```bash
aws rum batch-delete-rum-metric-definitions \
    --app-monitor-name <value> \
    --destination <value> \
    --metric-definition-ids <value> \
    [--destination-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-monitor-name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--destination` | **Yes** | string | -- | `CloudWatch` or `Evidently` |
| `--metric-definition-ids` | **Yes** | list | -- | Metric definition IDs to delete |
| `--destination-arn` | No | string | None | Evidently experiment ARN (required if destination is Evidently) |

**Output Schema:**
```json
{
    "Errors": [
        {
            "MetricDefinitionId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ],
    "MetricDefinitionIds": ["string"]
}
```

---

### 2.3 `batch-get-rum-metric-definitions`

Retrieves metric definitions for an app monitor. **Paginated operation.**

**Synopsis:**
```bash
aws rum batch-get-rum-metric-definitions \
    --app-monitor-name <value> \
    --destination <value> \
    [--destination-arn <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-monitor-name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--destination` | **Yes** | string | -- | `CloudWatch` or `Evidently` |
| `--destination-arn` | No | string | None | Evidently experiment ARN (required if destination is Evidently) |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Output Schema:**
```json
{
    "NextToken": "string",
    "MetricDefinitions": [
        {
            "MetricDefinitionId": "string",
            "Name": "string",
            "ValueKey": "string",
            "UnitLabel": "string",
            "DimensionKeys": {},
            "EventPattern": "string",
            "Namespace": "string"
        }
    ]
}
```

---

### 2.4 `update-rum-metric-definition`

Updates an existing metric definition.

**Synopsis:**
```bash
aws rum update-rum-metric-definition \
    --app-monitor-name <value> \
    --destination <value> \
    --metric-definition-id <value> \
    --metric-definition <value> \
    [--destination-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-monitor-name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--destination` | **Yes** | string | -- | `CloudWatch` or `Evidently` |
| `--metric-definition-id` | **Yes** | string | -- | Metric definition ID (1-255 chars) |
| `--metric-definition` | **Yes** | structure | -- | Updated metric definition |
| `--destination-arn` | No | string | None | Evidently experiment ARN (required if destination is Evidently) |

**MetricDefinition structure:**
```json
{
    "Name": "string",
    "ValueKey": "string",
    "UnitLabel": "string",
    "DimensionKeys": {},
    "EventPattern": "string",
    "Namespace": "string"
}
```

**Output:** None

---

### 2.5 `put-rum-metrics-destination`

Creates or updates a destination for sending app monitor metrics.

**Synopsis:**
```bash
aws rum put-rum-metrics-destination \
    --app-monitor-name <value> \
    --destination <value> \
    [--destination-arn <value>] \
    [--iam-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-monitor-name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--destination` | **Yes** | string | -- | `CloudWatch` or `Evidently` |
| `--destination-arn` | No | string | None | Evidently experiment ARN (required if destination is Evidently) |
| `--iam-role-arn` | No | string | None | IAM role for writing to Evidently (required if destination is Evidently) |

**Output:** None

---

### 2.6 `list-rum-metrics-destinations`

Lists metrics destinations for an app monitor. **Paginated operation.**

**Synopsis:**
```bash
aws rum list-rum-metrics-destinations \
    --app-monitor-name <value> \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-monitor-name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Destinations": [
        {
            "Destination": "CloudWatch|Evidently",
            "DestinationArn": "string",
            "IamRoleArn": "string"
        }
    ]
}
```

---

### 2.7 `delete-rum-metrics-destination`

Deletes a metrics destination.

**Synopsis:**
```bash
aws rum delete-rum-metrics-destination \
    --app-monitor-name <value> \
    --destination <value> \
    [--destination-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-monitor-name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--destination` | **Yes** | string | -- | `CloudWatch` or `Evidently` |
| `--destination-arn` | No | string | None | Evidently experiment ARN (required if destination is Evidently) |

**Output:** None
