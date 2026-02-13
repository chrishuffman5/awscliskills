# Problems

### 4.1 `describe-problem`

Describes a detected problem.

**Synopsis:**
```bash
aws application-insights describe-problem \
    --problem-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--problem-id` | **Yes** | string | -- | ID of the problem |
| `--account-id` | No | string | -- | AWS account ID (for cross-account) |

**Output Schema:**
```json
{
    "Problem": {
        "Id": "string",
        "Title": "string",
        "ShortName": "string",
        "Insights": "string",
        "Status": "IGNORE|RESOLVED|PENDING|RECURRING|RECOVERING",
        "AffectedResource": "string",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "SeverityLevel": "Informative|Low|Medium|High",
        "AccountId": "string",
        "ResourceGroupName": "string",
        "Feedback": {
            "string": "NOT_SPECIFIED|USEFUL|NOT_USEFUL"
        },
        "RecurringCount": "long",
        "LastRecurrenceTime": "timestamp",
        "Visibility": "IGNORED|VISIBLE"
    }
}
```

---

### 4.2 `list-problems`

Lists the problems detected by Application Insights. **Paginated operation.**

**Synopsis:**
```bash
aws application-insights list-problems \
    [--resource-group-name <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--component-name <value>] \
    [--account-id <value>] \
    [--visibility <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | No | string | -- | Name of the resource group to filter by |
| `--start-time` | No | timestamp | -- | Start time to filter problems |
| `--end-time` | No | timestamp | -- | End time to filter problems |
| `--component-name` | No | string | -- | Component name to filter by |
| `--account-id` | No | string | -- | AWS account ID |
| `--visibility` | No | string | -- | Visibility filter: `IGNORED`, `VISIBLE` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ProblemList": [
        {
            "Id": "string",
            "Title": "string",
            "ShortName": "string",
            "Insights": "string",
            "Status": "IGNORE|RESOLVED|PENDING|RECURRING|RECOVERING",
            "AffectedResource": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "SeverityLevel": "Informative|Low|Medium|High",
            "AccountId": "string",
            "ResourceGroupName": "string",
            "Feedback": {},
            "RecurringCount": "long",
            "LastRecurrenceTime": "timestamp",
            "Visibility": "IGNORED|VISIBLE"
        }
    ],
    "NextToken": "string",
    "ResourceGroupName": "string",
    "AccountId": "string"
}
```

---

### 4.3 `update-problem`

Updates a problem's status or visibility.

**Synopsis:**
```bash
aws application-insights update-problem \
    --problem-id <value> \
    [--update-status <value>] \
    [--visibility <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--problem-id` | **Yes** | string | -- | ID of the problem |
| `--update-status` | No | string | -- | New status: `RESOLVED` |
| `--visibility` | No | string | -- | Visibility: `IGNORED`, `VISIBLE` |

**Output Schema:**
```json
{}
```

---

### 4.4 `describe-problem-observations`

Describes the anomalies or errors associated with the problem.

**Synopsis:**
```bash
aws application-insights describe-problem-observations \
    --problem-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--problem-id` | **Yes** | string | -- | ID of the problem |
| `--account-id` | No | string | -- | AWS account ID |

**Output Schema:**
```json
{
    "RelatedObservations": {
        "ObservationList": [
            {
                "Id": "string",
                "StartTime": "timestamp",
                "EndTime": "timestamp",
                "SourceType": "string",
                "SourceARN": "string",
                "LogGroup": "string",
                "LineTime": "timestamp",
                "LogText": "string",
                "LogFilter": "ERROR|WARN|INFO",
                "MetricNamespace": "string",
                "MetricName": "string",
                "Unit": "string",
                "Value": "double",
                "CloudWatchEventId": "string",
                "CloudWatchEventSource": "EC2|CODE_DEPLOY|HEALTH|RDS",
                "CloudWatchEventDetailType": "string",
                "HealthEventArn": "string",
                "HealthService": "string",
                "HealthEventTypeCode": "string",
                "HealthEventTypeCategory": "string",
                "HealthEventDescription": "string",
                "CodeDeployDeploymentId": "string",
                "CodeDeployDeploymentGroup": "string",
                "CodeDeployState": "string",
                "CodeDeployApplication": "string",
                "CodeDeployInstanceGroupId": "string",
                "Ec2State": "string",
                "RdsEventCategories": "string",
                "RdsEventMessage": "string",
                "S3EventName": "string",
                "StatesExecutionArn": "string",
                "StatesArn": "string",
                "StatesStatus": "string",
                "StatesInput": "string",
                "EbsEvent": "string",
                "EbsResult": "string",
                "EbsCause": "string",
                "EbsRequestId": "string",
                "XRayFaultPercent": "integer",
                "XRayThrottlePercent": "integer",
                "XRayErrorPercent": "integer",
                "XRayRequestCount": "integer",
                "XRayRequestAverageLatency": "long",
                "XRayNodeName": "string",
                "XRayNodeType": "string"
            }
        ]
    }
}
```

---

### 4.5 `describe-observation`

Describes an anomaly or error with the application.

**Synopsis:**
```bash
aws application-insights describe-observation \
    --observation-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--observation-id` | **Yes** | string | -- | ID of the observation |
| `--account-id` | No | string | -- | AWS account ID |

**Output Schema:**
```json
{
    "Observation": {
        "Id": "string",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "SourceType": "string",
        "SourceARN": "string",
        "LogGroup": "string",
        "LineTime": "timestamp",
        "LogText": "string",
        "LogFilter": "ERROR|WARN|INFO",
        "MetricNamespace": "string",
        "MetricName": "string",
        "Unit": "string",
        "Value": "double",
        "CloudWatchEventId": "string",
        "CloudWatchEventSource": "EC2|CODE_DEPLOY|HEALTH|RDS",
        "CloudWatchEventDetailType": "string",
        "HealthEventArn": "string",
        "HealthService": "string",
        "HealthEventTypeCode": "string",
        "HealthEventTypeCategory": "string",
        "HealthEventDescription": "string",
        "CodeDeployDeploymentId": "string",
        "CodeDeployDeploymentGroup": "string",
        "CodeDeployState": "string",
        "CodeDeployApplication": "string",
        "CodeDeployInstanceGroupId": "string",
        "Ec2State": "string",
        "RdsEventCategories": "string",
        "RdsEventMessage": "string",
        "XRayFaultPercent": "integer",
        "XRayThrottlePercent": "integer",
        "XRayErrorPercent": "integer",
        "XRayRequestCount": "integer",
        "XRayRequestAverageLatency": "long",
        "XRayNodeName": "string",
        "XRayNodeType": "string"
    }
}
```

---

### 4.6 `list-configuration-history`

Lists the configuration history for the application. **Paginated operation.**

**Synopsis:**
```bash
aws application-insights list-configuration-history \
    [--resource-group-name <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--event-status <value>] \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | No | string | -- | Name of the resource group |
| `--start-time` | No | timestamp | -- | Start time filter |
| `--end-time` | No | timestamp | -- | End time filter |
| `--event-status` | No | string | -- | Event status filter: `INFO`, `WARN`, `ERROR` |
| `--account-id` | No | string | -- | AWS account ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "EventList": [
        {
            "ResourceGroupName": "string",
            "AccountId": "string",
            "MonitoredResourceARN": "string",
            "EventStatus": "INFO|WARN|ERROR",
            "EventResourceType": "CLOUDWATCH_ALARM|CLOUDWATCH_LOG|CLOUDFORMATION|SSM_ASSOCIATION",
            "EventTime": "timestamp",
            "EventDetail": "string",
            "EventResourceName": "string"
        }
    ],
    "NextToken": "string"
}
```
