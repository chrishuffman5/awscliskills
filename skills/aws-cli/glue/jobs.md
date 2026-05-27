# Jobs

### 1.1 `create-job`

Creates a new ETL job definition.

**Synopsis:**
```bash
aws glue create-job \
    --name <value> \
    --role <value> \
    --command <value> \
    [--description <value>] \
    [--log-uri <value>] \
    [--execution-property <value>] \
    [--default-arguments <value>] \
    [--non-overridable-arguments <value>] \
    [--connections <value>] \
    [--max-retries <value>] \
    [--allocated-capacity <value>] \
    [--timeout <value>] \
    [--max-capacity <value>] \
    [--security-configuration <value>] \
    [--tags <value>] \
    [--notification-property <value>] \
    [--glue-version <value>] \
    [--number-of-workers <value>] \
    [--worker-type <value>] \
    [--code-gen-configuration-nodes <value>] \
    [--execution-class <value>] \
    [--source-control-details <value>] \
    [--maintenance-window <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Job name (unique) |
| `--role` | **Yes** | string | -- | IAM role ARN |
| `--command` | **Yes** | structure | -- | Job command. Shorthand: `Name=string,ScriptLocation=string,PythonVersion=string,Runtime=string` |
| `--description` | No | string | -- | Description |
| `--log-uri` | No | string | -- | S3 log location |
| `--execution-property` | No | structure | -- | Max concurrent runs. Shorthand: `MaxConcurrentRuns=integer` |
| `--default-arguments` | No | map | -- | Default arguments as JSON |
| `--non-overridable-arguments` | No | map | -- | Arguments that cannot be overridden at run time |
| `--connections` | No | structure | -- | Connections. Shorthand: `Connections=string,string` |
| `--max-retries` | No | integer | 0 | Max retries on failure |
| `--timeout` | No | integer | 2880 | Timeout in minutes |
| `--max-capacity` | No | double | -- | Max DPUs (mutually exclusive with NumberOfWorkers/WorkerType) |
| `--security-configuration` | No | string | -- | Security configuration name |
| `--tags` | No | map | -- | Tags as JSON |
| `--notification-property` | No | structure | -- | Notification config. Shorthand: `NotifyDelayAfter=integer` |
| `--glue-version` | No | string | -- | Glue version: `2.0`, `3.0`, `4.0` |
| `--number-of-workers` | No | integer | -- | Number of workers |
| `--worker-type` | No | string | -- | `Standard`, `G.1X`, `G.2X`, `G.025X`, `G.4X`, `G.8X`, `Z.2X` |
| `--execution-class` | No | string | -- | `FLEX` or `STANDARD` |
| `--maintenance-window` | No | string | -- | Maintenance window (cron expression) |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 1.2 `delete-job`

Deletes a job definition and all associated runs.

**Synopsis:**
```bash
aws glue delete-job \
    --job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name to delete |

**Output Schema:**
```json
{
    "JobName": "string"
}
```

---

### 1.3 `get-job`

Retrieves a job definition.

**Synopsis:**
```bash
aws glue get-job \
    --job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name |

**Output Schema:**
```json
{
    "Job": {
        "Name": "string",
        "Description": "string",
        "LogUri": "string",
        "Role": "string",
        "CreatedOn": "timestamp",
        "LastModifiedOn": "timestamp",
        "ExecutionProperty": {
            "MaxConcurrentRuns": "integer"
        },
        "Command": {
            "Name": "string",
            "ScriptLocation": "string",
            "PythonVersion": "string",
            "Runtime": "string"
        },
        "DefaultArguments": {},
        "NonOverridableArguments": {},
        "Connections": {
            "Connections": ["string"]
        },
        "MaxRetries": "integer",
        "AllocatedCapacity": "integer",
        "Timeout": "integer",
        "MaxCapacity": "double",
        "WorkerType": "Standard|G.1X|G.2X|G.025X|G.4X|G.8X|Z.2X",
        "NumberOfWorkers": "integer",
        "SecurityConfiguration": "string",
        "NotificationProperty": {
            "NotifyDelayAfter": "integer"
        },
        "GlueVersion": "string",
        "ExecutionClass": "FLEX|STANDARD",
        "MaintenanceWindow": "string"
    }
}
```

---

### 1.4 `get-jobs`

Retrieves all job definitions. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-jobs \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Jobs": [
        {
            "Name": "string",
            "Role": "string",
            "Command": {},
            "GlueVersion": "string",
            "WorkerType": "string",
            "NumberOfWorkers": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-job`

Updates an existing job definition.

**Synopsis:**
```bash
aws glue update-job \
    --job-name <value> \
    --job-update <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name |
| `--job-update` | **Yes** | structure | -- | Updated job definition (JSON) |

**Output Schema:**
```json
{
    "JobName": "string"
}
```

---

### 1.6 `batch-get-jobs`

Returns detailed information for a list of jobs.

**Synopsis:**
```bash
aws glue batch-get-jobs \
    --job-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-names` | **Yes** | list(string) | -- | List of job names |

**Output Schema:**
```json
{
    "Jobs": ["<Job structure>"],
    "JobsNotFound": ["string"]
}
```

---

### 1.7 `start-job-run`

Starts a job run using a job definition.

**Synopsis:**
```bash
aws glue start-job-run \
    --job-name <value> \
    [--job-run-id <value>] \
    [--arguments <value>] \
    [--allocated-capacity <value>] \
    [--timeout <value>] \
    [--max-capacity <value>] \
    [--security-configuration <value>] \
    [--notification-property <value>] \
    [--worker-type <value>] \
    [--number-of-workers <value>] \
    [--execution-class <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name |
| `--job-run-id` | No | string | -- | Specific run ID (for retries) |
| `--arguments` | No | map | -- | Override arguments as JSON |
| `--timeout` | No | integer | -- | Override timeout in minutes |
| `--max-capacity` | No | double | -- | Override max DPUs |
| `--security-configuration` | No | string | -- | Override security configuration |
| `--notification-property` | No | structure | -- | Override notification config |
| `--worker-type` | No | string | -- | Override worker type |
| `--number-of-workers` | No | integer | -- | Override number of workers |
| `--execution-class` | No | string | -- | Override execution class |

**Output Schema:**
```json
{
    "JobRunId": "string"
}
```

---

### 1.8 `batch-stop-job-run`

Stops one or more job runs for a job.

**Synopsis:**
```bash
aws glue batch-stop-job-run \
    --job-name <value> \
    --job-run-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name |
| `--job-run-ids` | **Yes** | list(string) | -- | Run IDs to stop |

**Output Schema:**
```json
{
    "SuccessfulSubmissions": [
        {
            "JobName": "string",
            "JobRunId": "string"
        }
    ],
    "Errors": [
        {
            "JobName": "string",
            "JobRunId": "string",
            "ErrorDetail": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 1.9 `get-job-run`

Retrieves metadata for a specific job run.

**Synopsis:**
```bash
aws glue get-job-run \
    --job-name <value> \
    --run-id <value> \
    [--predecessors-included | --no-predecessors-included] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name |
| `--run-id` | **Yes** | string | -- | Job run ID |
| `--predecessors-included` | No | boolean | false | Include predecessor runs |

**Output Schema:**
```json
{
    "JobRun": {
        "Id": "string",
        "Attempt": "integer",
        "PreviousRunId": "string",
        "TriggerName": "string",
        "JobName": "string",
        "JobMode": "SCRIPT|VISUAL|NOTEBOOK",
        "StartedOn": "timestamp",
        "LastModifiedOn": "timestamp",
        "CompletedOn": "timestamp",
        "JobRunState": "STARTING|RUNNING|STOPPING|STOPPED|SUCCEEDED|FAILED|TIMEOUT|ERROR|WAITING|EXPIRED",
        "Arguments": {},
        "ErrorMessage": "string",
        "PredecessorRuns": [
            {
                "JobName": "string",
                "RunId": "string"
            }
        ],
        "AllocatedCapacity": "integer",
        "ExecutionTime": "integer",
        "Timeout": "integer",
        "MaxCapacity": "double",
        "WorkerType": "string",
        "NumberOfWorkers": "integer",
        "SecurityConfiguration": "string",
        "LogGroupName": "string",
        "NotificationProperty": {},
        "GlueVersion": "string",
        "DPUSeconds": "double",
        "ExecutionClass": "FLEX|STANDARD",
        "MaintenanceWindow": "string"
    }
}
```

---

### 1.10 `get-job-runs`

Retrieves metadata for all runs of a job. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-job-runs \
    --job-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "JobRuns": ["<JobRun structure>"],
    "NextToken": "string"
}
```

---

### 1.11 `get-job-bookmark`

Returns information on a job bookmark entry.

**Synopsis:**
```bash
aws glue get-job-bookmark \
    --job-name <value> \
    [--run-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name |
| `--run-id` | No | string | -- | Specific run ID |

**Output Schema:**
```json
{
    "JobBookmarkEntry": {
        "JobName": "string",
        "Version": "integer",
        "Run": "integer",
        "Attempt": "integer",
        "PreviousRunId": "string",
        "RunId": "string",
        "JobBookmark": "string"
    }
}
```

---

### 1.12 `reset-job-bookmark`

Resets a job bookmark so the job processes data from the beginning.

**Synopsis:**
```bash
aws glue reset-job-bookmark \
    --job-name <value> \
    [--run-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name |
| `--run-id` | No | string | -- | Specific run ID |

**Output Schema:**
```json
{
    "JobBookmarkEntry": {
        "JobName": "string",
        "Version": "integer",
        "Run": "integer",
        "Attempt": "integer",
        "PreviousRunId": "string",
        "RunId": "string",
        "JobBookmark": "string"
    }
}
```
