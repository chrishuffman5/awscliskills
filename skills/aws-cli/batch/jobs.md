# Jobs

### 1.1 `submit-job`

Submits a job to a job queue.

**Synopsis:**
```bash
aws batch submit-job \
    --job-name <value> \
    --job-queue <value> \
    --job-definition <value> \
    [--share-identifier <value>] \
    [--scheduling-priority-override <value>] \
    [--array-properties <value>] \
    [--depends-on <value>] \
    [--parameters <value>] \
    [--container-overrides <value>] \
    [--node-overrides <value>] \
    [--retry-strategy <value>] \
    [--propagate-tags | --no-propagate-tags] \
    [--timeout <value>] \
    [--tags <value>] \
    [--eks-properties-override <value>] \
    [--ecs-properties-override <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Name for the job |
| `--job-queue` | **Yes** | string | -- | Job queue name or ARN |
| `--job-definition` | **Yes** | string | -- | Job definition name or ARN (with optional revision) |
| `--share-identifier` | No | string | None | Fair share scheduling identifier |
| `--scheduling-priority-override` | No | integer | None | Override scheduling priority (0-9999) |
| `--array-properties` | No | structure | None | Array job properties. Shorthand: `size=integer` |
| `--depends-on` | No | list | None | Job dependencies. Shorthand: `jobId=string,type=N_TO_N\|SEQUENTIAL ...` |
| `--parameters` | No | map | None | Parameter substitution values |
| `--container-overrides` | No | structure | None | Override container properties (vcpus, memory, command, environment) |
| `--node-overrides` | No | structure | None | Override node properties |
| `--retry-strategy` | No | structure | None | Retry strategy. Shorthand: `attempts=integer,evaluateOnExit=[{...}]` |
| `--propagate-tags` | No | boolean | false | Propagate tags to ECS task |
| `--timeout` | No | structure | None | Job timeout. Shorthand: `attemptDurationSeconds=integer` |
| `--tags` | No | map | None | Tags (key-value pairs) |
| `--eks-properties-override` | No | structure | None | EKS properties override |
| `--ecs-properties-override` | No | structure | None | ECS properties override |

**Output Schema:**
```json
{
    "jobArn": "string",
    "jobName": "string",
    "jobId": "string"
}
```

---

### 1.2 `cancel-job`

Cancels a job in a SUBMITTED, PENDING, or RUNNABLE state.

**Synopsis:**
```bash
aws batch cancel-job \
    --job-id <value> \
    --reason <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | ID of the job to cancel |
| `--reason` | **Yes** | string | -- | Reason for cancellation |

**Output Schema:**
```json
{}
```

---

### 1.3 `terminate-job`

Terminates a running job.

**Synopsis:**
```bash
aws batch terminate-job \
    --job-id <value> \
    --reason <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | ID of the job to terminate |
| `--reason` | **Yes** | string | -- | Reason for termination |

**Output Schema:**
```json
{}
```

---

### 1.4 `describe-jobs`

Describes one or more jobs.

**Synopsis:**
```bash
aws batch describe-jobs \
    --jobs <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--jobs` | **Yes** | list(string) | -- | Job IDs (up to 100) |

**Output Schema:**
```json
{
    "jobs": [
        {
            "jobArn": "string",
            "jobName": "string",
            "jobId": "string",
            "jobQueue": "string",
            "status": "SUBMITTED|PENDING|RUNNABLE|STARTING|RUNNING|SUCCEEDED|FAILED",
            "shareIdentifier": "string",
            "schedulingPriority": "integer",
            "attempts": [
                {
                    "container": {
                        "containerInstanceArn": "string",
                        "taskArn": "string",
                        "exitCode": "integer",
                        "reason": "string",
                        "logStreamName": "string",
                        "networkInterfaces": []
                    },
                    "startedAt": "long",
                    "stoppedAt": "long",
                    "statusReason": "string"
                }
            ],
            "statusReason": "string",
            "createdAt": "long",
            "retryStrategy": {
                "attempts": "integer",
                "evaluateOnExit": []
            },
            "startedAt": "long",
            "stoppedAt": "long",
            "dependsOn": [],
            "jobDefinition": "string",
            "parameters": {},
            "container": {
                "image": "string",
                "vcpus": "integer",
                "memory": "integer",
                "command": ["string"],
                "jobRoleArn": "string",
                "executionRoleArn": "string",
                "environment": [],
                "mountPoints": [],
                "volumes": [],
                "exitCode": "integer",
                "reason": "string",
                "logStreamName": "string",
                "logConfiguration": {},
                "networkInterfaces": [],
                "resourceRequirements": []
            },
            "nodeDetails": {
                "nodeIndex": "integer",
                "isMainNode": true|false
            },
            "nodeProperties": {},
            "arrayProperties": {
                "statusSummary": {},
                "size": "integer",
                "index": "integer"
            },
            "timeout": {
                "attemptDurationSeconds": "integer"
            },
            "tags": {},
            "propagateTags": true|false,
            "platformCapabilities": ["EC2|FARGATE"],
            "eksProperties": {},
            "ecsProperties": {},
            "isCancelled": true|false,
            "isTerminated": true|false
        }
    ]
}
```

---

### 1.5 `list-jobs`

Lists jobs in a job queue or associated with an array/multi-node job. **Paginated operation.**

**Synopsis:**
```bash
aws batch list-jobs \
    [--job-queue <value>] \
    [--array-job-id <value>] \
    [--multi-node-job-id <value>] \
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
| `--job-queue` | No | string | None | Job queue name or ARN |
| `--array-job-id` | No | string | None | Array job ID to list children |
| `--multi-node-job-id` | No | string | None | Multi-node job ID to list children |
| `--job-status` | No | string | None | Filter by status: `SUBMITTED`, `PENDING`, `RUNNABLE`, `STARTING`, `RUNNING`, `SUCCEEDED`, `FAILED` |
| `--filters` | No | list | None | Filters. Shorthand: `name=string,values=string,string ...` |
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
            "createdAt": "long",
            "status": "SUBMITTED|PENDING|RUNNABLE|STARTING|RUNNING|SUCCEEDED|FAILED",
            "statusReason": "string",
            "startedAt": "long",
            "stoppedAt": "long",
            "container": {
                "exitCode": "integer",
                "reason": "string"
            },
            "arrayProperties": {
                "size": "integer",
                "index": "integer"
            },
            "nodeProperties": {
                "isMainNode": true|false,
                "numNodes": "integer",
                "nodeIndex": "integer"
            },
            "jobDefinition": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.6 `get-job-queue-snapshot`

Returns a snapshot of the current state of a job queue.

**Synopsis:**
```bash
aws batch get-job-queue-snapshot \
    --job-queue <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-queue` | **Yes** | string | -- | Job queue name or ARN |

**Output Schema:**
```json
{
    "frontOfQueue": {
        "jobs": [
            {
                "jobArn": "string",
                "earliestTimeAtPosition": "long"
            }
        ],
        "lastUpdatedAt": "long"
    }
}
```
