# Video Analysis

All video analysis follows a start/get pattern: call `start-*` to begin asynchronous processing of an S3-stored video, then call `get-*` to retrieve results. The `start-*` commands return a `JobId`; use optional `--notification-channel` for SNS completion notifications.

---

### 5.1 `start-label-detection`

Starts asynchronous detection of labels (objects/scenes) in a stored video.

**Synopsis:**
```bash
aws rekognition start-label-detection \
    --video <value> \
    [--client-request-token <value>] \
    [--min-confidence <value>] \
    [--notification-channel <value>] \
    [--job-tag <value>] \
    [--features <value>] \
    [--settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--video` | **Yes** | structure | -- | Video S3 location. Shorthand: `S3Object={Bucket=string,Name=string}` |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |
| `--min-confidence` | No | float | 50 | Minimum confidence threshold (0-100) |
| `--notification-channel` | No | structure | -- | SNS notification. Shorthand: `SNSTopicArn=string,RoleArn=string` |
| `--job-tag` | No | string | -- | Job identifier (1-1024 chars) |
| `--features` | No | list(string) | -- | Currently: `GENERAL_LABELS` |
| `--settings` | No | structure | -- | Label inclusion/exclusion filters |

**Output Schema:**
```json
{
    "JobId": "string"
}
```

---

### 5.2 `get-label-detection`

Gets label detection results for a stored video.

**Synopsis:**
```bash
aws rekognition get-label-detection \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--sort-by <value>] \
    [--aggregate-by <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID from start-label-detection |
| `--max-results` | No | integer | -- | Maximum results to return |
| `--next-token` | No | string | -- | Pagination token |
| `--sort-by` | No | string | -- | Sort by: `NAME` or `TIMESTAMP` |
| `--aggregate-by` | No | string | -- | Aggregate by: `TIMESTAMPS` or `SEGMENTS` |

**Output Schema:**
```json
{
    "JobStatus": "IN_PROGRESS|SUCCEEDED|FAILED",
    "StatusMessage": "string",
    "VideoMetadata": {
        "Codec": "string",
        "DurationMillis": "long",
        "Format": "string",
        "FrameRate": "float",
        "FrameHeight": "long",
        "FrameWidth": "long",
        "ColorRange": "FULL|LIMITED"
    },
    "Labels": [
        {
            "Timestamp": "long",
            "Label": {
                "Name": "string",
                "Confidence": "float",
                "Instances": [],
                "Parents": [],
                "Categories": []
            },
            "StartTimestampMillis": "long",
            "EndTimestampMillis": "long",
            "DurationMillis": "long"
        }
    ],
    "NextToken": "string",
    "LabelModelVersion": "string",
    "JobId": "string",
    "Video": {},
    "JobTag": "string"
}
```

---

### 5.3 `start-face-detection`

Starts asynchronous face detection in a stored video.

**Synopsis:**
```bash
aws rekognition start-face-detection \
    --video <value> \
    [--client-request-token <value>] \
    [--notification-channel <value>] \
    [--face-attributes <value>] \
    [--job-tag <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--video` | **Yes** | structure | -- | Video S3 location |
| `--client-request-token` | No | string | auto | Idempotency token |
| `--notification-channel` | No | structure | -- | SNS notification config |
| `--face-attributes` | No | string | `DEFAULT` | Facial attributes: `DEFAULT` or `ALL` |
| `--job-tag` | No | string | -- | Job identifier |

**Output Schema:**
```json
{"JobId": "string"}
```

---

### 5.4 `get-face-detection`

Gets face detection results for a stored video.

**Synopsis:**
```bash
aws rekognition get-face-detection \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--max-results` | No | integer | -- | Maximum results |
| `--next-token` | No | string | -- | Pagination token |

---

### 5.5 `start-face-search`

Starts asynchronous face search in a stored video against a face collection.

**Synopsis:**
```bash
aws rekognition start-face-search \
    --video <value> \
    --collection-id <value> \
    [--client-request-token <value>] \
    [--face-match-threshold <value>] \
    [--notification-channel <value>] \
    [--job-tag <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--video` | **Yes** | structure | -- | Video S3 location |
| `--collection-id` | **Yes** | string | -- | Face collection to search |
| `--face-match-threshold` | No | float | 80 | Minimum match confidence (0-100) |
| `--notification-channel` | No | structure | -- | SNS notification config |

**Output Schema:**
```json
{"JobId": "string"}
```

---

### 5.6 `get-face-search`

Gets face search results for a stored video.

**Synopsis:**
```bash
aws rekognition get-face-search \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--sort-by <value>]
```

---

### 5.7 `start-celebrity-recognition`

Starts asynchronous celebrity recognition in a stored video.

**Synopsis:**
```bash
aws rekognition start-celebrity-recognition \
    --video <value> \
    [--client-request-token <value>] \
    [--notification-channel <value>] \
    [--job-tag <value>]
```

---

### 5.8 `get-celebrity-recognition`

Gets celebrity recognition results for a stored video.

**Synopsis:**
```bash
aws rekognition get-celebrity-recognition \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--sort-by <value>]
```

---

### 5.9 `start-content-moderation`

Starts asynchronous content moderation in a stored video.

**Synopsis:**
```bash
aws rekognition start-content-moderation \
    --video <value> \
    [--min-confidence <value>] \
    [--client-request-token <value>] \
    [--notification-channel <value>] \
    [--job-tag <value>]
```

---

### 5.10 `get-content-moderation`

Gets content moderation results for a stored video.

**Synopsis:**
```bash
aws rekognition get-content-moderation \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--sort-by <value>] \
    [--aggregate-by <value>]
```

---

### 5.11 `start-person-tracking`

Starts asynchronous person tracking in a stored video.

**Synopsis:**
```bash
aws rekognition start-person-tracking \
    --video <value> \
    [--client-request-token <value>] \
    [--notification-channel <value>] \
    [--job-tag <value>]
```

---

### 5.12 `get-person-tracking`

Gets person tracking results for a stored video.

**Synopsis:**
```bash
aws rekognition get-person-tracking \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--sort-by <value>]
```

---

### 5.13 `start-segment-detection`

Starts asynchronous segment detection (shots, technical cues) in a stored video.

**Synopsis:**
```bash
aws rekognition start-segment-detection \
    --video <value> \
    --segment-types <value> \
    [--filters <value>] \
    [--client-request-token <value>] \
    [--notification-channel <value>] \
    [--job-tag <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--video` | **Yes** | structure | -- | Video S3 location |
| `--segment-types` | **Yes** | list(string) | -- | Segment types: `TECHNICAL_CUE`, `SHOT` |
| `--filters` | No | structure | -- | Detection filters |

---

### 5.14 `get-segment-detection`

Gets segment detection results for a stored video.

**Synopsis:**
```bash
aws rekognition get-segment-detection \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>]
```

---

### 5.15 `start-text-detection`

Starts asynchronous text detection in a stored video.

**Synopsis:**
```bash
aws rekognition start-text-detection \
    --video <value> \
    [--client-request-token <value>] \
    [--notification-channel <value>] \
    [--job-tag <value>] \
    [--filters <value>]
```

---

### 5.16 `get-text-detection`

Gets text detection results for a stored video.

**Synopsis:**
```bash
aws rekognition get-text-detection \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>]
```
