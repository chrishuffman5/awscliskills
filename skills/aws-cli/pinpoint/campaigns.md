# Campaigns

### 2.1 `create-campaign`

Creates a new campaign for an application.

**Synopsis:**
```bash
aws pinpoint create-campaign \
    --application-id <value> \
    --write-campaign-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--write-campaign-request` | **Yes** | structure | -- | Campaign configuration (JSON recommended) |

**WriteCampaignRequest Key Fields:**
- `Name` (string): Campaign name
- `Description` (string): Campaign description
- `SegmentId` (string): Target segment ID
- `SegmentVersion` (integer): Segment version
- `Schedule` (structure): `StartTime` (required: `IMMEDIATE` or ISO 8601), `EndTime`, `Frequency` (`ONCE|HOURLY|DAILY|WEEKLY|MONTHLY|EVENT|IN_APP_EVENT`), `IsLocalTime`, `Timezone`, `QuietTime`, `EventFilter`
- `MessageConfiguration` (structure): Channel-specific messages (`EmailMessage`, `SMSMessage`, `GCMMessage`, `APNSMessage`, `ADMMessage`, `BaiduMessage`, `DefaultMessage`, `InAppMessage`, `CustomMessage`)
- `TemplateConfiguration` (structure): Template references per channel
- `Limits` (structure): `Daily`, `Total`, `MessagesPerSecond`, `MaximumDuration`, `Session`
- `HoldoutPercent` (integer): Percent of segment to exclude
- `IsPaused` (boolean): Pause the campaign
- `AdditionalTreatments` (list): A/B testing treatments
- `Hook` (structure): Lambda code hook
- `Priority` (integer): Display priority

**Output Schema:**
```json
{
    "CampaignResponse": {
        "ApplicationId": "string",
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SegmentId": "string",
        "SegmentVersion": "integer",
        "State": {"CampaignStatus": "SCHEDULED|EXECUTING|PENDING_NEXT_RUN|COMPLETED|PAUSED|DELETED|INVALID"},
        "Schedule": {},
        "MessageConfiguration": {},
        "Limits": {},
        "CreationDate": "string",
        "LastModifiedDate": "string",
        "Version": "integer"
    }
}
```

---

### 2.2 `get-campaign`

Gets information about a campaign.

**Synopsis:**
```bash
aws pinpoint get-campaign \
    --application-id <value> \
    --campaign-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--campaign-id` | **Yes** | string | -- | Campaign ID |

**Output Schema:** Same as `CampaignResponse` above.

---

### 2.3 `get-campaigns`

Lists campaigns for an application.

**Synopsis:**
```bash
aws pinpoint get-campaigns \
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
    "CampaignsResponse": {
        "Item": [{"CampaignResponse": "..."}],
        "NextToken": "string"
    }
}
```

---

### 2.4 `update-campaign`

Updates a campaign.

**Synopsis:**
```bash
aws pinpoint update-campaign \
    --application-id <value> \
    --campaign-id <value> \
    --write-campaign-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--campaign-id` | **Yes** | string | -- | Campaign ID |
| `--write-campaign-request` | **Yes** | structure | -- | Updated campaign configuration |

**Output Schema:** Same as `CampaignResponse`.

---

### 2.5 `delete-campaign`

Deletes a campaign.

**Synopsis:**
```bash
aws pinpoint delete-campaign \
    --application-id <value> \
    --campaign-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--campaign-id` | **Yes** | string | -- | Campaign ID |

**Output Schema:** Same as `CampaignResponse`.

---

### 2.6 `get-campaign-activities`

Gets activity information for a campaign.

**Synopsis:**
```bash
aws pinpoint get-campaign-activities \
    --application-id <value> \
    --campaign-id <value> \
    [--page-size <value>] \
    [--token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--campaign-id` | **Yes** | string | -- | Campaign ID |
| `--page-size` | No | string | None | Max items per page |
| `--token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ActivitiesResponse": {
        "Item": [
            {
                "ApplicationId": "string",
                "CampaignId": "string",
                "Id": "string",
                "State": "string",
                "SuccessfulEndpointCount": "integer",
                "TotalEndpointCount": "integer",
                "Start": "string",
                "End": "string",
                "Result": "string",
                "TreatmentId": "string",
                "ExecutionMetrics": {}
            }
        ],
        "NextToken": "string"
    }
}
```

---

### 2.7 `get-campaign-date-range-kpi`

Gets KPI data for a campaign over a date range.

**Synopsis:**
```bash
aws pinpoint get-campaign-date-range-kpi \
    --application-id <value> \
    --campaign-id <value> \
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
| `--campaign-id` | **Yes** | string | -- | Campaign ID |
| `--kpi-name` | **Yes** | string | -- | KPI metric name |
| `--start-time` | No | timestamp | 7 days ago | Start time |
| `--end-time` | No | timestamp | Now | End time |

**Output Schema:**
```json
{
    "CampaignDateRangeKpiResponse": {
        "ApplicationId": "string",
        "CampaignId": "string",
        "KpiName": "string",
        "KpiResult": {},
        "StartTime": "timestamp",
        "EndTime": "timestamp"
    }
}
```

---

### 2.8 `get-campaign-version`

Gets a specific version of a campaign.

**Synopsis:**
```bash
aws pinpoint get-campaign-version \
    --application-id <value> \
    --campaign-id <value> \
    --version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--campaign-id` | **Yes** | string | -- | Campaign ID |
| `--version` | **Yes** | string | -- | Version number |

**Output Schema:** Same as `CampaignResponse`.

---

### 2.9 `get-campaign-versions`

Lists versions of a campaign.

**Synopsis:**
```bash
aws pinpoint get-campaign-versions \
    --application-id <value> \
    --campaign-id <value> \
    [--page-size <value>] \
    [--token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--campaign-id` | **Yes** | string | -- | Campaign ID |
| `--page-size` | No | string | None | Max items per page |
| `--token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "CampaignsResponse": {
        "Item": [{"CampaignResponse": "..."}],
        "NextToken": "string"
    }
}
```
