# Trackers

### 1.1 `create-tracker`

Creates a tracker resource to receive and store device position updates.

**Synopsis:**
```bash
aws location create-tracker \
    --tracker-name <value> \
    [--description <value>] \
    [--position-filtering <value>] \
    [--event-bridge-enabled | --no-event-bridge-enabled] \
    [--kms-key-id <value>] \
    [--kms-key-enable-geospatial-queries | --no-kms-key-enable-geospatial-queries] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name (1-100 chars, alphanumeric + `-._`) |
| `--description` | No | string | None | Optional description (0-1000 chars) |
| `--position-filtering` | No | string | `TimeBased` | Filtering mode: `TimeBased`, `DistanceBased`, `AccuracyBased` |
| `--event-bridge-enabled` | No | boolean | false | Enable position UPDATE events to EventBridge |
| `--kms-key-id` | No | string | None | AWS KMS key for encryption |
| `--kms-key-enable-geospatial-queries` | No | boolean | false | Enable geospatial queries for KMS-encrypted tracker |
| `--tags` | No | map | None | Resource tags (max 50) |

**Output Schema:**
```json
{
    "TrackerName": "string",
    "TrackerArn": "string",
    "CreateTime": "timestamp"
}
```

---

### 1.2 `delete-tracker`

Deletes a tracker resource.

**Synopsis:**
```bash
aws location delete-tracker \
    --tracker-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Name of the tracker to delete |

**Output Schema:**

None (empty response on success).

---

### 1.3 `describe-tracker`

Retrieves the tracker resource details.

**Synopsis:**
```bash
aws location describe-tracker \
    --tracker-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Name of the tracker |

**Output Schema:**
```json
{
    "TrackerName": "string",
    "TrackerArn": "string",
    "Description": "string",
    "PositionFiltering": "TimeBased|DistanceBased|AccuracyBased",
    "EventBridgeEnabled": "boolean",
    "KmsKeyEnableGeospatialQueries": "boolean",
    "KmsKeyId": "string",
    "Tags": { "string": "string" },
    "CreateTime": "timestamp",
    "UpdateTime": "timestamp"
}
```

---

### 1.4 `list-trackers`

Lists tracker resources. **Paginated operation.**

**Synopsis:**
```bash
aws location list-trackers \
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
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Entries": [
        {
            "TrackerName": "string",
            "Description": "string",
            "CreateTime": "timestamp",
            "UpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-tracker`

Updates the specified properties of a tracker.

**Synopsis:**
```bash
aws location update-tracker \
    --tracker-name <value> \
    [--description <value>] \
    [--position-filtering <value>] \
    [--event-bridge-enabled | --no-event-bridge-enabled] \
    [--kms-key-enable-geospatial-queries | --no-kms-key-enable-geospatial-queries] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker to update |
| `--description` | No | string | None | New description |
| `--position-filtering` | No | string | None | New filtering mode |
| `--event-bridge-enabled` | No | boolean | None | Toggle EventBridge |
| `--kms-key-enable-geospatial-queries` | No | boolean | None | Toggle geospatial queries |

**Output Schema:**
```json
{
    "TrackerName": "string",
    "TrackerArn": "string",
    "UpdateTime": "timestamp"
}
```

---

### 1.6 `batch-update-device-position`

Uploads position updates for one or more devices to a tracker (max 10 per batch).

**Synopsis:**
```bash
aws location batch-update-device-position \
    --tracker-name <value> \
    --updates <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Target tracker name |
| `--updates` | **Yes** | list | -- | Position updates (1-10 items) |

**Updates Structure:**
```json
[
    {
        "DeviceId": "string",
        "Position": [longitude, latitude],
        "SampleTime": "timestamp",
        "Accuracy": { "Horizontal": "double" },
        "PositionProperties": { "string": "string" }
    }
]
```

**Output Schema:**
```json
{
    "Errors": [
        {
            "DeviceId": "string",
            "SampleTime": "timestamp",
            "Error": { "Code": "string", "Message": "string" }
        }
    ]
}
```

---

### 1.7 `batch-get-device-position`

Retrieves the current position for multiple devices from a tracker.

**Synopsis:**
```bash
aws location batch-get-device-position \
    --tracker-name <value> \
    --device-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--device-ids` | **Yes** | list(string) | -- | Device IDs to query (1-10) |

**Output Schema:**
```json
{
    "DevicePositions": [
        {
            "DeviceId": "string",
            "TrackerName": "string",
            "Position": ["double", "double"],
            "Accuracy": { "Horizontal": "double" },
            "PositionProperties": {},
            "SampleTime": "timestamp",
            "ReceivedTime": "timestamp"
        }
    ],
    "Errors": [
        { "DeviceId": "string", "Error": { "Code": "string", "Message": "string" } }
    ]
}
```

---

### 1.8 `batch-delete-device-position-history`

Deletes the position history for one or more devices from a tracker.

**Synopsis:**
```bash
aws location batch-delete-device-position-history \
    --tracker-name <value> \
    --device-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--device-ids` | **Yes** | list(string) | -- | Device IDs (1-100) |

**Output Schema:**
```json
{
    "Errors": [
        { "DeviceId": "string", "Error": { "Code": "string", "Message": "string" } }
    ]
}
```

---

### 1.9 `get-device-position`

Retrieves the latest device position.

**Synopsis:**
```bash
aws location get-device-position \
    --tracker-name <value> \
    --device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--device-id` | **Yes** | string | -- | Device identifier |

**Output Schema:**
```json
{
    "DeviceId": "string",
    "Position": ["double", "double"],
    "Accuracy": { "Horizontal": "double" },
    "PositionProperties": {},
    "SampleTime": "timestamp",
    "ReceivedTime": "timestamp"
}
```

---

### 1.10 `get-device-position-history`

Retrieves the position history for a device. **Paginated operation.**

**Synopsis:**
```bash
aws location get-device-position-history \
    --tracker-name <value> \
    --device-id <value> \
    [--start-time-inclusive <value>] \
    [--end-time-exclusive <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--device-id` | **Yes** | string | -- | Device identifier |
| `--start-time-inclusive` | No | timestamp | None | Start of time range |
| `--end-time-exclusive` | No | timestamp | None | End of time range |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "DevicePositions": [
        {
            "DeviceId": "string",
            "Position": ["double", "double"],
            "Accuracy": { "Horizontal": "double" },
            "PositionProperties": {},
            "SampleTime": "timestamp",
            "ReceivedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.11 `list-device-positions`

Lists device positions for a tracker. **Paginated operation.**

**Synopsis:**
```bash
aws location list-device-positions \
    --tracker-name <value> \
    [--filter-geometry <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--filter-geometry` | No | structure | None | Geometry filter for positions |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Entries": [
        {
            "DeviceId": "string",
            "Position": ["double", "double"],
            "Accuracy": { "Horizontal": "double" },
            "PositionProperties": {},
            "SampleTime": "timestamp",
            "ReceivedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.12 `verify-device-position`

Verifies a device position against geofences associated with the tracker.

**Synopsis:**
```bash
aws location verify-device-position \
    --tracker-name <value> \
    --device-state <value> \
    [--distance-unit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--device-state` | **Yes** | structure | -- | Device position state to verify |
| `--distance-unit` | No | string | `Kilometers` | `Kilometers` or `Miles` |

**Output Schema:**
```json
{
    "InferredState": {
        "Position": ["double", "double"],
        "Accuracy": { "Horizontal": "double" },
        "DeviationDistance": "double",
        "ProxyDetected": "boolean"
    }
}
```

---

### 1.13 `associate-tracker-consumer`

Associates a geofence collection with a tracker for automatic geofence evaluation.

**Synopsis:**
```bash
aws location associate-tracker-consumer \
    --tracker-name <value> \
    --consumer-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--consumer-arn` | **Yes** | string | -- | ARN of the geofence collection |

**Output Schema:**

None (empty response on success).

---

### 1.14 `disassociate-tracker-consumer`

Removes a geofence collection association from a tracker.

**Synopsis:**
```bash
aws location disassociate-tracker-consumer \
    --tracker-name <value> \
    --consumer-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--consumer-arn` | **Yes** | string | -- | ARN of the geofence collection to disassociate |

**Output Schema:**

None (empty response on success).

---

### 1.15 `list-tracker-consumers`

Lists geofence collections associated with a tracker. **Paginated operation.**

**Synopsis:**
```bash
aws location list-tracker-consumers \
    --tracker-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracker-name` | **Yes** | string | -- | Tracker name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "ConsumerArns": ["string"],
    "NextToken": "string"
}
```
