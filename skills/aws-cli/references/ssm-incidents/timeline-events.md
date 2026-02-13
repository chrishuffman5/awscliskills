# Timeline Events

### 5.1 `create-timeline-event`

Creates a custom timeline event on the incident details page.

**Synopsis:**
```bash
aws ssm-incidents create-timeline-event \
    --incident-record-arn <value> \
    --event-time <value> \
    --event-type <value> \
    --event-data <value> \
    [--event-references <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-record-arn` | **Yes** | string | -- | Incident record ARN |
| `--event-time` | **Yes** | timestamp | -- | Time the event occurred |
| `--event-type` | **Yes** | string | -- | Event type (e.g., `Custom Event`) |
| `--event-data` | **Yes** | string | -- | Event data (JSON string) |
| `--event-references` | No | list | None | Event references (related resources) |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "incidentRecordArn": "string",
    "eventId": "string"
}
```

---

### 5.2 `delete-timeline-event`

Deletes a timeline event from the incident.

**Synopsis:**
```bash
aws ssm-incidents delete-timeline-event \
    --incident-record-arn <value> \
    --event-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-record-arn` | **Yes** | string | -- | Incident record ARN |
| `--event-id` | **Yes** | string | -- | Event ID to delete |

**Output Schema:**
```json
{}
```

---

### 5.3 `get-timeline-event`

Retrieves a timeline event.

**Synopsis:**
```bash
aws ssm-incidents get-timeline-event \
    --incident-record-arn <value> \
    --event-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-record-arn` | **Yes** | string | -- | Incident record ARN |
| `--event-id` | **Yes** | string | -- | Event ID |

**Output Schema:**
```json
{
    "event": {
        "incidentRecordArn": "string",
        "eventId": "string",
        "eventTime": "timestamp",
        "eventUpdatedTime": "timestamp",
        "eventType": "string",
        "eventData": "string",
        "eventReferences": [
            {
                "resource": "string",
                "relatedItemId": {
                    "type": "string",
                    "value": {}
                }
            }
        ]
    }
}
```

---

### 5.4 `list-timeline-events`

Lists timeline events for the specified incident record. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-incidents list-timeline-events \
    --incident-record-arn <value> \
    [--filters <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-record-arn` | **Yes** | string | -- | Incident record ARN |
| `--filters` | No | list | None | Filters |
| `--sort-by` | No | string | None | Sort field: `EVENT_TIME` |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "eventSummaries": [
        {
            "incidentRecordArn": "string",
            "eventId": "string",
            "eventTime": "timestamp",
            "eventUpdatedTime": "timestamp",
            "eventType": "string",
            "eventReferences": []
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `update-timeline-event`

Updates a timeline event.

**Synopsis:**
```bash
aws ssm-incidents update-timeline-event \
    --incident-record-arn <value> \
    --event-id <value> \
    [--event-time <value>] \
    [--event-type <value>] \
    [--event-data <value>] \
    [--event-references <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-record-arn` | **Yes** | string | -- | Incident record ARN |
| `--event-id` | **Yes** | string | -- | Event ID |
| `--event-time` | No | timestamp | None | Updated event time |
| `--event-type` | No | string | None | Updated event type |
| `--event-data` | No | string | None | Updated event data |
| `--event-references` | No | list | None | Updated event references |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{}
```
