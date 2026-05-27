# EMR Containers — Job Runs (`aws emr-containers`)

### 12.1 `start-job-run`

Starts a job run on a virtual cluster.

**Synopsis:**
```bash
aws emr-containers start-job-run \
    --virtual-cluster-id <value> \
    --execution-role-arn <value> \
    --release-label <value> \
    --job-driver <value> \
    [--name <value>] \
    [--client-token <value>] \
    [--configuration-overrides <value>] \
    [--tags <value>] \
    [--job-template-id <value>] \
    [--job-template-parameters <value>] \
    [--retry-policy-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-cluster-id` | **Yes** | string | -- | Virtual cluster ID |
| `--execution-role-arn` | **Yes** | string | -- | IAM execution role ARN |
| `--release-label` | **Yes** | string | -- | EMR release label (e.g., `emr-7.0.0-latest`) |
| `--job-driver` | **Yes** | structure | -- | Job driver configuration (see below) |
| `--name` | No | string | -- | Job run name |
| `--client-token` | No | string | -- | Idempotency token |
| `--configuration-overrides` | No | structure | -- | Configuration and monitoring overrides |
| `--tags` | No | map | -- | Tags |
| `--job-template-id` | No | string | -- | Job template ID |
| `--job-template-parameters` | No | map | -- | Template parameters |
| `--retry-policy-configuration` | No | structure | -- | Retry policy. Shorthand: `maxAttempts=integer` |

**Job Driver (Spark Submit):**
```json
{
    "sparkSubmitJobDriver": {
        "entryPoint": "s3://bucket/script.py",
        "entryPointArguments": ["arg1", "arg2"],
        "sparkSubmitParameters": "--conf spark.executor.instances=2 --conf spark.executor.memory=2G"
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
                "spark.dynamicAllocation.enabled": "false"
            }
        }
    ],
    "monitoringConfiguration": {
        "cloudWatchMonitoringConfiguration": {
            "logGroupName": "/emr-containers/jobs",
            "logStreamNamePrefix": "my-job"
        },
        "s3MonitoringConfiguration": {
            "logUri": "s3://bucket/logs/"
        }
    }
}
```

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "virtualClusterId": "string"
}
```

---

### 12.2 `cancel-job-run`

Cancels a running job.

**Synopsis:**
```bash
aws emr-containers cancel-job-run \
    --id <value> \
    --virtual-cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Job run ID to cancel |
| `--virtual-cluster-id` | **Yes** | string | -- | Virtual cluster ID |

**Output Schema:**
```json
{
    "id": "string",
    "virtualClusterId": "string"
}
```

---

### 12.3 `describe-job-run`

Describes a job run.

**Synopsis:**
```bash
aws emr-containers describe-job-run \
    --id <value> \
    --virtual-cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Job run ID |
| `--virtual-cluster-id` | **Yes** | string | -- | Virtual cluster ID |

**Output Schema:**
```json
{
    "jobRun": {
        "id": "string",
        "name": "string",
        "virtualClusterId": "string",
        "arn": "string",
        "state": "PENDING|SUBMITTED|RUNNING|FAILED|CANCELLED|CANCEL_PENDING|COMPLETED",
        "clientToken": "string",
        "executionRoleArn": "string",
        "releaseLabel": "string",
        "configurationOverrides": {},
        "jobDriver": {},
        "createdAt": "timestamp",
        "createdBy": "string",
        "finishedAt": "timestamp",
        "stateDetails": "string",
        "failureReason": "INTERNAL_ERROR|USER_ERROR|VALIDATION_ERROR|CLUSTER_UNAVAILABLE",
        "tags": {},
        "retryPolicyConfiguration": {},
        "retryPolicyExecution": {
            "currentAttemptCount": "integer"
        }
    }
}
```

---

### 12.4 `list-job-runs`

Lists job runs in a virtual cluster. **Paginated operation.**

**Synopsis:**
```bash
aws emr-containers list-job-runs \
    --virtual-cluster-id <value> \
    [--created-before <value>] \
    [--created-after <value>] \
    [--name <value>] \
    [--states <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-cluster-id` | **Yes** | string | -- | Virtual cluster ID |
| `--created-before` | No | timestamp | -- | Filter before this time |
| `--created-after` | No | timestamp | -- | Filter after this time |
| `--name` | No | string | -- | Filter by name |
| `--states` | No | list(string) | -- | Filter: `PENDING`, `SUBMITTED`, `RUNNING`, `FAILED`, `CANCELLED`, `CANCEL_PENDING`, `COMPLETED` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "jobRuns": [
        {
            "id": "string",
            "name": "string",
            "virtualClusterId": "string",
            "arn": "string",
            "state": "string",
            "createdAt": "timestamp",
            "finishedAt": "timestamp",
            "stateDetails": "string",
            "failureReason": "string",
            "releaseLabel": "string",
            "executionRoleArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 12.5 `get-managed-endpoint-session-credentials`

Gets session credentials for a managed endpoint.

**Synopsis:**
```bash
aws emr-containers get-managed-endpoint-session-credentials \
    --endpoint-identifier <value> \
    --virtual-cluster-identifier <value> \
    --execution-role-arn <value> \
    --credential-type <value> \
    [--duration-in-seconds <value>] \
    [--log-context <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-identifier` | **Yes** | string | -- | Managed endpoint ID |
| `--virtual-cluster-identifier` | **Yes** | string | -- | Virtual cluster ID |
| `--execution-role-arn` | **Yes** | string | -- | Execution role ARN |
| `--credential-type` | **Yes** | string | -- | Credential type: `TOKEN` |
| `--duration-in-seconds` | No | integer | -- | Token duration |
| `--log-context` | No | string | -- | Log context |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "id": "string",
    "credentials": {
        "token": "string"
    },
    "expiresAt": "timestamp"
}
```
