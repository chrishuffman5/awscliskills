# Jobs

### 2.1 `create-job`

Creates a transcoding job in a pipeline.

**Synopsis:**
```bash
aws elastictranscoder create-job \
    --pipeline-id <value> \
    [--inputs <value>] \
    [--input <value>] \
    [--outputs <value>] \
    [--output <value>] \
    [--output-key-prefix <value>] \
    [--playlists <value>] \
    [--user-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID for the job |
| `--inputs` | No | list | None | Input file(s) configuration (use for clip stitching) |
| `--input` | No | structure | None | Single input file (legacy, use `--inputs` instead) |
| `--outputs` | No | list | None | Output file configurations |
| `--output` | No | structure | None | Single output (legacy, use `--outputs` instead) |
| `--output-key-prefix` | No | string | None | Prefix for output file keys in S3 |
| `--playlists` | No | list | None | HLS/MPEG-DASH playlist configuration |
| `--user-metadata` | No | map | None | Custom metadata key-value pairs |

**Input structure:**
```json
{
    "Key": "string",
    "FrameRate": "auto|10|15|23.97|24|25|29.97|30|50|60",
    "Resolution": "auto|widthxheight",
    "AspectRatio": "auto|1:1|4:3|3:2|16:9",
    "Interlaced": "auto|true|false",
    "Container": "auto|3gp|aac|asf|avi|divx|flv|m4a|mkv|mov|mp3|mp4|mpeg|mpeg-ps|mpeg-ts|mxf|ogg|vob|wav|webm",
    "Encryption": {},
    "TimeSpan": {
        "StartTime": "string",
        "Duration": "string"
    },
    "InputCaptions": {}
}
```

**Output structure:**
```json
{
    "Key": "string",
    "ThumbnailPattern": "string",
    "ThumbnailEncryption": {},
    "Rotate": "auto|0|90|180|270",
    "PresetId": "string",
    "SegmentDuration": "string",
    "Watermarks": [],
    "Encryption": {},
    "Captions": {},
    "Composition": []
}
```

**Playlist structure:**
```json
{
    "Name": "string",
    "Format": "HLSv3|HLSv4|MPEG-DASH|Smooth",
    "OutputKeys": ["string"],
    "HlsContentProtection": {},
    "PlayReadyDrm": {}
}
```

**Output Schema:**
```json
{
    "Job": {
        "Id": "string",
        "Arn": "string",
        "PipelineId": "string",
        "Status": "Submitted|Progressing|Complete|Canceled|Error",
        "Inputs": [
            {
                "Key": "string",
                "FrameRate": "string",
                "Resolution": "string",
                "AspectRatio": "string",
                "Interlaced": "string",
                "Container": "string",
                "DetectedProperties": {
                    "Width": "integer",
                    "Height": "integer",
                    "FrameRate": "string",
                    "FileSize": "long",
                    "DurationMillis": "long"
                }
            }
        ],
        "Outputs": [
            {
                "Id": "string",
                "Key": "string",
                "PresetId": "string",
                "Status": "string",
                "StatusDetail": "string",
                "Duration": "long",
                "Width": "integer",
                "Height": "integer",
                "FrameRate": "string",
                "FileSize": "long",
                "DurationMillis": "long",
                "ThumbnailPattern": "string",
                "Watermarks": [],
                "Encryption": {},
                "AppliedColorSpaceConversion": "string"
            }
        ],
        "OutputKeyPrefix": "string",
        "Playlists": [],
        "UserMetadata": {},
        "Timing": {
            "SubmitTimeMillis": "long",
            "StartTimeMillis": "long",
            "FinishTimeMillis": "long"
        }
    }
}
```

---

### 2.2 `read-job`

Reads the settings and status of a job.

**Synopsis:**
```bash
aws elastictranscoder read-job \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Job ID |

**Output Schema:** Same as `create-job` output.

---

### 2.3 `cancel-job`

Cancels a job that has a status of Submitted. Cannot cancel jobs already progressing.

**Synopsis:**
```bash
aws elastictranscoder cancel-job \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Job ID to cancel |

**Output:** None

---

### 2.4 `list-jobs-by-pipeline`

Lists jobs for a specific pipeline. **Paginated operation.**

**Synopsis:**
```bash
aws elastictranscoder list-jobs-by-pipeline \
    --pipeline-id <value> \
    [--ascending <value>] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--ascending` | No | string | None | `true` for ascending, `false` for descending |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "Jobs": [
        {
            "Id": "string",
            "Arn": "string",
            "PipelineId": "string",
            "Status": "Submitted|Progressing|Complete|Canceled|Error",
            "Inputs": [],
            "Outputs": [],
            "OutputKeyPrefix": "string",
            "Playlists": [],
            "UserMetadata": {},
            "Timing": {}
        }
    ]
}
```

---

### 2.5 `list-jobs-by-status`

Lists jobs by status across all pipelines. **Paginated operation.**

**Synopsis:**
```bash
aws elastictranscoder list-jobs-by-status \
    --status <value> \
    [--ascending <value>] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | **Yes** | string | -- | `Submitted`, `Progressing`, `Complete`, `Canceled`, `Error` |
| `--ascending` | No | string | None | `true` for ascending, `false` for descending |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:** Same as `list-jobs-by-pipeline` output.
