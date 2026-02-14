# Jobs Query & Resource Share

### 8.1 `start-jobs-query`

Starts an advanced asynchronous query for jobs with multiple filter criteria including codec type, engine version, and standard job attributes.

**Synopsis:**
```bash
aws mediaconvert start-jobs-query \
    [--filter-list <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--order <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-list` | No | list | None | Array of filter objects |
| `--max-results` | No | integer | None | Number of jobs to return (1-20) |
| `--next-token` | No | string | None | Pagination token |
| `--order` | No | string | None | `ASCENDING` or `DESCENDING` |

**Filter structure:**
```json
[
    {
        "Key": "string",
        "Values": ["string"]
    }
]
```

**Supported filter keys:**
- `queue` — Queue name or ARN
- `status` — `SUBMITTED`, `PROGRESSING`, `COMPLETE`, `CANCELED`, `ERROR`
- `fileInput` — Input file URL or partial name
- `jobEngineVersionRequested` — Requested engine version (YYYY-MM-DD)
- `jobEngineVersionUsed` — Used engine version (YYYY-MM-DD)
- `audioCodec` — `AAC`, `MP2`, `MP3`, `WAV`, `AIFF`, `AC3`, `EAC3`, etc.
- `videoCodec` — `AV1`, `H_264`, `H_265`, `MPEG2`, `VP9`, etc.

**Output Schema:**
```json
{
    "Id": "string"
}
```

Use the returned `Id` with `get-jobs-query-results` to retrieve matching jobs.

---

### 8.2 `get-jobs-query-results`

Retrieves the results of an advanced jobs query started with `start-jobs-query`. Returns up to 20 matching jobs.

**Synopsis:**
```bash
aws mediaconvert get-jobs-query-results \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The jobs query ID |

**Output Schema:**
```json
{
    "Jobs": [
        {
            "Arn": "string",
            "Id": "string",
            "Status": "SUBMITTED|PROGRESSING|COMPLETE|CANCELED|ERROR",
            "CurrentPhase": "PROBING|TRANSCODING|UPLOADING",
            "JobPercentComplete": "integer",
            "Queue": "string",
            "Role": "string",
            "Priority": "integer",
            "CreatedAt": "timestamp",
            "AccelerationSettings": {
                "Mode": "DISABLED|ENABLED|PREFERRED"
            },
            "AccelerationStatus": "NOT_APPLICABLE|IN_PROGRESS|ACCELERATED|NOT_ACCELERATED",
            "JobEngineVersionRequested": "string",
            "JobEngineVersionUsed": "string",
            "Settings": {
                "Inputs": [],
                "OutputGroups": []
            },
            "OutputGroupDetails": [
                {
                    "OutputDetails": [
                        {
                            "DurationInMs": "integer",
                            "VideoDetails": {
                                "HeightInPx": "integer",
                                "WidthInPx": "integer"
                            }
                        }
                    ]
                }
            ],
            "Messages": {
                "Info": ["string"],
                "Warning": ["string"]
            },
            "QueueTransitions": [],
            "RetryCount": "integer",
            "Timing": {
                "SubmitTime": "timestamp",
                "StartTime": "timestamp",
                "FinishTime": "timestamp"
            },
            "UserMetadata": {}
        }
    ]
}
```

---

### 8.3 `create-resource-share`

Shares a job's resources with AWS Support for troubleshooting via a support case.

**Synopsis:**
```bash
aws mediaconvert create-resource-share \
    --job-id <value> \
    --support-case-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | MediaConvert job ID or ARN to share |
| `--support-case-id` | **Yes** | string | -- | AWS Support case ID |

**Output:** None
