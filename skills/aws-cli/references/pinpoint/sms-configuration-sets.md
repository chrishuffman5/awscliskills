# SMS v2 Configuration Sets

All commands in this section use `aws pinpoint-sms-voice-v2`.

### 12.1 `create-configuration-set`

Creates a new configuration set for tracking SMS/Voice/MMS events.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-configuration-set \
    --configuration-set-name <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name (1-64 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ConfigurationSetArn": "string",
    "ConfigurationSetName": "string",
    "Tags": [{"Key": "string", "Value": "string"}],
    "CreatedTimestamp": "timestamp"
}
```

---

### 12.2 `describe-configuration-sets`

Describes configuration sets.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-configuration-sets \
    [--configuration-set-names <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-names` | No | list | None | Names or ARNs to describe |
| `--filters` | No | list | None | Filters. Name: `event-destination-name`, Values: list |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConfigurationSets": [
        {
            "ConfigurationSetArn": "string",
            "ConfigurationSetName": "string",
            "EventDestinations": [
                {
                    "EventDestinationName": "string",
                    "Enabled": "boolean",
                    "MatchingEventTypes": ["ALL|TEXT_ALL|TEXT_SENT|TEXT_PENDING|TEXT_QUEUED|TEXT_SUCCESSFUL|TEXT_DELIVERED|TEXT_INVALID|TEXT_INVALID_MESSAGE|TEXT_UNREACHABLE|TEXT_CARRIER_UNREACHABLE|TEXT_BLOCKED|TEXT_CARRIER_BLOCKED|TEXT_SPAM|TEXT_UNKNOWN|TEXT_TTL_EXPIRED|VOICE_ALL|VOICE_INITIATED|VOICE_RINGING|VOICE_ANSWERED|VOICE_COMPLETED|VOICE_BUSY|VOICE_NO_ANSWER|VOICE_FAILED|VOICE_TTL_EXPIRED|MEDIA_ALL|MEDIA_PENDING|MEDIA_QUEUED|MEDIA_SUCCESSFUL|MEDIA_DELIVERED|MEDIA_INVALID|MEDIA_INVALID_MESSAGE|MEDIA_UNREACHABLE|MEDIA_CARRIER_UNREACHABLE|MEDIA_BLOCKED|MEDIA_CARRIER_BLOCKED|MEDIA_SPAM|MEDIA_UNKNOWN|MEDIA_TTL_EXPIRED|MEDIA_FILE_INACCESSIBLE|MEDIA_FILE_TYPE_UNSUPPORTED|MEDIA_FILE_SIZE_EXCEEDED"],
                    "CloudWatchLogsDestination": {},
                    "KinesisFirehoseDestination": {},
                    "SnsDestination": {}
                }
            ],
            "DefaultMessageType": "TRANSACTIONAL|PROMOTIONAL",
            "DefaultSenderId": "string",
            "CreatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 12.3 `delete-configuration-set`

Deletes a configuration set.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-configuration-set \
    --configuration-set-name <value>
```

---

### 12.4 `create-event-destination`

Creates an event destination within a configuration set.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-event-destination \
    --configuration-set-name <value> \
    --event-destination-name <value> \
    --matching-event-types <value> \
    [--cloud-watch-logs-destination <value>] \
    [--kinesis-firehose-destination <value>] \
    [--sns-destination <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name |
| `--event-destination-name` | **Yes** | string | -- | Event destination name (1-64 chars) |
| `--matching-event-types` | **Yes** | list | -- | Event types to match |
| `--cloud-watch-logs-destination` | No | structure | None | CloudWatch Logs. Shorthand: `IamRoleArn=string,LogGroupArn=string` |
| `--kinesis-firehose-destination` | No | structure | None | Firehose. Shorthand: `IamRoleArn=string,DeliveryStreamArn=string` |
| `--sns-destination` | No | structure | None | SNS. Shorthand: `TopicArn=string` |

**Output Schema:**
```json
{
    "ConfigurationSetArn": "string",
    "ConfigurationSetName": "string",
    "EventDestination": {
        "EventDestinationName": "string",
        "Enabled": "boolean",
        "MatchingEventTypes": ["string"],
        "CloudWatchLogsDestination": {},
        "KinesisFirehoseDestination": {},
        "SnsDestination": {}
    }
}
```

---

### 12.5 `update-event-destination`

Updates an event destination.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 update-event-destination \
    --configuration-set-name <value> \
    --event-destination-name <value> \
    [--enabled | --no-enabled] \
    [--matching-event-types <value>] \
    [--cloud-watch-logs-destination <value>] \
    [--kinesis-firehose-destination <value>] \
    [--sns-destination <value>]
```

---

### 12.6 `delete-event-destination`

Deletes an event destination.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-event-destination \
    --configuration-set-name <value> \
    --event-destination-name <value>
```
