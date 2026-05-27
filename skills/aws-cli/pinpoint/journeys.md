# Journeys

### 3.1 `create-journey`

Creates a journey for an application.

**Synopsis:**
```bash
aws pinpoint create-journey \
    --application-id <value> \
    --write-journey-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--write-journey-request` | **Yes** | structure | -- | Journey configuration (JSON recommended) |

**WriteJourneyRequest Key Fields:**
- `Name` (string, **required**): Journey name
- `StartActivity` (string): ID of the first activity
- `Activities` (map): Map of activity ID to Activity definition
- `StartCondition` (structure): How users enter the journey
- `Schedule` (structure): Journey schedule with `StartTime`, `EndTime`, `Timezone`
- `Limits` (structure): `DailyCap`, `TotalCap`, `MessagesPerSecond`, `EndpointReentryCap`, `EndpointReentryInterval`
- `QuietTime` (structure): Default quiet time
- `State` (string): `DRAFT`, `ACTIVE`, `COMPLETED`, `CANCELLED`, `CLOSED`, `PAUSED`
- `LocalTime` (boolean): Use local time zone
- `RefreshFrequency` (string): Segment refresh frequency
- `WaitForQuietTime` (boolean): Wait for quiet time before sending

**Output Schema:**
```json
{
    "JourneyResponse": {
        "ApplicationId": "string",
        "Id": "string",
        "Name": "string",
        "State": "DRAFT|ACTIVE|COMPLETED|CANCELLED|CLOSED|PAUSED",
        "Activities": {},
        "StartActivity": "string",
        "StartCondition": {},
        "Schedule": {},
        "Limits": {},
        "CreationDate": "string",
        "LastModifiedDate": "string"
    }
}
```

---

### 3.2 `get-journey`

Gets journey details.

**Synopsis:**
```bash
aws pinpoint get-journey \
    --application-id <value> \
    --journey-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--journey-id` | **Yes** | string | -- | Journey ID |

**Output Schema:** Same as `JourneyResponse` above.

---

### 3.3 `list-journeys`

Lists journeys for an application.

**Synopsis:**
```bash
aws pinpoint list-journeys \
    --application-id <value> \
    [--page-size <value>] \
    [--token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--page-size` | No | string | None | Max items per page |
| `--token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "JourneysResponse": {
        "Item": [{"JourneyResponse": "..."}],
        "NextToken": "string"
    }
}
```

---

### 3.4 `update-journey`

Updates a journey.

**Synopsis:**
```bash
aws pinpoint update-journey \
    --application-id <value> \
    --journey-id <value> \
    --write-journey-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--journey-id` | **Yes** | string | -- | Journey ID |
| `--write-journey-request` | **Yes** | structure | -- | Updated journey configuration |

**Output Schema:** Same as `JourneyResponse`.

---

### 3.5 `delete-journey`

Deletes a journey.

**Synopsis:**
```bash
aws pinpoint delete-journey \
    --application-id <value> \
    --journey-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--journey-id` | **Yes** | string | -- | Journey ID |

**Output Schema:** Same as `JourneyResponse`.

---

### 3.6 `update-journey-state`

Starts, pauses, or cancels a journey.

**Synopsis:**
```bash
aws pinpoint update-journey-state \
    --application-id <value> \
    --journey-id <value> \
    --journey-state-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--journey-id` | **Yes** | string | -- | Journey ID |
| `--journey-state-request` | **Yes** | structure | -- | Shorthand: `State=ACTIVE|PAUSED|CANCELLED|COMPLETED|CLOSED` |

**Output Schema:** Same as `JourneyResponse`.

---

### 3.7 `get-journey-date-range-kpi`

Gets KPI data for a journey over a date range.

**Synopsis:**
```bash
aws pinpoint get-journey-date-range-kpi \
    --application-id <value> \
    --journey-id <value> \
    --kpi-name <value> \
    [--start-time <value>] \
    [--end-time <value>] \
    [--page-size <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--journey-id` | **Yes** | string | -- | Journey ID |
| `--kpi-name` | **Yes** | string | -- | KPI metric name |
| `--start-time` | No | timestamp | 7 days ago | Start time |
| `--end-time` | No | timestamp | Now | End time |

**Output Schema:**
```json
{
    "JourneyDateRangeKpiResponse": {
        "ApplicationId": "string",
        "JourneyId": "string",
        "KpiName": "string",
        "KpiResult": {},
        "StartTime": "timestamp",
        "EndTime": "timestamp"
    }
}
```

---

### 3.8 `get-journey-execution-metrics`

Gets execution metrics for a journey.

**Synopsis:**
```bash
aws pinpoint get-journey-execution-metrics \
    --application-id <value> \
    --journey-id <value> \
    [--next-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--journey-id` | **Yes** | string | -- | Journey ID |

**Output Schema:**
```json
{
    "JourneyExecutionMetricsResponse": {
        "ApplicationId": "string",
        "JourneyId": "string",
        "LastEvaluatedTime": "string",
        "Metrics": {"string": "string"}
    }
}
```

---

### 3.9 `get-journey-execution-activity-metrics`

Gets execution metrics for a specific activity in a journey.

**Synopsis:**
```bash
aws pinpoint get-journey-execution-activity-metrics \
    --application-id <value> \
    --journey-id <value> \
    --journey-activity-id <value> \
    [--next-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--journey-id` | **Yes** | string | -- | Journey ID |
| `--journey-activity-id` | **Yes** | string | -- | Activity ID |

**Output Schema:**
```json
{
    "JourneyExecutionActivityMetricsResponse": {
        "ApplicationId": "string",
        "JourneyId": "string",
        "JourneyActivityId": "string",
        "ActivityType": "string",
        "LastEvaluatedTime": "string",
        "Metrics": {"string": "string"}
    }
}
```

---

### 3.10-3.12 Journey Runs

`get-journey-runs`, `get-journey-run-execution-metrics`, and `get-journey-run-execution-activity-metrics` follow the same pattern as above with additional `--run-id` parameter for run-specific queries.

**Common Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--journey-id` | **Yes** | string | -- | Journey ID |
| `--run-id` | **Yes** | string | -- | Journey run ID (for run-specific commands) |
