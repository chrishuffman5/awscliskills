# Event Selectors

### 2.1 `get-event-selectors`

Returns the event selectors configured for a trail, including basic event selectors and advanced event selectors.

**Synopsis:**
```bash
aws cloudtrail get-event-selectors \
    --trail-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trail-name` | **Yes** | string | -- | Trail name or ARN |

**Output Schema:**
```json
{
    "TrailARN": "string",
    "EventSelectors": [
        {
            "ReadWriteType": "ReadOnly|WriteOnly|All",
            "IncludeManagementEvents": true|false,
            "DataResources": [
                {
                    "Type": "string",
                    "Values": ["string"]
                }
            ],
            "ExcludeManagementEventSources": ["string"]
        }
    ],
    "AdvancedEventSelectors": [
        {
            "Name": "string",
            "FieldSelectors": [
                {
                    "Field": "string",
                    "Equals": ["string"],
                    "StartsWith": ["string"],
                    "EndsWith": ["string"],
                    "NotEquals": ["string"],
                    "NotStartsWith": ["string"],
                    "NotEndsWith": ["string"]
                }
            ]
        }
    ]
}
```

---

### 2.2 `put-event-selectors`

Configures event selectors for a trail. Use basic event selectors or advanced event selectors (not both). Advanced event selectors provide finer control over data event logging.

**Synopsis:**
```bash
aws cloudtrail put-event-selectors \
    --trail-name <value> \
    [--event-selectors <value>] \
    [--advanced-event-selectors <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trail-name` | **Yes** | string | -- | Trail name or ARN |
| `--event-selectors` | No | list | None | Basic event selectors (max 5). Cannot be used with `--advanced-event-selectors` |
| `--advanced-event-selectors` | No | list | None | Advanced event selectors. Cannot be used with `--event-selectors` |

**Basic Event Selector Structure:**
```json
[
    {
        "ReadWriteType": "ReadOnly|WriteOnly|All",
        "IncludeManagementEvents": true|false,
        "DataResources": [
            {
                "Type": "AWS::S3::Object|AWS::Lambda::Function|AWS::DynamoDB::Table|...",
                "Values": ["arn:aws:s3:::my-bucket/", "arn:aws:s3"]
            }
        ],
        "ExcludeManagementEventSources": ["kms.amazonaws.com", "rdsdata.amazonaws.com"]
    }
]
```

**Advanced Event Selector Structure:**
```json
[
    {
        "Name": "string",
        "FieldSelectors": [
            {
                "Field": "eventCategory|eventName|eventSource|eventType|readOnly|resources.type|resources.ARN",
                "Equals": ["string"],
                "StartsWith": ["string"],
                "EndsWith": ["string"],
                "NotEquals": ["string"],
                "NotStartsWith": ["string"],
                "NotEndsWith": ["string"]
            }
        ]
    }
]
```

**Common Advanced Event Selector Fields:**

| Field | Description |
|-------|-------------|
| `eventCategory` | `Management`, `Data`, `Insight`, `NetworkActivity` |
| `eventName` | API action name (e.g., `GetObject`) |
| `eventSource` | Service source (e.g., `s3.amazonaws.com`) |
| `readOnly` | `true` for read events, `false` for write events |
| `resources.type` | Resource type (e.g., `AWS::S3::Object`, `AWS::Lambda::Function`) |
| `resources.ARN` | Resource ARN pattern |

**Output Schema:**
```json
{
    "TrailARN": "string",
    "EventSelectors": [],
    "AdvancedEventSelectors": []
}
```

---

### 2.3 `get-insight-selectors`

Returns the insight selectors configured for a trail.

**Synopsis:**
```bash
aws cloudtrail get-insight-selectors \
    [--trail-name <value>] \
    [--event-data-store <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trail-name` | No | string | None | Trail name or ARN |
| `--event-data-store` | No | string | None | Event data store ARN or ID |

**Output Schema:**
```json
{
    "TrailARN": "string",
    "InsightSelectors": [
        {
            "InsightType": "ApiCallRateInsight|ApiErrorRateInsight"
        }
    ],
    "EventDataStoreArn": "string",
    "InsightsDestination": "string"
}
```

---

### 2.4 `put-insight-selectors`

Enables or disables CloudTrail Insights event collection for a trail. Insights identify unusual API call rates and error rates.

**Synopsis:**
```bash
aws cloudtrail put-insight-selectors \
    [--trail-name <value>] \
    --insight-selectors <value> \
    [--event-data-store <value>] \
    [--insights-destination <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trail-name` | No | string | None | Trail name or ARN |
| `--insight-selectors` | **Yes** | list | -- | Insight types to enable. Shorthand: `InsightType=ApiCallRateInsight ...` |
| `--event-data-store` | No | string | None | Source event data store ARN |
| `--insights-destination` | No | string | None | Destination event data store ARN for insights |

**Insight Types:**

| Type | Description |
|------|-------------|
| `ApiCallRateInsight` | Detects unusual API call volume |
| `ApiErrorRateInsight` | Detects unusual API error rates |

**Output Schema:**
```json
{
    "TrailARN": "string",
    "InsightSelectors": [
        {
            "InsightType": "ApiCallRateInsight|ApiErrorRateInsight"
        }
    ],
    "EventDataStoreArn": "string",
    "InsightsDestination": "string"
}
```
