# Campaigns

### 6.1 `create-campaign`

Creates a data collection campaign targeting a vehicle or fleet.

**Synopsis:**
```bash
aws iotfleetwise create-campaign \
    --name <value> \
    --signal-catalog-arn <value> \
    --target-arn <value> \
    --collection-scheme <value> \
    [--description <value>] \
    [--start-time <value>] \
    [--expiry-time <value>] \
    [--post-trigger-collection-duration <value>] \
    [--diagnostics-mode <value>] \
    [--spooling-mode <value>] \
    [--compression <value>] \
    [--priority <value>] \
    [--signals-to-collect <value>] \
    [--data-extra-dimensions <value>] \
    [--tags <value>] \
    [--data-destination-configs <value>] \
    [--data-partitions <value>] \
    [--signals-to-fetch <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Campaign name (1-100 chars) |
| `--signal-catalog-arn` | **Yes** | string | -- | ARN of the signal catalog |
| `--target-arn` | **Yes** | string | -- | ARN of the vehicle or fleet |
| `--collection-scheme` | **Yes** | structure | -- | Time-based or condition-based collection |
| `--description` | No | string | None | Description (1-2048 chars) |
| `--start-time` | No | timestamp | 0 | Delivery time after approval (ms) |
| `--expiry-time` | No | timestamp | 253402214400 | Campaign expiry (epoch seconds) |
| `--post-trigger-collection-duration` | No | long | 0 | Data collection after trigger (ms, 0-4294967295) |
| `--diagnostics-mode` | No | string | OFF | `OFF` or `SEND_ACTIVE_DTCS` |
| `--spooling-mode` | No | string | OFF | `OFF` or `TO_DISK` |
| `--compression` | No | string | SNAPPY | `OFF` or `SNAPPY` |
| `--priority` | No | integer | 0 | Priority (lower deploys first, min 0) |
| `--signals-to-collect` | No | list | None | Signals to collect (0-1000) |
| `--data-extra-dimensions` | No | list | None | Vehicle attributes to enrich data (0-5) |
| `--tags` | No | list | None | Tags (max 50) |
| `--data-destination-configs` | No | list | None | Data destinations (1-3) |
| `--data-partitions` | No | list | None | Data partition configs (1-20) |
| `--signals-to-fetch` | No | list | None | Signals to fetch from vehicle (1-2) |

**Collection Scheme (tagged union):**

Time-based:
```json
{
    "timeBasedCollectionScheme": {
        "periodMs": 60000
    }
}
```
- `periodMs` (required): Collection interval (10000-86400000 ms)

Condition-based:
```json
{
    "conditionBasedCollectionScheme": {
        "expression": "$variable.`Vehicle.Speed` >= 100.0",
        "minimumTriggerIntervalMs": 0,
        "triggerMode": "RISING_EDGE",
        "conditionLanguageVersion": 1
    }
}
```
- `triggerMode`: `ALWAYS` or `RISING_EDGE`

**Signals to Collect:**
```json
[
    {
        "name": "Vehicle.Speed",
        "maxSampleCount": 1000,
        "minimumSamplingIntervalMs": 100,
        "dataPartitionId": "default"
    }
]
```

**Data Destination Configs (tagged union):**

S3:
```json
{
    "s3Config": {
        "bucketArn": "arn:aws:s3:::my-bucket",
        "dataFormat": "JSON|PARQUET",
        "storageCompressionFormat": "NONE|GZIP",
        "prefix": "vehicle-data"
    }
}
```

Timestream:
```json
{
    "timestreamConfig": {
        "timestreamTableArn": "string",
        "executionRoleArn": "string"
    }
}
```

MQTT Topic:
```json
{
    "mqttTopicConfig": {
        "mqttTopicArn": "string",
        "executionRoleArn": "string"
    }
}
```

**Data Partitions:**
```json
[
    {
        "id": "string",
        "storageOptions": {
            "maximumSize": {"unit": "MB|GB|TB", "value": 100},
            "storageLocation": "string",
            "minimumTimeToLive": {"unit": "HOURS|DAYS|WEEKS", "value": 7}
        },
        "uploadOptions": {
            "expression": "string",
            "conditionLanguageVersion": 1
        }
    }
]
```

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 6.2 `get-campaign`

Retrieves information about a campaign.

**Synopsis:**
```bash
aws iotfleetwise get-campaign \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Campaign name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "description": "string",
    "signalCatalogArn": "string",
    "targetArn": "string",
    "status": "CREATING|WAITING_FOR_APPROVAL|RUNNING|SUSPENDED",
    "startTime": "timestamp",
    "expiryTime": "timestamp",
    "postTriggerCollectionDuration": "long",
    "diagnosticsMode": "OFF|SEND_ACTIVE_DTCS",
    "spoolingMode": "OFF|TO_DISK",
    "compression": "OFF|SNAPPY",
    "priority": "integer",
    "signalsToCollect": [
        {
            "name": "string",
            "maxSampleCount": "long",
            "minimumSamplingIntervalMs": "long",
            "dataPartitionId": "string"
        }
    ],
    "collectionScheme": {
        "timeBasedCollectionScheme": {"periodMs": "long"},
        "conditionBasedCollectionScheme": {
            "expression": "string",
            "minimumTriggerIntervalMs": "long",
            "triggerMode": "ALWAYS|RISING_EDGE",
            "conditionLanguageVersion": "integer"
        }
    },
    "dataExtraDimensions": ["string"],
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp",
    "dataDestinationConfigs": [
        {
            "s3Config": {
                "bucketArn": "string",
                "dataFormat": "JSON|PARQUET",
                "storageCompressionFormat": "NONE|GZIP",
                "prefix": "string"
            },
            "timestreamConfig": {
                "timestreamTableArn": "string",
                "executionRoleArn": "string"
            },
            "mqttTopicConfig": {
                "mqttTopicArn": "string",
                "executionRoleArn": "string"
            }
        }
    ],
    "dataPartitions": [],
    "signalsToFetch": []
}
```

---

### 6.3 `list-campaigns`

Lists campaigns. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-campaigns \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | Filter: `CREATING`, `WAITING_FOR_APPROVAL`, `RUNNING`, `SUSPENDED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "campaignSummaries": [
        {
            "name": "string",
            "arn": "string",
            "description": "string",
            "signalCatalogArn": "string",
            "targetArn": "string",
            "status": "CREATING|WAITING_FOR_APPROVAL|RUNNING|SUSPENDED",
            "creationTime": "timestamp",
            "lastModificationTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.4 `update-campaign`

Updates a campaign or changes its status (approve, suspend, resume).

**Synopsis:**
```bash
aws iotfleetwise update-campaign \
    --name <value> \
    --action <value> \
    [--description <value>] \
    [--data-extra-dimensions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Campaign name |
| `--action` | **Yes** | string | -- | `APPROVE`, `SUSPEND`, `RESUME`, or `UPDATE` |
| `--description` | No | string | None | Updated description |
| `--data-extra-dimensions` | No | list | None | Vehicle attributes (0-5) |

**Output Schema:**
```json
{
    "arn": "string",
    "name": "string",
    "status": "CREATING|WAITING_FOR_APPROVAL|RUNNING|SUSPENDED"
}
```

---

### 6.5 `delete-campaign`

Deletes a campaign. Suspends data collection on all vehicles.

**Synopsis:**
```bash
aws iotfleetwise delete-campaign \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Campaign name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```
