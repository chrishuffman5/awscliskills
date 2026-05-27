# Serverless — Job Runs (`aws emr-serverless`)

### 15.1 `start-job-run`

Starts a job run on an EMR Serverless application.

**Synopsis:**
```bash
aws emr-serverless start-job-run \
    --application-id <value> \
    --execution-role-arn <value> \
    [--name <value>] \
    [--client-token <value>] \
    [--job-driver <value>] \
    [--configuration-overrides <value>] \
    [--tags <value>] \
    [--execution-timeout-minutes <value>] \
    [--mode <value>] \
    [--retry-policy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--execution-role-arn` | **Yes** | string | -- | IAM execution role ARN |
| `--name` | No | string | -- | Job run name |
| `--client-token` | No | string | -- | Idempotency token |
| `--job-driver` | No | structure | -- | Job driver (see below) |
| `--configuration-overrides` | No | structure | -- | Configuration and monitoring overrides |
| `--tags` | No | map | -- | Tags |
| `--execution-timeout-minutes` | No | long | -- | Timeout in minutes |
| `--mode` | No | string | `BATCH` | `BATCH` or `STREAMING` |
| `--retry-policy` | No | structure | -- | Retry policy. Shorthand: `maxAttempts=integer,maxFailedAttemptsPerHour=integer` |

**Spark Job Driver:**
```json
{
    "sparkSubmit": {
        "entryPoint": "s3://bucket/script.py",
        "entryPointArguments": ["arg1", "arg2"],
        "sparkSubmitParameters": "--conf spark.executor.instances=10"
    }
}
```

**Hive Job Driver:**
```json
{
    "hive": {
        "query": "s3://bucket/query.sql",
        "initQueryFile": "s3://bucket/init.sql",
        "parameters": "--hiveconf hive.exec.parallel=true"
    }
}
```

**Configuration Overrides:**
```json
{
    "applicationConfiguration": [
        {
            "classification": "spark-defaults",
            "properties": {
                "spark.dynamicAllocation.enabled": "true"
            }
        }
    ],
    "monitoringConfiguration": {
        "s3MonitoringConfiguration": {
            "logUri": "s3://bucket/logs/"
        },
        "managedPersistenceMonitoringConfiguration": {
            "enabled": true
        },
        "cloudWatchLoggingConfiguration": {
            "enabled": true,
            "logGroupName": "/emr-serverless/jobs",
            "logStreamNamePrefix": "my-job"
        }
    }
}
```

**Output Schema:**
```json
{
    "applicationId": "string",
    "jobRunId": "string",
    "arn": "string"
}
```

---

### 15.2 `cancel-job-run`

Cancels a running job.

**Synopsis:**
```bash
aws emr-serverless cancel-job-run \
    --application-id <value> \
    --job-run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--job-run-id` | **Yes** | string | -- | Job run ID to cancel |

**Output Schema:**
```json
{
    "applicationId": "string",
    "jobRunId": "string"
}
```

---

### 15.3 `get-job-run`

Gets details about a job run.

**Synopsis:**
```bash
aws emr-serverless get-job-run \
    --application-id <value> \
    --job-run-id <value> \
    [--attempt <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--job-run-id` | **Yes** | string | -- | Job run ID |
| `--attempt` | No | integer | -- | Specific attempt number |

**Output Schema:**
```json
{
    "jobRun": {
        "applicationId": "string",
        "jobRunId": "string",
        "name": "string",
        "arn": "string",
        "createdBy": "string",
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "executionRole": "string",
        "state": "SUBMITTED|PENDING|SCHEDULED|RUNNING|SUCCESS|FAILED|CANCELLING|CANCELLED",
        "stateDetails": "string",
        "releaseLabel": "string",
        "configurationOverrides": {},
        "jobDriver": {},
        "tags": {},
        "totalResourceUtilization": {
            "vCPUHour": "double",
            "memoryGBHour": "double",
            "storageGBHour": "double"
        },
        "networkConfiguration": {},
        "totalExecutionDurationSeconds": "integer",
        "executionTimeoutMinutes": "long",
        "billedResourceUtilization": {
            "vCPUHour": "double",
            "memoryGBHour": "double",
            "storageGBHour": "double"
        },
        "mode": "BATCH|STREAMING",
        "retryPolicy": {},
        "attempt": "integer",
        "attemptCreatedAt": "timestamp",
        "attemptUpdatedAt": "timestamp",
        "queuedDurationMilliseconds": "long"
    }
}
```

---

### 15.4 `list-job-runs`

Lists job runs for an application. **Paginated operation.**

**Synopsis:**
```bash
aws emr-serverless list-job-runs \
    --application-id <value> \
    [--created-at-after <value>] \
    [--created-at-before <value>] \
    [--states <value>] \
    [--mode <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--created-at-after` | No | timestamp | -- | Filter after this time |
| `--created-at-before` | No | timestamp | -- | Filter before this time |
| `--states` | No | list(string) | -- | Filter: `SUBMITTED`, `PENDING`, `SCHEDULED`, `RUNNING`, `SUCCESS`, `FAILED`, `CANCELLING`, `CANCELLED` |
| `--mode` | No | string | -- | Filter: `BATCH` or `STREAMING` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "jobRuns": [
        {
            "applicationId": "string",
            "id": "string",
            "name": "string",
            "arn": "string",
            "createdBy": "string",
            "createdAt": "timestamp",
            "updatedAt": "timestamp",
            "executionRole": "string",
            "state": "string",
            "stateDetails": "string",
            "releaseLabel": "string",
            "type": "string",
            "mode": "string",
            "attempt": "integer",
            "attemptCreatedAt": "timestamp",
            "attemptUpdatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 15.5 `get-dashboard-for-job-run`

Gets the URL for the Spark or Tez dashboard for a job run.

**Synopsis:**
```bash
aws emr-serverless get-dashboard-for-job-run \
    --application-id <value> \
    --job-run-id <value> \
    [--attempt <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--job-run-id` | **Yes** | string | -- | Job run ID |
| `--attempt` | No | integer | -- | Specific attempt number |

**Output Schema:**
```json
{
    "url": "string"
}
```

---

### 15.6 `tag-resource`

Adds tags to an EMR Serverless resource.

**Synopsis:**
```bash
aws emr-serverless tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs |

No output on success.

---

### 15.7 `untag-resource`

Removes tags from an EMR Serverless resource.

**Synopsis:**
```bash
aws emr-serverless untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

No output on success.

---

### 15.8 `list-tags-for-resource`

Lists tags for an EMR Serverless resource.

**Synopsis:**
```bash
aws emr-serverless list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "tags": {"string": "string"}
}
```
