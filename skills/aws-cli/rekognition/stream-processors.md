# Stream Processors

### 7.1 `create-stream-processor`

Creates a stream processor for real-time analysis of streaming video from Kinesis Video Streams.

**Synopsis:**
```bash
aws rekognition create-stream-processor \
    --input <value> \
    --name <value> \
    --settings <value> \
    --role-arn <value> \
    --stream-processor-output <value> \
    [--tags <value>] \
    [--notification-channel <value>] \
    [--kms-key-id <value>] \
    [--regions-of-interest <value>] \
    [--data-sharing-preference <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input` | **Yes** | structure | -- | Kinesis Video Stream input. Shorthand: `KinesisVideoStream={Arn=string}` |
| `--name` | **Yes** | string | -- | Name for the stream processor (1-128 chars) |
| `--settings` | **Yes** | structure | -- | Face search or connected home config |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for access |
| `--stream-processor-output` | **Yes** | structure | -- | Output destination (Kinesis Data Stream or S3) |
| `--tags` | No | map | -- | Key-value tags (max 200) |
| `--notification-channel` | No | structure | -- | SNS topic for notifications |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--regions-of-interest` | No | list | -- | Up to 10 regions (bounding boxes or polygons) |
| `--data-sharing-preference` | No | structure | -- | Data sharing opt-in preference |

**Settings Structure:**
```json
{
    "FaceSearch": {
        "CollectionId": "string",
        "FaceMatchThreshold": "float (0-100, default 80)"
    },
    "ConnectedHome": {
        "Labels": ["PERSON", "PET", "PACKAGE", "ALL"],
        "MinConfidence": "float (0-100)"
    }
}
```

**Output Schema:**
```json
{
    "StreamProcessorArn": "string"
}
```

---

### 7.2 `delete-stream-processor`

Deletes a stream processor.

**Synopsis:**
```bash
aws rekognition delete-stream-processor \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the stream processor |

**Output:** None (HTTP 200 on success)

---

### 7.3 `describe-stream-processor`

Describes a stream processor.

**Synopsis:**
```bash
aws rekognition describe-stream-processor \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the stream processor |

**Output Schema:**
```json
{
    "Name": "string",
    "StreamProcessorArn": "string",
    "Status": "STOPPED|STARTING|RUNNING|FAILED|STOPPING|UPDATING",
    "StatusMessage": "string",
    "CreationTimestamp": "timestamp",
    "LastUpdateTimestamp": "timestamp",
    "Input": {},
    "Output": {},
    "RoleArn": "string",
    "Settings": {},
    "NotificationChannel": {},
    "KmsKeyId": "string",
    "RegionsOfInterest": [],
    "DataSharingPreference": {}
}
```

---

### 7.4 `list-stream-processors`

Lists stream processors. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition list-stream-processors \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "StreamProcessors": [
        {
            "Name": "string",
            "Status": "string"
        }
    ]
}
```

---

### 7.5 `start-stream-processor`

Starts a stream processor.

**Synopsis:**
```bash
aws rekognition start-stream-processor \
    --name <value> \
    [--start-selector <value>] \
    [--stop-selector <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the stream processor |
| `--start-selector` | No | structure | -- | Start position (connected home only) |
| `--stop-selector` | No | structure | -- | Stop condition (connected home only) |

**Output Schema:**
```json
{
    "SessionId": "string"
}
```

---

### 7.6 `stop-stream-processor`

Stops a stream processor.

**Synopsis:**
```bash
aws rekognition stop-stream-processor \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the stream processor |

**Output:** None (HTTP 200 on success)

---

### 7.7 `update-stream-processor`

Updates the settings of a stream processor.

**Synopsis:**
```bash
aws rekognition update-stream-processor \
    --name <value> \
    [--settings-for-update <value>] \
    [--regions-of-interest-for-update <value>] \
    [--data-sharing-preference-for-update <value>] \
    [--parameters-to-delete <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the stream processor |
| `--settings-for-update` | No | structure | -- | Updated connected home settings |
| `--regions-of-interest-for-update` | No | list | -- | Updated regions of interest |
| `--data-sharing-preference-for-update` | No | structure | -- | Updated data sharing preference |
| `--parameters-to-delete` | No | list(string) | -- | Parameters to remove: `ConnectedHomeMinConfidence`, `RegionsOfInterest` |

**Output:** None (HTTP 200 on success)
