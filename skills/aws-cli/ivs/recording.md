# Recording

### 4.1 `create-recording-configuration`

Creates a recording configuration for automatically recording live streams to S3.

**Synopsis:**
```bash
aws ivs create-recording-configuration \
    --destination-configuration <value> \
    [--name <value>] \
    [--recording-reconnect-window-seconds <value>] \
    [--rendition-configuration <value>] \
    [--thumbnail-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-configuration` | **Yes** | structure | -- | S3 bucket for recordings |
| `--name` | No | string | None | Name (0-128 chars) |
| `--recording-reconnect-window-seconds` | No | integer | 0 | Reconnect window to merge streams (0-300) |
| `--rendition-configuration` | No | structure | None | Which renditions to record |
| `--thumbnail-configuration` | No | structure | None | Thumbnail recording settings |
| `--tags` | No | map | None | Key-value tag pairs |

**DestinationConfiguration:**
```json
{
    "s3": {"bucketName": "my-recording-bucket"}
}
```

**RenditionConfiguration:**
```json
{
    "renditionSelection": "ALL|NONE|CUSTOM",
    "renditions": ["SD", "HD", "FULL_HD", "LOWEST_RESOLUTION"]
}
```

**ThumbnailConfiguration:**
```json
{
    "recordingMode": "DISABLED|INTERVAL",
    "targetIntervalSeconds": 30,
    "resolution": "SD|HD|FULL_HD|LOWEST_RESOLUTION",
    "storage": ["SEQUENTIAL", "LATEST"]
}
```

**Output Schema:**
```json
{
    "recordingConfiguration": {
        "arn": "string",
        "name": "string",
        "state": "CREATING|CREATE_FAILED|ACTIVE",
        "destinationConfiguration": {"s3": {"bucketName": "string"}},
        "recordingReconnectWindowSeconds": "integer",
        "renditionConfiguration": {},
        "thumbnailConfiguration": {},
        "tags": {"string": "string"}
    }
}
```

---

### 4.2 `get-recording-configuration`

Gets details for a recording configuration.

**Synopsis:**
```bash
aws ivs get-recording-configuration \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the recording configuration |

**Output Schema:** Same as `create-recording-configuration` output.

---

### 4.3 `list-recording-configurations`

Lists recording configurations. **Paginated operation.**

**Synopsis:**
```bash
aws ivs list-recording-configurations \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "recordingConfigurations": [
        {"arn": "string", "name": "string", "state": "string", "destinationConfiguration": {}, "tags": {}}
    ],
    "nextToken": "string"
}
```

---

### 4.4 `delete-recording-configuration`

Deletes a recording configuration.

**Synopsis:**
```bash
aws ivs delete-recording-configuration \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the recording configuration to delete |

**Output:** None
