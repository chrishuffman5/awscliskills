# Monitors

### 1.1 `create-monitor`

Creates a monitor in Amazon CloudWatch Internet Monitor.

**Synopsis:**
```bash
aws internetmonitor create-monitor \
    --monitor-name <value> \
    [--resources <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--max-city-networks-to-monitor <value>] \
    [--traffic-percentage-to-monitor <value>] \
    [--internet-measurements-log-delivery <value>] \
    [--health-events-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name (1-255 chars, pattern: `[a-zA-Z0-9_.-]+`) |
| `--resources` | No | list(string) | -- | ARNs of resources to monitor (VPCs, NLBs, CloudFront distributions, WorkSpaces directories) |
| `--client-token` | No | string | -- | Idempotent token (up to 64 ASCII chars) |
| `--tags` | No | map | -- | Key-value tags (max 50) |
| `--max-city-networks-to-monitor` | No | integer | -- | Max city-networks to monitor (1-500,000) |
| `--traffic-percentage-to-monitor` | No | integer | -- | Percentage of traffic to monitor (1-100) |
| `--internet-measurements-log-delivery` | No | structure | -- | S3 config for log delivery |
| `--health-events-config` | No | structure | -- | Health event thresholds |

**Internet Measurements Log Delivery Structure:**
```json
{
    "S3Config": {
        "BucketName": "string",
        "BucketPrefix": "string",
        "LogDeliveryStatus": "ENABLED|DISABLED"
    }
}
```

**Health Events Config Structure:**
```json
{
    "AvailabilityScoreThreshold": "double (0-100)",
    "PerformanceScoreThreshold": "double (0-100)",
    "AvailabilityLocalHealthEventsConfig": {
        "Status": "ENABLED|DISABLED",
        "HealthScoreThreshold": "double (0-100)",
        "MinTrafficImpact": "double (0-100, default: 0.1)"
    },
    "PerformanceLocalHealthEventsConfig": {
        "Status": "ENABLED|DISABLED",
        "HealthScoreThreshold": "double (0-100)",
        "MinTrafficImpact": "double (0-100, default: 0.1)"
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Status": "PENDING|ACTIVE|INACTIVE|ERROR"
}
```

---

### 1.2 `get-monitor`

Gets information about a monitor.

**Synopsis:**
```bash
aws internetmonitor get-monitor \
    --monitor-name <value> \
    [--linked-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--linked-account-id` | No | string | -- | Account ID for cross-account sharing (12 digits) |

**Output Schema:**
```json
{
    "MonitorName": "string",
    "MonitorArn": "string",
    "Resources": ["string"],
    "Status": "PENDING|ACTIVE|INACTIVE|ERROR",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "ProcessingStatus": "OK|INACTIVE|COLLECTING_DATA|INSUFFICIENT_DATA|FAULT_SERVICE|FAULT_ACCESS_CLOUDWATCH",
    "ProcessingStatusInfo": "string",
    "Tags": { "string": "string" },
    "MaxCityNetworksToMonitor": "integer",
    "InternetMeasurementsLogDelivery": {
        "S3Config": {
            "BucketName": "string",
            "BucketPrefix": "string",
            "LogDeliveryStatus": "ENABLED|DISABLED"
        }
    },
    "TrafficPercentageToMonitor": "integer",
    "HealthEventsConfig": {
        "AvailabilityScoreThreshold": "double",
        "PerformanceScoreThreshold": "double",
        "AvailabilityLocalHealthEventsConfig": {
            "Status": "ENABLED|DISABLED",
            "HealthScoreThreshold": "double",
            "MinTrafficImpact": "double"
        },
        "PerformanceLocalHealthEventsConfig": {
            "Status": "ENABLED|DISABLED",
            "HealthScoreThreshold": "double",
            "MinTrafficImpact": "double"
        }
    }
}
```

---

### 1.3 `update-monitor`

Updates a monitor. You can update a monitor to change the percentage of traffic to monitor or the maximum number of city-networks, to add or remove resources, or to change the status.

**Synopsis:**
```bash
aws internetmonitor update-monitor \
    --monitor-name <value> \
    [--resources-to-add <value>] \
    [--resources-to-remove <value>] \
    [--status <value>] \
    [--client-token <value>] \
    [--max-city-networks-to-monitor <value>] \
    [--traffic-percentage-to-monitor <value>] \
    [--internet-measurements-log-delivery <value>] \
    [--health-events-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--resources-to-add` | No | list(string) | -- | Resource ARNs to add |
| `--resources-to-remove` | No | list(string) | -- | Resource ARNs to remove |
| `--status` | No | string | -- | `ACTIVE` or `INACTIVE` |
| `--client-token` | No | string | -- | Idempotent token |
| `--max-city-networks-to-monitor` | No | integer | -- | New max city-networks |
| `--traffic-percentage-to-monitor` | No | integer | -- | New traffic percentage |
| `--internet-measurements-log-delivery` | No | structure | -- | New S3 log delivery config |
| `--health-events-config` | No | structure | -- | New health event thresholds |

**Output Schema:**
```json
{
    "MonitorArn": "string",
    "Status": "PENDING|ACTIVE|INACTIVE|ERROR"
}
```

---

### 1.4 `delete-monitor`

Deletes a monitor.

**Synopsis:**
```bash
aws internetmonitor delete-monitor \
    --monitor-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name to delete |

**Output Schema:** None (HTTP 200 on success).

---

### 1.5 `list-monitors`

Lists all of your monitors. **Paginated operation.**

**Synopsis:**
```bash
aws internetmonitor list-monitors \
    [--monitor-status <value>] \
    [--include-linked-accounts | --no-include-linked-accounts] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-status` | No | string | -- | Filter by status |
| `--include-linked-accounts` | No | boolean | -- | Include cross-account monitors |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Monitors": [
        {
            "MonitorName": "string",
            "MonitorArn": "string",
            "Status": "PENDING|ACTIVE|INACTIVE|ERROR",
            "ProcessingStatus": "string"
        }
    ],
    "NextToken": "string"
}
```
