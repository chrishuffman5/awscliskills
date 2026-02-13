# Events

### 8.1 `lookup-events`

Looks up management and data events captured by CloudTrail. Returns events for the last 90 days. For longer retention, use CloudTrail Lake. **Paginated operation.**

**Synopsis:**
```bash
aws cloudtrail lookup-events \
    [--lookup-attributes <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--event-category <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lookup-attributes` | No | list | None | Attributes to filter events. Shorthand: `AttributeKey=string,AttributeValue=string ...` |
| `--start-time` | No | timestamp | None | Return events after this time |
| `--end-time` | No | timestamp | None | Return events before this time |
| `--event-category` | No | string | None | Event category: `insight` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 50) |
| `--max-items` | No | integer | None | Total items to return |

**Lookup Attribute Keys:**

| Key | Description |
|-----|-------------|
| `EventId` | Event ID |
| `EventName` | Event name (e.g., `RunInstances`) |
| `ReadOnly` | Read-only status (`true` or `false`) |
| `Username` | IAM identity name |
| `ResourceType` | Resource type (e.g., `AWS::EC2::Instance`) |
| `ResourceName` | Resource name or ID |
| `EventSource` | Event source (e.g., `ec2.amazonaws.com`) |
| `AccessKeyId` | Access key ID used |

**Output Schema:**
```json
{
    "Events": [
        {
            "EventId": "string",
            "EventName": "string",
            "ReadOnly": "string",
            "AccessKeyId": "string",
            "EventTime": "timestamp",
            "EventSource": "string",
            "Username": "string",
            "Resources": [
                {
                    "ResourceType": "string",
                    "ResourceName": "string"
                }
            ],
            "CloudTrailEvent": "string"
        }
    ],
    "NextToken": "string"
}
```

The `CloudTrailEvent` field is a JSON string containing the full event record, including:
- `eventVersion`, `eventSource`, `eventName`, `awsRegion`
- `sourceIPAddress`, `userAgent`, `userIdentity`
- `requestParameters`, `responseElements`
- `errorCode`, `errorMessage` (if the API call failed)

---

### 8.2 `get-trail-status`

Returns the current logging status, latest delivery timestamps, and any error information for a trail.

**Synopsis:**
```bash
aws cloudtrail get-trail-status \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trail name or ARN |

**Output Schema:**
```json
{
    "IsLogging": true|false,
    "LatestDeliveryError": "string",
    "LatestNotificationError": "string",
    "LatestDeliveryTime": "timestamp",
    "LatestNotificationTime": "timestamp",
    "StartLoggingTime": "timestamp",
    "StopLoggingTime": "timestamp",
    "LatestCloudWatchLogsDeliveryError": "string",
    "LatestCloudWatchLogsDeliveryTime": "timestamp",
    "LatestDigestDeliveryTime": "timestamp",
    "LatestDigestDeliveryError": "string",
    "LatestDeliveryAttemptTime": "string",
    "LatestNotificationAttemptTime": "string",
    "LatestNotificationAttemptSucceeded": "string",
    "LatestDeliveryAttemptSucceeded": "string",
    "TimeLoggingStarted": "string",
    "TimeLoggingStopped": "string"
}
```

**Key Fields:**

| Field | Description |
|-------|-------------|
| `IsLogging` | Whether the trail is currently logging |
| `LatestDeliveryError` | Last S3 delivery error (empty if no error) |
| `LatestDeliveryTime` | Timestamp of last successful S3 log delivery |
| `LatestDigestDeliveryTime` | Timestamp of last digest file delivery |
| `LatestCloudWatchLogsDeliveryError` | Last CloudWatch Logs delivery error |
