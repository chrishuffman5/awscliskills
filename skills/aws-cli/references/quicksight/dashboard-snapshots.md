# Dashboard Snapshots

### 3.1 `start-dashboard-snapshot-job`

Starts an asynchronous job to generate a dashboard snapshot (PDF, CSV, or Excel).

**Synopsis:**
```bash
aws quicksight start-dashboard-snapshot-job \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --snapshot-job-id <value> \
    --user-configuration <value> \
    --snapshot-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--snapshot-job-id` | **Yes** | string | -- | Unique job ID |
| `--user-configuration` | **Yes** | structure | -- | User context for the snapshot |
| `--snapshot-configuration` | **Yes** | structure | -- | Output format and destination |

**Snapshot Configuration:**
```json
{
    "FileGroups": [
        {
            "Files": [
                {
                    "SheetSelections": [
                        {
                            "SheetId": "string",
                            "SelectionScope": "ALL_VISUALS|SELECTED_VISUALS",
                            "VisualIds": ["string"]
                        }
                    ],
                    "FormatType": "CSV|EXCEL|PDF"
                }
            ]
        }
    ],
    "DestinationConfiguration": {
        "S3Destinations": [
            {
                "BucketConfiguration": {
                    "BucketName": "string",
                    "BucketPrefix": "string",
                    "BucketRegion": "string"
                }
            }
        ]
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "SnapshotJobId": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 3.2 `describe-dashboard-snapshot-job`

Describes the status of a dashboard snapshot job.

**Synopsis:**
```bash
aws quicksight describe-dashboard-snapshot-job \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --snapshot-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--snapshot-job-id` | **Yes** | string | -- | Snapshot job ID |

**Output Schema:**
```json
{
    "AwsAccountId": "string",
    "DashboardId": "string",
    "SnapshotJobId": "string",
    "UserConfiguration": {},
    "SnapshotConfiguration": {},
    "Arn": "string",
    "JobStatus": "QUEUED|RUNNING|COMPLETED|FAILED",
    "CreatedTime": "timestamp",
    "LastUpdatedTime": "timestamp",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 3.3 `describe-dashboard-snapshot-job-result`

Returns the results and output location of a completed snapshot job.

**Synopsis:**
```bash
aws quicksight describe-dashboard-snapshot-job-result \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --snapshot-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `describe-dashboard-snapshot-job`.

**Output Schema:**
```json
{
    "Arn": "string",
    "JobStatus": "QUEUED|RUNNING|COMPLETED|FAILED",
    "CreatedTime": "timestamp",
    "LastUpdatedTime": "timestamp",
    "Result": {
        "AnonymousUsers": [
            {
                "RowLevelPermissionResults": [],
                "RowLevelPermissionTagKeys": []
            }
        ]
    },
    "ErrorInfo": {
        "ErrorMessage": "string",
        "ErrorType": "string"
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 3.4 `start-dashboard-snapshot-job-schedule`

Starts a recurring snapshot job schedule for a dashboard.

**Synopsis:**
```bash
aws quicksight start-dashboard-snapshot-job-schedule \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --schedule-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--schedule-id` | **Yes** | string | -- | Schedule ID |

**Output Schema:**
```json
{
    "RequestId": "string",
    "Status": "integer"
}
```
