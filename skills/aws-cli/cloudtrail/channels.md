# Channels

### 5.1 `create-channel`

Creates a channel for CloudTrail Lake to receive events from external sources (non-AWS) or from CloudTrail event data stores in other accounts.

**Synopsis:**
```bash
aws cloudtrail create-channel \
    --name <value> \
    --source <value> \
    --destinations <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Channel name (3-128 chars) |
| `--source` | **Yes** | string | -- | Source of events. Use `Custom` for non-AWS sources, or an AWS partner name |
| `--destinations` | **Yes** | list | -- | Event data store destinations. Shorthand: `Type=EVENT_DATA_STORE,Location=string ...` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Destination Structure:**
```json
[
    {
        "Type": "EVENT_DATA_STORE|AWS_SERVICE",
        "Location": "string"
    }
]
```

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "Name": "string",
    "Source": "string",
    "Destinations": [
        {
            "Type": "EVENT_DATA_STORE|AWS_SERVICE",
            "Location": "string"
        }
    ],
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 5.2 `delete-channel`

Deletes a CloudTrail Lake channel.

**Synopsis:**
```bash
aws cloudtrail delete-channel \
    --channel <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel` | **Yes** | string | -- | Channel ARN |

**Output:** None (HTTP 200 on success)

---

### 5.3 `get-channel`

Returns information about a specific channel, including its source, destinations, and ingestion status.

**Synopsis:**
```bash
aws cloudtrail get-channel \
    --channel <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel` | **Yes** | string | -- | Channel ARN |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "Name": "string",
    "Source": "string",
    "SourceConfig": {
        "ApplyToAllRegions": true|false,
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
    },
    "Destinations": [
        {
            "Type": "EVENT_DATA_STORE|AWS_SERVICE",
            "Location": "string"
        }
    ],
    "IngestionStatus": {
        "LatestIngestionSuccessTime": "timestamp",
        "LatestIngestionSuccessEventID": "string",
        "LatestIngestionErrorCode": "string",
        "LatestIngestionAttemptTime": "timestamp",
        "LatestIngestionAttemptEventID": "string"
    }
}
```

---

### 5.4 `list-channels`

Lists channels in the current account. **Paginated operation.**

**Synopsis:**
```bash
aws cloudtrail list-channels \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Channels": [
        {
            "ChannelArn": "string",
            "Name": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `update-channel`

Updates a channel's name, source, or destinations.

**Synopsis:**
```bash
aws cloudtrail update-channel \
    --channel <value> \
    [--destinations <value>] \
    [--name <value>] \
    [--source <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel` | **Yes** | string | -- | Channel ARN |
| `--destinations` | No | list | unchanged | Updated destinations |
| `--name` | No | string | unchanged | New channel name |
| `--source` | No | string | unchanged | Updated source |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "Name": "string",
    "Source": "string",
    "Destinations": [
        {
            "Type": "EVENT_DATA_STORE|AWS_SERVICE",
            "Location": "string"
        }
    ]
}
```
