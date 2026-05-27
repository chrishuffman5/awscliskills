# Ingestions

### 9.1 `create-ingestion`

Creates a SPICE ingestion for a data set.

**Synopsis:**
```bash
aws quicksight create-ingestion \
    --aws-account-id <value> \
    --data-set-id <value> \
    --ingestion-id <value> \
    [--ingestion-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--ingestion-id` | **Yes** | string | -- | Ingestion ID |
| `--ingestion-type` | No | string | `FULL_REFRESH` | `FULL_REFRESH` or `INCREMENTAL_REFRESH` |

**Output Schema:**
```json
{
    "Arn": "string",
    "IngestionId": "string",
    "IngestionStatus": "INITIALIZED|QUEUED|RUNNING|FAILED|COMPLETED|CANCELLED",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 9.2 `describe-ingestion`

Describes an ingestion.

**Synopsis:**
```bash
aws quicksight describe-ingestion \
    --aws-account-id <value> \
    --data-set-id <value> \
    --ingestion-id <value>
```

**Output Schema:**
```json
{
    "Ingestion": {
        "Arn": "string",
        "IngestionId": "string",
        "IngestionStatus": "INITIALIZED|QUEUED|RUNNING|FAILED|COMPLETED|CANCELLED",
        "ErrorInfo": {
            "Type": "string",
            "Message": "string"
        },
        "RowInfo": {
            "RowsIngested": "long",
            "RowsDropped": "long",
            "TotalRowsInDataset": "long"
        },
        "QueueInfo": {
            "WaitingOnIngestion": "string",
            "QueuedIngestion": "string"
        },
        "CreatedTime": "timestamp",
        "IngestionTimeInSeconds": "long",
        "IngestionSizeInBytes": "long",
        "RequestSource": "MANUAL|SCHEDULED",
        "RequestType": "INITIAL_INGESTION|EDIT|FULL_REFRESH|INCREMENTAL_REFRESH"
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 9.3 `list-ingestions`

Lists ingestions for a data set. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-ingestions \
    --aws-account-id <value> \
    --data-set-id <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

### 9.4 `cancel-ingestion`

Cancels a running ingestion.

**Synopsis:**
```bash
aws quicksight cancel-ingestion \
    --aws-account-id <value> \
    --data-set-id <value> \
    --ingestion-id <value>
```

---

### 9.5 `create-refresh-schedule`

Creates a refresh schedule for a SPICE data set.

**Synopsis:**
```bash
aws quicksight create-refresh-schedule \
    --aws-account-id <value> \
    --data-set-id <value> \
    --schedule <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--schedule` | **Yes** | structure | -- | Refresh schedule configuration |

**Schedule Structure:**
```json
{
    "ScheduleId": "string",
    "ScheduleFrequency": {
        "Interval": "MINUTE15|MINUTE30|HOURLY|DAILY|WEEKLY|MONTHLY",
        "RefreshOnDay": {
            "DayOfWeek": "SUNDAY|MONDAY|...|SATURDAY",
            "DayOfMonth": "string"
        },
        "Timezone": "string",
        "TimeOfTheDay": "string"
    },
    "StartAfterDateTime": "timestamp",
    "RefreshType": "INCREMENTAL_REFRESH|FULL_REFRESH",
    "Arn": "string"
}
```

**Output Schema:**
```json
{
    "Status": "integer",
    "RequestId": "string",
    "ScheduleId": "string",
    "Arn": "string"
}
```

---

### 9.6 `describe-refresh-schedule` / `update-refresh-schedule` / `delete-refresh-schedule`

Manage refresh schedules.

**Synopsis:**
```bash
aws quicksight describe-refresh-schedule \
    --aws-account-id <value> --data-set-id <value> --schedule-id <value>

aws quicksight update-refresh-schedule \
    --aws-account-id <value> --data-set-id <value> --schedule <value>

aws quicksight delete-refresh-schedule \
    --aws-account-id <value> --data-set-id <value> --schedule-id <value>
```

---

### 9.7 `list-refresh-schedules`

Lists refresh schedules for a data set.

**Synopsis:**
```bash
aws quicksight list-refresh-schedules \
    --aws-account-id <value> \
    --data-set-id <value>
```
