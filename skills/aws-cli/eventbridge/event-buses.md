# Event Buses

### 1.1 `create-event-bus`

Creates a new custom event bus or a partner event bus.

**Synopsis:**
```bash
aws events create-event-bus \
    --name <value> \
    [--event-source-name <value>] \
    [--description <value>] \
    [--kms-key-identifier <value>] \
    [--dead-letter-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the event bus (max 256 chars) |
| `--event-source-name` | No | string | None | Partner event source name (for partner event buses only) |
| `--description` | No | string | None | Description of the event bus |
| `--kms-key-identifier` | No | string | None | KMS key ARN for encryption |
| `--dead-letter-config` | No | structure | None | Dead-letter queue config. Shorthand: `Arn=string` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "EventBusArn": "string",
    "Description": "string",
    "DeadLetterConfig": {
        "Arn": "string"
    },
    "KmsKeyIdentifier": "string"
}
```

---

### 1.2 `delete-event-bus`

Deletes a custom event bus. Cannot delete the default event bus.

**Synopsis:**
```bash
aws events delete-event-bus \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the event bus to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-event-bus`

Displays details about an event bus, including its policy and configuration.

**Synopsis:**
```bash
aws events describe-event-bus \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | `default` | Name or ARN of the event bus |

**Output Schema:**
```json
{
    "Name": "string",
    "Arn": "string",
    "Description": "string",
    "KmsKeyIdentifier": "string",
    "DeadLetterConfig": {
        "Arn": "string"
    },
    "Policy": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 1.4 `list-event-buses`

Lists all event buses in the account, including the default event bus, custom event buses, and partner event buses. **Paginated operation.**

**Synopsis:**
```bash
aws events list-event-buses \
    [--name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by name prefix |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EventBuses": [
        {
            "Name": "string",
            "Arn": "string",
            "Description": "string",
            "Policy": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `put-events`

Sends one or more custom events to the specified event bus (max 10 entries per call).

**Synopsis:**
```bash
aws events put-events \
    --entries <value> \
    [--endpoint-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entries` | **Yes** | list | -- | Event entries (max 10 per call) |
| `--endpoint-id` | No | string | None | Global endpoint ID for multi-region routing |

**Entry Structure:**
```json
[
    {
        "Time": "timestamp",
        "Source": "string",
        "Resources": ["string"],
        "DetailType": "string",
        "Detail": "string",
        "EventBusName": "string",
        "TraceHeader": "string"
    }
]
```

**Output Schema:**
```json
{
    "FailedEntryCount": "integer",
    "Entries": [
        {
            "EventId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 1.6 `put-partner-events`

Sends events from a partner event source. Used by SaaS partner integrations.

**Synopsis:**
```bash
aws events put-partner-events \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entries` | **Yes** | list | -- | Partner event entries |

**Entry Structure:**
```json
[
    {
        "Time": "timestamp",
        "Source": "string",
        "Resources": ["string"],
        "DetailType": "string",
        "Detail": "string"
    }
]
```

**Output Schema:**
```json
{
    "FailedEntryCount": "integer",
    "Entries": [
        {
            "EventId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```
