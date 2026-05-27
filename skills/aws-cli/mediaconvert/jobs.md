# Jobs

### 1.1 `create-job`

Creates a new transcoding job. Requires an IAM role and job settings specifying inputs, outputs, and codec configuration.

**Synopsis:**
```bash
aws mediaconvert create-job \
    --role <value> \
    --settings <value> \
    [--acceleration-settings <value>] \
    [--billing-tags-source <value>] \
    [--client-request-token <value>] \
    [--hop-destinations <value>] \
    [--job-engine-version <value>] \
    [--job-template <value>] \
    [--priority <value>] \
    [--queue <value>] \
    [--simulate-reserved-queue <value>] \
    [--status-update-interval <value>] \
    [--tags <value>] \
    [--user-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role` | **Yes** | string | -- | IAM role ARN for job execution |
| `--settings` | **Yes** | structure | -- | JobSettings with inputs, output groups, and codec settings |
| `--acceleration-settings` | No | structure | None | Accelerated transcoding mode |
| `--billing-tags-source` | No | string | None | `QUEUE`, `PRESET`, `JOB_TEMPLATE`, `JOB` |
| `--client-request-token` | No | string | Auto | Idempotency token (up to 64 ASCII chars) |
| `--hop-destinations` | No | list | None | Queue hopping configuration |
| `--job-engine-version` | No | string | None | Engine version in YYYY-MM-DD format |
| `--job-template` | No | string | None | Job template name for predefined settings |
| `--priority` | No | integer | 0 | Relative priority (-50 to 50) |
| `--queue` | No | string | Default | Queue name or ARN |
| `--simulate-reserved-queue` | No | string | None | `DISABLED`, `ENABLED` |
| `--status-update-interval` | No | string | None | `SECONDS_10`, `SECONDS_12`, `SECONDS_15`, `SECONDS_20`, `SECONDS_30`, `SECONDS_60` |
| `--tags` | No | map | None | Key-value tag pairs |
| `--user-metadata` | No | map | None | Custom metadata key-value pairs |

**AccelerationSettings:**
```json
{
    "Mode": "DISABLED|ENABLED|PREFERRED"
}
```

**HopDestinations:**
```json
[
    {
        "Priority": -50,
        "Queue": "string",
        "WaitMinutes": 1
    }
]
```

**Output Schema:**
```json
{
    "Job": {
        "Arn": "string",
        "Id": "string",
        "Role": "string",
        "Queue": "string",
        "Status": "SUBMITTED|PROGRESSING|COMPLETE|CANCELED|ERROR",
        "CurrentPhase": "PROBING|TRANSCODING|UPLOADING",
        "JobPercentComplete": "integer",
        "Priority": "integer",
        "CreatedAt": "timestamp",
        "Settings": {
            "Inputs": [],
            "OutputGroups": []
        },
        "Timing": {
            "SubmitTime": "timestamp",
            "StartTime": "timestamp",
            "FinishTime": "timestamp"
        },
        "AccelerationSettings": {
            "Mode": "string"
        },
        "AccelerationStatus": "NOT_APPLICABLE|IN_PROGRESS|ACCELERATED|NOT_ACCELERATED",
        "BillingTagsSource": "string",
        "ClientRequestToken": "string",
        "HopDestinations": [],
        "JobEngineVersion": "string",
        "JobTemplate": "string",
        "Messages": {
            "Info": ["string"],
            "Warning": ["string"]
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
        "QueueTransitions": [],
        "RetryCount": "integer",
        "StatusUpdateInterval": "string",
        "Tags": {},
        "UserMetadata": {},
        "Warnings": [
            {
                "Code": "string",
                "Count": "integer",
                "Message": "string"
            }
        ]
    }
}
```

---

### 1.2 `get-job`

Retrieves the details of a transcoding job by its ID.

**Synopsis:**
```bash
aws mediaconvert get-job \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The job ID |

**Output Schema:**
```json
{
    "Job": {
        "Arn": "string",
        "Id": "string",
        "Role": "string",
        "Queue": "string",
        "Status": "SUBMITTED|PROGRESSING|COMPLETE|CANCELED|ERROR",
        "CurrentPhase": "PROBING|TRANSCODING|UPLOADING",
        "JobPercentComplete": "integer",
        "ErrorCode": "integer",
        "ErrorMessage": "string",
        "Priority": "integer",
        "CreatedAt": "timestamp",
        "Settings": {
            "Inputs": [],
            "OutputGroups": []
        },
        "Timing": {
            "SubmitTime": "timestamp",
            "StartTime": "timestamp",
            "FinishTime": "timestamp"
        },
        "AccelerationSettings": {
            "Mode": "string"
        },
        "AccelerationStatus": "string",
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
        "Tags": {},
        "UserMetadata": {}
    }
}
```

---

### 1.3 `cancel-job`

Cancels a transcoding job. Jobs already being processed cannot be cancelled.

**Synopsis:**
```bash
aws mediaconvert cancel-job \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The job ID to cancel |

**Output:** None

---

### 1.4 `list-jobs`

Lists transcoding jobs. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconvert list-jobs \
    [--order <value>] \
    [--queue <value>] \
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
| `--order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--queue` | No | string | None | Filter by queue name |
| `--status` | No | string | None | `SUBMITTED`, `PROGRESSING`, `COMPLETE`, `CANCELED`, `ERROR` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
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
            "JobTemplate": "string",
            "AccelerationSettings": {
                "Mode": "string"
            },
            "AccelerationStatus": "string",
            "JobEngineVersionRequested": "string",
            "JobEngineVersionUsed": "string",
            "Settings": {},
            "OutputGroupDetails": [],
            "Messages": {},
            "QueueTransitions": [],
            "RetryCount": "integer",
            "Timing": {
                "SubmitTime": "timestamp",
                "StartTime": "timestamp",
                "FinishTime": "timestamp"
            }
        }
    ]
}
```

---

### 1.5 `search-jobs`

Searches for jobs by input file, queue, or status. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconvert search-jobs \
    [--input-file <value>] \
    [--order <value>] \
    [--queue <value>] \
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
| `--input-file` | No | string | None | Input file URL or partial name (max 300 chars) |
| `--order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--queue` | No | string | None | Queue name or ARN |
| `--status` | No | string | None | `SUBMITTED`, `PROGRESSING`, `COMPLETE`, `CANCELED`, `ERROR` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Jobs": [
        {
            "Arn": "string",
            "Id": "string",
            "Status": "SUBMITTED|PROGRESSING|COMPLETE|CANCELED|ERROR",
            "CurrentPhase": "string",
            "JobPercentComplete": "integer",
            "Queue": "string",
            "Role": "string",
            "Priority": "integer",
            "CreatedAt": "timestamp",
            "AccelerationSettings": {},
            "AccelerationStatus": "string",
            "JobEngineVersionRequested": "string",
            "JobEngineVersionUsed": "string",
            "Settings": {},
            "OutputGroupDetails": [],
            "Messages": {},
            "QueueTransitions": [],
            "RetryCount": "integer"
        }
    ]
}
```
