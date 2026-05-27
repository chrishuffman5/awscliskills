# Job Queues

### 3.1 `create-job-queue`

Creates a job queue.

**Synopsis:**
```bash
aws batch create-job-queue \
    --job-queue-name <value> \
    --priority <value> \
    --compute-environment-order <value> \
    [--state <value>] \
    [--scheduling-policy-arn <value>] \
    [--tags <value>] \
    [--job-state-time-limit-actions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-queue-name` | **Yes** | string | -- | Name for the job queue |
| `--priority` | **Yes** | integer | -- | Priority (higher = more priority, 0-100) |
| `--compute-environment-order` | **Yes** | list | -- | Compute environment order. Shorthand: `order=integer,computeEnvironment=string ...` |
| `--state` | No | string | `ENABLED` | State: `ENABLED`, `DISABLED` |
| `--scheduling-policy-arn` | No | string | None | Scheduling policy ARN |
| `--tags` | No | map | None | Tags |
| `--job-state-time-limit-actions` | No | list | None | Time limit actions for jobs in RUNNABLE state |

**Output Schema:**
```json
{
    "jobQueueName": "string",
    "jobQueueArn": "string"
}
```

---

### 3.2 `update-job-queue`

Updates a job queue.

**Synopsis:**
```bash
aws batch update-job-queue \
    --job-queue <value> \
    [--state <value>] \
    [--scheduling-policy-arn <value>] \
    [--priority <value>] \
    [--compute-environment-order <value>] \
    [--job-state-time-limit-actions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-queue` | **Yes** | string | -- | Job queue name or ARN |
| `--state` | No | string | None | State: `ENABLED`, `DISABLED` |
| `--scheduling-policy-arn` | No | string | None | Scheduling policy ARN (empty string to remove) |
| `--priority` | No | integer | None | New priority |
| `--compute-environment-order` | No | list | None | New compute environment order |
| `--job-state-time-limit-actions` | No | list | None | Time limit actions |

**Output Schema:**
```json
{
    "jobQueueName": "string",
    "jobQueueArn": "string"
}
```

---

### 3.3 `delete-job-queue`

Deletes a job queue. Queue must be in DISABLED state with no running/pending jobs.

**Synopsis:**
```bash
aws batch delete-job-queue \
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
{}
```

---

### 3.4 `describe-job-queues`

Describes job queues. **Paginated operation.**

**Synopsis:**
```bash
aws batch describe-job-queues \
    [--job-queues <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-queues` | No | list(string) | None | Job queue names or ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "jobQueues": [
        {
            "jobQueueName": "string",
            "jobQueueArn": "string",
            "state": "ENABLED|DISABLED",
            "status": "CREATING|UPDATING|DELETING|DELETED|VALID|INVALID",
            "statusReason": "string",
            "priority": "integer",
            "computeEnvironmentOrder": [
                {
                    "order": "integer",
                    "computeEnvironment": "string"
                }
            ],
            "schedulingPolicyArn": "string",
            "tags": {},
            "jobStateTimeLimitActions": []
        }
    ],
    "nextToken": "string"
}
```
