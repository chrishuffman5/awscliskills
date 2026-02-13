# Geofences

### 2.1 `create-geofence-collection`

Creates a geofence collection to store and manage geofences.

**Synopsis:**
```bash
aws location create-geofence-collection \
    --collection-name <value> \
    [--description <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Collection name (1-100 chars) |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--kms-key-id` | No | string | None | KMS key for encryption |
| `--tags` | No | map | None | Resource tags (max 50) |

**Output Schema:**
```json
{ "CollectionName": "string", "CollectionArn": "string", "CreateTime": "timestamp" }
```

---

### 2.2 `delete-geofence-collection`

**Synopsis:**
```bash
aws location delete-geofence-collection --collection-name <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Collection to delete |

**Output:** None.

---

### 2.3 `describe-geofence-collection`

**Synopsis:**
```bash
aws location describe-geofence-collection --collection-name <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Collection name |

**Output Schema:**
```json
{
    "CollectionName": "string", "CollectionArn": "string", "Description": "string",
    "KmsKeyId": "string", "Tags": {}, "CreateTime": "timestamp", "UpdateTime": "timestamp",
    "GeofenceCount": "integer"
}
```

---

### 2.4 `list-geofence-collections`

**Paginated operation.**

**Synopsis:**
```bash
aws location list-geofence-collections [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

**Output Schema:**
```json
{ "Entries": [{ "CollectionName": "string", "Description": "string", "CreateTime": "timestamp", "UpdateTime": "timestamp" }], "NextToken": "string" }
```

---

### 2.5 `update-geofence-collection`

**Synopsis:**
```bash
aws location update-geofence-collection --collection-name <value> [--description <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Collection to update |
| `--description` | No | string | None | New description |

**Output Schema:**
```json
{ "CollectionName": "string", "CollectionArn": "string", "UpdateTime": "timestamp" }
```

---

### 2.6 `put-geofence`

Adds or updates a geofence in a collection.

**Synopsis:**
```bash
aws location put-geofence \
    --collection-name <value> \
    --geofence-id <value> \
    --geometry <value> \
    [--geofence-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Target collection |
| `--geofence-id` | **Yes** | string | -- | Geofence identifier (1-100 chars) |
| `--geometry` | **Yes** | structure | -- | Geofence shape (Polygon, Circle, MultiPolygon, or Geobuf) |
| `--geofence-properties` | No | map | None | Properties (max 3 key-value pairs) |

**Geometry Structure:**
```json
{
    "Polygon": [[[lng,lat], [lng,lat], ...]],
    "Circle": { "Center": [lng, lat], "Radius": "double" },
    "MultiPolygon": [[[[lng,lat], ...]]],
    "Geobuf": "blob"
}
```

**Output Schema:**
```json
{ "GeofenceId": "string", "CreateTime": "timestamp", "UpdateTime": "timestamp" }
```

---

### 2.7 `get-geofence`

**Synopsis:**
```bash
aws location get-geofence --collection-name <value> --geofence-id <value>
```

**Output Schema:**
```json
{
    "GeofenceId": "string", "Geometry": { "Polygon": [], "Circle": {} },
    "GeofenceProperties": {}, "Status": "ACTIVE|DELETED",
    "CreateTime": "timestamp", "UpdateTime": "timestamp"
}
```

---

### 2.8 `list-geofences`

**Paginated operation.**

**Synopsis:**
```bash
aws location list-geofences --collection-name <value> [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

**Output Schema:**
```json
{ "Entries": [{ "GeofenceId": "string", "Geometry": {}, "GeofenceProperties": {}, "Status": "string", "CreateTime": "timestamp", "UpdateTime": "timestamp" }], "NextToken": "string" }
```

---

### 2.9 `batch-put-geofence`

Adds multiple geofences to a collection (max 10 per batch).

**Synopsis:**
```bash
aws location batch-put-geofence --collection-name <value> --entries <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Target collection |
| `--entries` | **Yes** | list | -- | Geofence entries (1-10) |

**Output Schema:**
```json
{
    "Successes": [{ "GeofenceId": "string", "CreateTime": "timestamp", "UpdateTime": "timestamp" }],
    "Errors": [{ "GeofenceId": "string", "Error": { "Code": "string", "Message": "string" } }]
}
```

---

### 2.10 `batch-delete-geofence`

Deletes multiple geofences (max 10 per batch).

**Synopsis:**
```bash
aws location batch-delete-geofence --collection-name <value> --geofence-ids <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Target collection |
| `--geofence-ids` | **Yes** | list(string) | -- | Geofence IDs to delete (1-10) |

**Output Schema:**
```json
{ "Errors": [{ "GeofenceId": "string", "Error": { "Code": "string", "Message": "string" } }] }
```

---

### 2.11 `batch-evaluate-geofences`

Evaluates device positions against geofences in a collection.

**Synopsis:**
```bash
aws location batch-evaluate-geofences --collection-name <value> --device-position-updates <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Geofence collection |
| `--device-position-updates` | **Yes** | list | -- | Device positions to evaluate (1-10) |

**Output Schema:**
```json
{ "Errors": [{ "DeviceId": "string", "SampleTime": "timestamp", "Error": { "Code": "string", "Message": "string" } }] }
```

---

### 2.12 `forecast-geofence-events`

Forecasts future geofence events based on device trajectory. **Paginated operation.**

**Synopsis:**
```bash
aws location forecast-geofence-events \
    --collection-name <value> \
    --device-state <value> \
    [--time-horizon-minutes <value>] \
    [--distance-unit <value>] \
    [--speed-unit <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-name` | **Yes** | string | -- | Geofence collection |
| `--device-state` | **Yes** | structure | -- | Current device position, speed, and heading |
| `--time-horizon-minutes` | No | double | None | Forecast horizon in minutes |
| `--distance-unit` | No | string | `Kilometers` | `Kilometers` or `Miles` |
| `--speed-unit` | No | string | `KilometersPerHour` | `KilometersPerHour` or `MilesPerHour` |

**Output Schema:**
```json
{
    "ForecastedEvents": [
        {
            "EventId": "string", "GeofenceId": "string",
            "IsDeviceInGeofence": "boolean", "NearestDistance": "double",
            "EventType": "ENTER|EXIT",
            "ForecastedBreachTime": "timestamp",
            "GeofenceProperties": {}
        }
    ],
    "DistanceUnit": "string",
    "SpeedUnit": "string",
    "NextToken": "string"
}
```
