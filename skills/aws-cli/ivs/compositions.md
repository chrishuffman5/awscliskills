# Compositions (Real-Time)

### 8.1 `start-composition`

Starts a server-side composition that combines participants from a stage into a single video output.

**Synopsis:**
```bash
aws ivs-realtime start-composition \
    --stage-arn <value> \
    --destinations <value> \
    [--layout <value>] \
    [--idempotency-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | ARN of the stage to composite |
| `--destinations` | **Yes** | list | -- | Output destinations (1-2, channel or S3) |
| `--layout` | No | structure | Grid | Layout: `grid` or `pip` (picture-in-picture) |
| `--idempotency-token` | No | string | Auto | Idempotency token (1-64 chars) |
| `--tags` | No | map | None | Key-value tag pairs |

**Destination — Channel:**
```json
[{
    "name": "string",
    "channel": {
        "channelArn": "string",
        "encoderConfigurationArn": "string"
    }
}]
```

**Destination — S3:**
```json
[{
    "name": "string",
    "s3": {
        "storageConfigurationArn": "string",
        "encoderConfigurationArns": ["string"],
        "recordingConfiguration": {
            "format": "HLS",
            "hlsConfiguration": {"targetSegmentDurationSeconds": 6}
        }
    }
}]
```

**Grid Layout:**
```json
{
    "grid": {
        "featuredParticipantAttribute": "string",
        "omitStoppedVideo": false,
        "videoAspectRatio": "AUTO|VIDEO|SQUARE|PORTRAIT",
        "videoFillMode": "FILL|COVER|CONTAIN",
        "gridGap": 2
    }
}
```

**PiP Layout:**
```json
{
    "pip": {
        "featuredParticipantAttribute": "string",
        "pipPosition": "TOP_LEFT|TOP_RIGHT|BOTTOM_LEFT|BOTTOM_RIGHT",
        "pipWidth": 360,
        "pipHeight": 240,
        "pipOffset": 0,
        "pipBehavior": "STATIC|DYNAMIC",
        "videoFillMode": "FILL|COVER|CONTAIN",
        "gridGap": 2
    }
}
```

**Output Schema:**
```json
{
    "composition": {
        "arn": "string",
        "stageArn": "string",
        "state": "STARTING|ACTIVE|STOPPING|FAILED|STOPPED",
        "layout": {},
        "destinations": [
            {
                "id": "string",
                "state": "STARTING|ACTIVE|STOPPING|RECONNECTING|FAILED|STOPPED",
                "startTime": "timestamp",
                "endTime": "timestamp",
                "configuration": {},
                "detail": {"s3": {"recordingPrefix": "string"}}
            }
        ],
        "tags": {"string": "string"},
        "startTime": "timestamp",
        "endTime": "timestamp"
    }
}
```

---

### 8.2 `get-composition`

Gets details for a composition.

**Synopsis:**
```bash
aws ivs-realtime get-composition \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the composition |

**Output Schema:** Same as `start-composition` output.

---

### 8.3 `list-compositions`

Lists compositions. **Paginated operation.**

**Synopsis:**
```bash
aws ivs-realtime list-compositions \
    [--filter-by-stage-arn <value>] \
    [--filter-by-encoder-configuration-arn <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-by-stage-arn` | No | string | None | Filter by stage ARN |
| `--filter-by-encoder-configuration-arn` | No | string | None | Filter by encoder config ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

---

### 8.4 `stop-composition`

Stops a composition.

**Synopsis:**
```bash
aws ivs-realtime stop-composition \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the composition to stop |

**Output:** None
