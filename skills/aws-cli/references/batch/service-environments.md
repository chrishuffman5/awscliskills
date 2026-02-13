# Service Environments

### 7.1 `create-service-environment`

Creates a Batch service environment for long-running workloads.

**Synopsis:**
```bash
aws batch create-service-environment \
    --service-environment-name <value> \
    --compute-environment <value> \
    [--service-role <value>] \
    [--instance-role <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-environment-name` | **Yes** | string | -- | Name for the service environment |
| `--compute-environment` | **Yes** | string | -- | Compute environment name or ARN |
| `--service-role` | No | string | None | Service role ARN |
| `--instance-role` | No | string | None | Instance role ARN |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "serviceEnvironmentName": "string",
    "serviceEnvironmentArn": "string"
}
```

---

### 7.2 `update-service-environment`

Updates a service environment.

**Synopsis:**
```bash
aws batch update-service-environment \
    --service-environment <value> \
    [--compute-environment <value>] \
    [--service-role <value>] \
    [--instance-role <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-environment` | **Yes** | string | -- | Service environment name or ARN |
| `--compute-environment` | No | string | None | New compute environment |
| `--service-role` | No | string | None | New service role ARN |
| `--instance-role` | No | string | None | New instance role ARN |

**Output Schema:**
```json
{
    "serviceEnvironmentName": "string",
    "serviceEnvironmentArn": "string"
}
```

---

### 7.3 `delete-service-environment`

Deletes a service environment.

**Synopsis:**
```bash
aws batch delete-service-environment \
    --service-environment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-environment` | **Yes** | string | -- | Service environment name or ARN |

**Output Schema:**
```json
{}
```

---

### 7.4 `describe-service-environments`

Describes service environments. **Paginated operation.**

**Synopsis:**
```bash
aws batch describe-service-environments \
    [--service-environments <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-environments` | No | list(string) | None | Service environment names or ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "serviceEnvironments": [
        {
            "serviceEnvironmentName": "string",
            "serviceEnvironmentArn": "string",
            "computeEnvironment": "string",
            "state": "ACTIVE|DELETING|CREATING|UPDATING",
            "status": "string",
            "statusReason": "string",
            "serviceRole": "string",
            "instanceRole": "string",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 7.5 `describe-service-job`

Describes a service job.

**Synopsis:**
```bash
aws batch describe-service-job \
    --service-environment <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-environment` | **Yes** | string | -- | Service environment name or ARN |
| `--job-id` | **Yes** | string | -- | Job ID |

**Output Schema:**
```json
{
    "job": {
        "jobId": "string",
        "jobName": "string",
        "jobArn": "string",
        "serviceEnvironment": "string",
        "status": "SUBMITTED|PENDING|RUNNABLE|STARTING|RUNNING|SUCCEEDED|FAILED",
        "statusReason": "string",
        "createdAt": "long",
        "startedAt": "long",
        "stoppedAt": "long",
        "container": {},
        "tags": {}
    }
}
```

---

### 7.6 `submit-service-job`

Submits a job to a service environment.

**Synopsis:**
```bash
aws batch submit-service-job \
    --job-name <value> \
    --service-environment <value> \
    --job-definition <value> \
    [--container-overrides <value>] \
    [--parameters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Name for the job |
| `--service-environment` | **Yes** | string | -- | Service environment name or ARN |
| `--job-definition` | **Yes** | string | -- | Job definition name or ARN |
| `--container-overrides` | No | structure | None | Container overrides |
| `--parameters` | No | map | None | Parameter substitution values |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "jobArn": "string",
    "jobName": "string",
    "jobId": "string"
}
```

---

### 7.7 `list-service-jobs`

Lists jobs in a service environment. **Paginated operation.**

**Synopsis:**
```bash
aws batch list-service-jobs \
    --service-environment <value> \
    [--job-status <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-environment` | **Yes** | string | -- | Service environment name or ARN |
| `--job-status` | No | string | None | Filter by status |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "jobSummaryList": [
        {
            "jobArn": "string",
            "jobId": "string",
            "jobName": "string",
            "status": "SUBMITTED|PENDING|RUNNABLE|STARTING|RUNNING|SUCCEEDED|FAILED",
            "statusReason": "string",
            "createdAt": "long",
            "startedAt": "long",
            "stoppedAt": "long"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.8 `terminate-service-job`

Terminates a running service job.

**Synopsis:**
```bash
aws batch terminate-service-job \
    --service-environment <value> \
    --job-id <value> \
    --reason <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-environment` | **Yes** | string | -- | Service environment name or ARN |
| `--job-id` | **Yes** | string | -- | Job ID to terminate |
| `--reason` | **Yes** | string | -- | Reason for termination |

**Output Schema:**
```json
{}
```
