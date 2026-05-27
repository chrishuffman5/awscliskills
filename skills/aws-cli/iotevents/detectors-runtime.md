# Detectors Runtime

Commands from the `aws iotevents-data` service for managing detector instances at runtime.

## 4.1 `describe-detector`

Describes a detector instance state.

**Synopsis:**
```bash
aws iotevents-data describe-detector \
    --detector-model-name <value> \
    [--key-value <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-model-name` | **Yes** | string | -- | Detector model name (1-128 chars) |
| `--key-value` | No | string | None | Key value for the detector instance (1-128 chars) |

**Output Schema:**
```json
{
    "detector": {
        "detectorModelName": "string",
        "keyValue": "string",
        "detectorModelVersion": "string",
        "state": {
            "stateName": "string",
            "variables": [
                {"name": "string", "value": "string"}
            ],
            "timers": [
                {"name": "string", "timestamp": "timestamp"}
            ]
        },
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp"
    }
}
```

---

## 4.2 `list-detectors`

Lists detector instances for a model. **Paginated operation.**

**Synopsis:**
```bash
aws iotevents-data list-detectors \
    --detector-model-name <value> \
    [--state-name <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-model-name` | **Yes** | string | -- | Detector model name |
| `--state-name` | No | string | None | Filter by state name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "detectorSummaries": [
        {
            "detectorModelName": "string",
            "keyValue": "string",
            "detectorModelVersion": "string",
            "state": {"stateName": "string"},
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 4.3 `batch-put-message`

Sends messages (input data) to one or more detectors.

**Synopsis:**
```bash
aws iotevents-data batch-put-message \
    --messages <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--messages` | **Yes** | list | -- | Messages to send (min 1) |

**Message structure:**
```json
[
    {
        "messageId": "string",
        "inputName": "string",
        "payload": "blob",
        "timestamp": {"timeInMillis": "long"}
    }
]
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `messageId` | **Yes** | string | Unique message ID (1-64 chars) |
| `inputName` | **Yes** | string | Input name (1-128 chars) |
| `payload` | **Yes** | blob | JSON payload data |
| `timestamp` | No | structure | Optional timestamp |

**Output Schema:**
```json
{
    "BatchPutMessageErrorEntries": [
        {
            "messageId": "string",
            "errorCode": "ResourceNotFoundException|InvalidRequestException|InternalFailureException|ServiceUnavailableException|ThrottlingException",
            "errorMessage": "string"
        }
    ]
}
```

---

## 4.4 `batch-update-detector`

Updates one or more detector instances (state, variables, timers).

**Synopsis:**
```bash
aws iotevents-data batch-update-detector \
    --detectors <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detectors` | **Yes** | list | -- | Detector update requests (min 1) |

**Detector update request structure:**
```json
[
    {
        "messageId": "string",
        "detectorModelName": "string",
        "keyValue": "string",
        "state": {
            "stateName": "string",
            "variables": [{"name": "string", "value": "string"}],
            "timers": [{"name": "string", "seconds": "integer"}]
        }
    }
]
```

**Output Schema:**
```json
{
    "batchUpdateDetectorErrorEntries": [
        {
            "messageId": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

## 4.5 `batch-delete-detector`

Deletes one or more detector instances.

**Synopsis:**
```bash
aws iotevents-data batch-delete-detector \
    --detectors <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detectors` | **Yes** | list | -- | Detector delete requests (min 1) |

**Delete request structure:**
```json
[
    {
        "messageId": "string",
        "detectorModelName": "string",
        "keyValue": "string"
    }
]
```

**Output Schema:**
```json
{
    "batchDeleteDetectorErrorEntries": [
        {
            "messageId": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```
