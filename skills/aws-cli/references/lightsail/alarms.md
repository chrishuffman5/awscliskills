# Alarms

### 13.1 `put-alarm`

Creates or updates an alarm. Alarms notify you when a metric crosses a threshold.

**Synopsis:**
```bash
aws lightsail put-alarm \
    --alarm-name <value> \
    --metric-name <value> \
    --monitored-resource-name <value> \
    --comparison-operator <value> \
    --threshold <value> \
    --evaluation-periods <value> \
    [--datapoints-to-alarm <value>] \
    [--treat-missing-data <value>] \
    [--contact-protocols <value>] \
    [--notification-triggers <value>] \
    [--notification-enabled | --no-notification-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | **Yes** | string | -- | Name for the alarm |
| `--metric-name` | **Yes** | string | -- | Metric name (e.g., `CPUUtilization`, `NetworkIn`, `StatusCheckFailed`) |
| `--monitored-resource-name` | **Yes** | string | -- | Name of the resource to monitor |
| `--comparison-operator` | **Yes** | string | -- | Operator: `GreaterThanOrEqualToThreshold`, `GreaterThanThreshold`, `LessThanThreshold`, `LessThanOrEqualToThreshold` |
| `--threshold` | **Yes** | double | -- | Threshold value |
| `--evaluation-periods` | **Yes** | integer | -- | Number of periods to evaluate |
| `--datapoints-to-alarm` | No | integer | None | Datapoints to trigger alarm (must be <= evaluation periods) |
| `--treat-missing-data` | No | string | `missing` | How to treat missing data: `breaching`, `notBreaching`, `ignore`, `missing` |
| `--contact-protocols` | No | list(string) | None | Notification protocols: `Email`, `SMS` |
| `--notification-triggers` | No | list(string) | None | Triggers: `OK`, `ALARM`, `INSUFFICIENT_DATA` |
| `--notification-enabled` | No | boolean | None | Enable notifications |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Alarm",
            "operationType": "PutAlarm",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 13.2 `delete-alarm`

Deletes an alarm.

**Synopsis:**
```bash
aws lightsail delete-alarm \
    --alarm-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | **Yes** | string | -- | Name of the alarm to delete |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Alarm",
            "operationType": "DeleteAlarm",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 13.3 `get-alarms`

Returns information about alarms. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-alarms \
    [--alarm-name <value>] \
    [--page-token <value>] \
    [--monitored-resource-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | No | string | None | Specific alarm name |
| `--page-token` | No | string | None | Pagination token |
| `--monitored-resource-name` | No | string | None | Filter by monitored resource |

**Output Schema:**
```json
{
    "alarms": [
        {
            "name": "string",
            "arn": "string",
            "createdAt": "timestamp",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            },
            "resourceType": "Alarm",
            "supportCode": "string",
            "monitoredResourceInfo": {
                "arn": "string",
                "name": "string",
                "resourceType": "string"
            },
            "comparisonOperator": "GreaterThanOrEqualToThreshold|GreaterThanThreshold|LessThanThreshold|LessThanOrEqualToThreshold",
            "evaluationPeriods": "integer",
            "period": "integer",
            "threshold": "double",
            "datapointsToAlarm": "integer",
            "treatMissingData": "breaching|notBreaching|ignore|missing",
            "statistic": "Minimum|Maximum|Sum|Average|SampleCount",
            "metricName": "string",
            "state": "OK|ALARM|INSUFFICIENT_DATA",
            "unit": "string",
            "contactProtocols": ["Email|SMS"],
            "notificationTriggers": ["OK|ALARM|INSUFFICIENT_DATA"],
            "notificationEnabled": true|false
        }
    ],
    "nextPageToken": "string"
}
```

---

### 13.4 `test-alarm`

Tests an alarm by setting it to the specified state for testing notification actions.

**Synopsis:**
```bash
aws lightsail test-alarm \
    --alarm-name <value> \
    --state <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-name` | **Yes** | string | -- | Name of the alarm to test |
| `--state` | **Yes** | string | -- | Alarm state: `OK`, `ALARM`, `INSUFFICIENT_DATA` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Alarm",
            "operationType": "TestAlarm",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```
