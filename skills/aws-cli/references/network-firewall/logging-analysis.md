# Logging & Analysis

### 9.1 `describe-logging-configuration`

Returns the logging configuration for the specified firewall.

**Synopsis:**
```bash
aws network-firewall describe-logging-configuration \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |

*Must specify either name or ARN.

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "LoggingConfiguration": {
        "LogDestinationConfigs": [
            {
                "LogType": "ALERT|FLOW|TLS",
                "LogDestinationType": "S3|CloudWatchLogs|KinesisDataFirehose",
                "LogDestination": {
                    "bucketName": "string",
                    "prefix": "string",
                    "logGroup": "string",
                    "deliveryStream": "string"
                }
            }
        ]
    },
    "EnableMonitoringDashboard": true|false
}
```

---

### 9.2 `update-logging-configuration`

Configures logging for the specified firewall. Supports S3, CloudWatch Logs, and Kinesis Data Firehose destinations.

**Synopsis:**
```bash
aws network-firewall update-logging-configuration \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--logging-configuration <value>] \
    [--enable-monitoring-dashboard | --no-enable-monitoring-dashboard] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--logging-configuration` | No | structure | None | Logging configuration with destinations |
| `--enable-monitoring-dashboard` | No | boolean | None | Enable detailed monitoring dashboard |

**Logging Configuration Structure:**
```json
{
    "LogDestinationConfigs": [
        {
            "LogType": "ALERT|FLOW|TLS",
            "LogDestinationType": "S3|CloudWatchLogs|KinesisDataFirehose",
            "LogDestination": {
                "bucketName": "string",
                "prefix": "string",
                "logGroup": "string",
                "deliveryStream": "string"
            }
        }
    ]
}
```

**Log Destination Keys:**
- **S3:** `bucketName` (required), `prefix` (optional)
- **CloudWatch Logs:** `logGroup` (required)
- **Kinesis Data Firehose:** `deliveryStream` (required)

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "LoggingConfiguration": {
        "LogDestinationConfigs": []
    },
    "EnableMonitoringDashboard": true|false
}
```

---

### 9.3 `start-analysis-report`

Starts a traffic analysis report for the specified firewall.

**Synopsis:**
```bash
aws network-firewall start-analysis-report \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    --analysis-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--analysis-type` | **Yes** | string | -- | Analysis type: `TLS_SNI` or `HTTP_HOST` |

**Output Schema:**
```json
{
    "AnalysisReportId": "string"
}
```

---

### 9.4 `list-analysis-reports`

Lists analysis reports for the specified firewall. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-analysis-reports \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AnalysisReports": [
        {
            "AnalysisReportId": "string",
            "AnalysisType": "TLS_SNI|HTTP_HOST",
            "ReportTime": "timestamp",
            "Status": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `get-analysis-report-results`

Returns the results of a completed analysis report. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall get-analysis-report-results \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    --analysis-report-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--analysis-report-id` | **Yes** | string | -- | ID of the analysis report |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Status": "string",
    "AnalysisType": "TLS_SNI|HTTP_HOST",
    "ReportTime": "timestamp",
    "AnalysisReportResults": [
        {
            "Domain": "string",
            "Protocol": "string",
            "Hits": "long",
            "UniqueSources": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.6 `describe-flow-operation`

Returns details about a flow operation (capture or flush).

**Synopsis:**
```bash
aws network-firewall describe-flow-operation \
    [--firewall-arn <value>] \
    --flow-operation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-arn` | No | string | None | Firewall ARN |
| `--flow-operation-id` | **Yes** | string | -- | Flow operation ID |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FlowOperationId": "string",
    "FlowOperationType": "FLOW_CAPTURE|FLOW_FLUSH",
    "FlowOperationStatus": "string",
    "StatusMessage": "string"
}
```

---

### 9.7 `list-flow-operations`

Lists flow operations for a firewall. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-flow-operations \
    --firewall-arn <value> \
    [--flow-operation-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-arn` | **Yes** | string | -- | Firewall ARN |
| `--flow-operation-type` | No | string | None | Filter: `FLOW_CAPTURE` or `FLOW_FLUSH` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FlowOperations": [
        {
            "FlowOperationId": "string",
            "FlowOperationType": "FLOW_CAPTURE|FLOW_FLUSH",
            "FlowOperationStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.8 `list-flow-operation-results`

Lists results of a flow operation. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-flow-operation-results \
    --firewall-arn <value> \
    --flow-operation-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-arn` | **Yes** | string | -- | Firewall ARN |
| `--flow-operation-id` | **Yes** | string | -- | Flow operation ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FlowOperationId": "string",
    "FlowOperationStatus": "string",
    "FlowRequestTimestamp": "timestamp",
    "FlowOperationResults": [],
    "NextToken": "string"
}
```

---

### 9.9 `start-flow-capture`

Starts a flow capture on the specified firewall to capture network flow data.

**Synopsis:**
```bash
aws network-firewall start-flow-capture \
    --firewall-arn <value> \
    [--flow-filters <value>] \
    [--minimum-flow-age-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-arn` | **Yes** | string | -- | Firewall ARN |
| `--flow-filters` | No | list | None | Filters for flow capture |
| `--minimum-flow-age-in-seconds` | No | integer | None | Minimum age of flows to capture |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FlowOperationId": "string",
    "FlowOperationStatus": "string"
}
```

---

### 9.10 `start-flow-flush`

Starts a flow flush on the specified firewall to clear active flows.

**Synopsis:**
```bash
aws network-firewall start-flow-flush \
    --firewall-arn <value> \
    [--flow-filters <value>] \
    [--minimum-flow-age-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-arn` | **Yes** | string | -- | Firewall ARN |
| `--flow-filters` | No | list | None | Filters for flow flush |
| `--minimum-flow-age-in-seconds` | No | integer | None | Minimum age of flows to flush |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FlowOperationId": "string",
    "FlowOperationStatus": "string"
}
```
