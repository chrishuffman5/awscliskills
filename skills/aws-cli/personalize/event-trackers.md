# Event Trackers

### 8.1 `create-event-tracker`

Creates an event tracker that provides a tracking ID for recording real-time user events with the `put-events` API.

**Synopsis:**
```bash
aws personalize create-event-tracker \
    --name <value> \
    --dataset-group-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Event tracker name (1-63 chars) |
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the dataset group |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "eventTrackerArn": "string",
    "trackingId": "string"
}
```

---

### 8.2 `describe-event-tracker`

Describes an event tracker.

**Synopsis:**
```bash
aws personalize describe-event-tracker \
    --event-tracker-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-tracker-arn` | **Yes** | string | -- | ARN of the event tracker |

**Output Schema:**
```json
{
    "eventTracker": {
        "name": "string",
        "eventTrackerArn": "string",
        "accountId": "string",
        "trackingId": "string",
        "datasetGroupArn": "string",
        "status": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp"
    }
}
```

---

### 8.3 `list-event-trackers`

Lists event trackers for a dataset group. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-event-trackers \
    [--dataset-group-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | No | string | None | Filter by dataset group ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "eventTrackers": [
        {
            "name": "string",
            "eventTrackerArn": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.4 `delete-event-tracker`

Deletes an event tracker. Events previously recorded with the tracking ID are not affected.

**Synopsis:**
```bash
aws personalize delete-event-tracker \
    --event-tracker-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-tracker-arn` | **Yes** | string | -- | ARN of the event tracker to delete |

**Output:** None
