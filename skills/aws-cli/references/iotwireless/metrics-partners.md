# Metrics & Partner Accounts

### 11.1 `get-metrics`

Gets summary metrics for wireless devices and gateways.

**Synopsis:**
```bash
aws iotwireless get-metrics \
    [--summary-metric-queries <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--summary-metric-queries` | No | list | None | Metric queries (max 20) |

**Query structure:**
```json
[
    {
        "QueryId": "string",
        "MetricName": "DeviceRSSI|DeviceSNR|DeviceUplinkCount|DeviceDownlinkCount|DeviceUplinkLostCount|DeviceUplinkLostRate|DeviceJoinRequestCount|DeviceJoinAcceptCount|DeviceRoamingUplinkCount|DeviceRoamingDownlinkCount|GatewayUpTime|GatewayDownTime|GatewayRSSI|GatewaySNR|GatewayUplinkCount|GatewayDownlinkCount|GatewayJoinRequestCount|GatewayJoinAcceptCount",
        "Dimensions": [
            {"name": "DeviceId|GatewayId", "value": "string"}
        ],
        "AggregationPeriod": "OneHour|OneDay|OneWeek",
        "StartTimestamp": "timestamp",
        "EndTimestamp": "timestamp"
    }
]
```

**Output Schema:**
```json
{
    "SummaryMetricQueryResults": [
        {
            "QueryId": "string",
            "QueryStatus": "Succeeded|Failed",
            "Error": "string",
            "MetricName": "string",
            "Dimensions": [{"name": "string", "value": "string"}],
            "AggregationPeriod": "OneHour|OneDay|OneWeek",
            "StartTimestamp": "timestamp",
            "EndTimestamp": "timestamp",
            "Timestamps": ["timestamp"],
            "Values": [{"Min": "double", "Max": "double", "Sum": "double", "Avg": "double", "Std": "double", "P90": "double"}],
            "Unit": "string"
        }
    ]
}
```

---

### 11.2 `get-metric-configuration`

Gets the summary metric configuration.

**Synopsis:**
```bash
aws iotwireless get-metric-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "SummaryMetric": {
        "Status": "Enabled|Disabled"
    }
}
```

---

### 11.3 `update-metric-configuration`

Updates the metric configuration.

**Synopsis:**
```bash
aws iotwireless update-metric-configuration \
    [--summary-metric <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--summary-metric` | No | structure | None | Summary metric config |

**Structure:**
```json
{
    "Status": "Enabled|Disabled"
}
```

**Output:** None

---

### 11.4 `associate-aws-account-with-partner-account`

Associates an AWS account with a Sidewalk partner account.

**Synopsis:**
```bash
aws iotwireless associate-aws-account-with-partner-account \
    --sidewalk <value> \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sidewalk` | **Yes** | structure | -- | Sidewalk account info |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (max 200) |

**Sidewalk structure:**
```json
{
    "AmazonId": "string",
    "AppServerPrivateKey": "string"
}
```

**Output Schema:**
```json
{
    "Sidewalk": {
        "AmazonId": "string",
        "AppServerPrivateKey": "string"
    },
    "Arn": "string"
}
```

---

### 11.5 `disassociate-aws-account-from-partner-account`

Disassociates an AWS account from a partner account.

**Synopsis:**
```bash
aws iotwireless disassociate-aws-account-from-partner-account \
    --partner-account-id <value> \
    --partner-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--partner-account-id` | **Yes** | string | -- | Partner account ID |
| `--partner-type` | **Yes** | string | -- | `Sidewalk` |

**Output:** None

---

### 11.6 `get-partner-account`

Gets information about a partner account.

**Synopsis:**
```bash
aws iotwireless get-partner-account \
    --partner-account-id <value> \
    --partner-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--partner-account-id` | **Yes** | string | -- | Partner account ID |
| `--partner-type` | **Yes** | string | -- | `Sidewalk` |

**Output Schema:**
```json
{
    "Sidewalk": {
        "AmazonId": "string",
        "Fingerprint": "string",
        "Arn": "string"
    },
    "AccountLinked": "boolean"
}
```

---

### 11.7 `list-partner-accounts`

Lists partner accounts. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-partner-accounts \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (0-250) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Sidewalk": [
        {
            "AmazonId": "string",
            "Fingerprint": "string",
            "Arn": "string"
        }
    ]
}
```

---

### 11.8 `update-partner-account`

Updates a partner account configuration.

**Synopsis:**
```bash
aws iotwireless update-partner-account \
    --sidewalk <value> \
    --partner-account-id <value> \
    --partner-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sidewalk` | **Yes** | structure | -- | Updated Sidewalk config |
| `--partner-account-id` | **Yes** | string | -- | Partner account ID |
| `--partner-type` | **Yes** | string | -- | `Sidewalk` |

**Sidewalk structure:**
```json
{
    "AppServerPrivateKey": "string"
}
```

**Output:** None
