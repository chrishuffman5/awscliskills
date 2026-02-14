# Metrics

### 19.1 `get-current-metric-data`

Gets current metric data for queues.

**Synopsis:**
```bash
aws connect get-current-metric-data \
    --instance-id <value> \
    --filters <value> \
    --current-metrics <value> \
    [--groupings <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--sort-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--filters` | **Yes** | structure | -- | Filters: `Queues`, `Channels`, `RoutingProfiles`, `RoutingStepExpressions` |
| `--current-metrics` | **Yes** | list | -- | Metrics to retrieve |
| `--groupings` | No | list | None | `QUEUE`, `CHANNEL`, `ROUTING_PROFILE`, `ROUTING_STEP_EXPRESSION` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--sort-criteria` | No | list | None | Sort criteria |

**Common Metrics:** `AGENTS_ONLINE`, `AGENTS_AVAILABLE`, `AGENTS_ON_CALL`, `AGENTS_NON_PRODUCTIVE`, `AGENTS_AFTER_CONTACT_WORK`, `AGENTS_ERROR`, `AGENTS_STAFFED`, `CONTACTS_IN_QUEUE`, `OLDEST_CONTACT_AGE`, `CONTACTS_SCHEDULED`, `AGENTS_ON_CONTACT`, `SLOTS_ACTIVE`, `SLOTS_AVAILABLE`

**Output Schema:**
```json
{
    "MetricResults": [
        {
            "Dimensions": { "Queue": { "Id": "string", "Arn": "string" }, "Channel": "string", "RoutingProfile": {} },
            "Collections": [ { "Metric": { "Name": "string", "Unit": "SECONDS|COUNT|PERCENT" }, "Value": "double" } ]
        }
    ],
    "DataSnapshotTime": "timestamp",
    "ApproximateTotalCount": "long",
    "NextToken": "string"
}
```

---

### 19.2 `get-metric-data`

Gets historical metric data. **Paginated operation.**

**Synopsis:**
```bash
aws connect get-metric-data \
    --instance-id <value> \
    --start-time <value> \
    --end-time <value> \
    --filters <value> \
    --historical-metrics <value> \
    [--groupings <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--start-time` | **Yes** | timestamp | -- | Start time (UTC) |
| `--end-time` | **Yes** | timestamp | -- | End time (UTC) |
| `--filters` | **Yes** | structure | -- | Filters: `Queues`, `Channels` |
| `--historical-metrics` | **Yes** | list | -- | Metrics with Name, Threshold, Statistic, Unit |
| `--groupings` | No | list | None | `QUEUE`, `CHANNEL` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "MetricResults": [
        {
            "Dimensions": { "Queue": {}, "Channel": "string" },
            "Collections": [ { "Metric": {}, "Value": "double" } ]
        }
    ],
    "NextToken": "string"
}
```

---

### 19.3 `get-metric-data-v2`

Gets historical metric data (v2) with enhanced filters and groupings. **Paginated operation.**

**Synopsis:**
```bash
aws connect get-metric-data-v2 \
    --resource-arn <value> \
    --start-time <value> \
    --end-time <value> \
    --filters <value> \
    --metrics <value> \
    [--interval <value>] \
    [--groupings <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Instance ARN |
| `--start-time` | **Yes** | timestamp | -- | Start time (epoch) |
| `--end-time` | **Yes** | timestamp | -- | End time (epoch) |
| `--filters` | **Yes** | list | -- | Filters with FilterKey and FilterValues (max 5 keys, 100 values) |
| `--metrics` | **Yes** | list | -- | Metrics by Name or MetricId (max 20) |
| `--interval` | No | structure | None | `IntervalPeriod`: `FIFTEEN_MIN`, `THIRTY_MIN`, `HOUR`, `DAY`, `WEEK`, `TOTAL` |
| `--groupings` | No | list | None | Groupings (max 4): `AGENT`, `QUEUE`, `CHANNEL`, `ROUTING_PROFILE`, etc. |
| `--next-token` | No | string | None | Pagination token (max 2500) |
| `--max-results` | No | integer | None | Max results (1-100) |

**Filter Keys:** `AGENT`, `QUEUE`, `ROUTING_PROFILE`, `CHANNEL`, `CAMPAIGN`, `FEATURE`, `FLOWS_RESOURCE_ID`, `DISCONNECT_REASON`, `EVALUATION_FORM`, `ROUTING_STEP_EXPRESSION`

**Common Metrics:** `AVG_HANDLE_TIME`, `CONTACTS_HANDLED`, `CONTACTS_ABANDONED`, `ABANDONMENT_RATE`, `AVG_QUEUE_ANSWER_TIME`, `SERVICE_LEVEL`, `AGENT_OCCUPANCY`, `AVG_CONTACT_DURATION`, `SUM_AFTER_CONTACT_WORK_TIME`, `CONTACTS_QUEUED`

**Output Schema:**
```json
{
    "NextToken": "string",
    "MetricResults": [
        {
            "Dimensions": { "key": "value" },
            "MetricInterval": { "Interval": "string", "StartTime": "timestamp", "EndTime": "timestamp" },
            "Collections": [
                { "Metric": { "Name": "string", "MetricId": "string", "Threshold": [], "MetricFilters": [] }, "Value": "double" }
            ]
        }
    ]
}
```

---

### 19.4 `get-federation-token`

Retrieves a token for federation (SSO).

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output Schema:**
```json
{
    "Credentials": {
        "AccessToken": "string",
        "AccessTokenExpiration": "timestamp",
        "RefreshToken": "string",
        "RefreshTokenExpiration": "timestamp"
    },
    "SignInUrl": "string",
    "UserArn": "string",
    "UserId": "string"
}
```
