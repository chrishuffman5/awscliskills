# Applications

### 1.1 `create-app`

Creates an Amazon Pinpoint application (project).

**Synopsis:**
```bash
aws pinpoint create-app \
    --create-application-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--create-application-request` | **Yes** | structure | -- | Application settings. Shorthand: `Name=string,tags={key1=val1}` |

**CreateApplicationRequest Fields:**
- `Name` (string, **required**): Application display name
- `tags` (map, optional): Key-value tag pairs

**Output Schema:**
```json
{
    "ApplicationResponse": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "tags": {"string": "string"},
        "CreationDate": "string"
    }
}
```

---

### 1.2 `get-app`

Gets information about an application.

**Synopsis:**
```bash
aws pinpoint get-app \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |

**Output Schema:**
```json
{
    "ApplicationResponse": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "tags": {"string": "string"},
        "CreationDate": "string"
    }
}
```

---

### 1.3 `get-apps`

Lists all applications (projects).

**Synopsis:**
```bash
aws pinpoint get-apps \
    [--page-size <value>] \
    [--token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-size` | No | string | None | Max number of items per page |
| `--token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ApplicationsResponse": {
        "Item": [
            {
                "Arn": "string",
                "Id": "string",
                "Name": "string",
                "tags": {"string": "string"},
                "CreationDate": "string"
            }
        ],
        "NextToken": "string"
    }
}
```

---

### 1.4 `delete-app`

Deletes an application and all associated settings.

**Synopsis:**
```bash
aws pinpoint delete-app \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |

**Output Schema:**
```json
{
    "ApplicationResponse": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "tags": {"string": "string"}
    }
}
```

---

### 1.5 `update-application-settings`

Updates the settings for an application.

**Synopsis:**
```bash
aws pinpoint update-application-settings \
    --application-id <value> \
    --write-application-settings-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--write-application-settings-request` | **Yes** | structure | -- | Application settings |

**WriteApplicationSettingsRequest Fields:**
- `CampaignHook` (structure): Lambda function settings for campaigns
- `CloudWatchMetricsEnabled` (boolean): Enable CloudWatch metrics
- `Limits` (structure): Default campaign messaging limits
- `QuietTime` (structure): Default quiet time (Start/End in HH:MM format)
- `JourneyLimits` (structure): Default journey messaging limits

**Output Schema:**
```json
{
    "ApplicationSettingsResource": {
        "ApplicationId": "string",
        "CampaignHook": {"LambdaFunctionName": "string", "Mode": "DELIVERY|FILTER", "WebUrl": "string"},
        "LastModifiedDate": "string",
        "Limits": {"Daily": "integer", "MaximumDuration": "integer", "MessagesPerSecond": "integer", "Total": "integer", "Session": "integer"},
        "QuietTime": {"Start": "string", "End": "string"},
        "JourneyLimits": {}
    }
}
```

---

### 1.6 `get-application-settings`

Gets the settings for an application.

**Synopsis:**
```bash
aws pinpoint get-application-settings \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |

**Output Schema:**
```json
{
    "ApplicationSettingsResource": {
        "ApplicationId": "string",
        "CampaignHook": {},
        "LastModifiedDate": "string",
        "Limits": {},
        "QuietTime": {},
        "JourneyLimits": {}
    }
}
```

---

### 1.7 `get-application-date-range-kpi`

Gets KPI data for an application over a date range.

**Synopsis:**
```bash
aws pinpoint get-application-date-range-kpi \
    --application-id <value> \
    --kpi-name <value> \
    [--end-time <value>] \
    [--start-time <value>] \
    [--page-size <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--kpi-name` | **Yes** | string | -- | KPI metric name |
| `--end-time` | No | timestamp | Now | End time for the query |
| `--start-time` | No | timestamp | 7 days ago | Start time for the query |
| `--page-size` | No | string | None | Max items per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ApplicationDateRangeKpiResponse": {
        "ApplicationId": "string",
        "KpiName": "string",
        "KpiResult": {
            "Rows": [{"GroupedBys": [], "Values": []}]
        },
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "NextToken": "string"
    }
}
```
