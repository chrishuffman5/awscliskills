# Capacity

### 4.1 `start-capacity-task`

Starts a capacity task on the specified Outpost. A capacity task configures instance capacity on the Outpost hardware.

**Synopsis:**
```bash
aws outposts start-capacity-task \
    --outpost-identifier <value> \
    --instance-pools <value> \
    [--order-id <value>] \
    [--dry-run | --no-dry-run] \
    [--instances-to-exclude <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-identifier` | **Yes** | string | -- | ID or ARN of the Outpost |
| `--instance-pools` | **Yes** | list | -- | Instance pools to configure. Shorthand: `InstanceType=string,Count=integer ...` |
| `--order-id` | No | string | -- | ID of the order associated with this capacity task |
| `--dry-run` | No | boolean | false | Perform a dry run without making changes |
| `--no-dry-run` | No | boolean | -- | Explicitly disable dry run |
| `--instances-to-exclude` | No | structure | None | Instances to exclude from the capacity task |

**Instance Pool Structure:**
```json
{
    "InstanceType": "string",
    "Count": "integer"
}
```

**Instances to Exclude Structure:**
```json
{
    "Instances": ["string"],
    "AccountIds": ["string"],
    "Services": ["AWS"|"EC2"|"ELASTICACHE"|"ELB"|"RDS"|"ROUTE53"]
}
```

**Output Schema:**
```json
{
    "CapacityTaskId": "string",
    "OutpostId": "string",
    "OrderId": "string",
    "RequestedInstancePools": [
        {
            "InstanceType": "string",
            "Count": "integer"
        }
    ],
    "InstancesToExclude": {
        "Instances": ["string"],
        "AccountIds": ["string"],
        "Services": ["string"]
    },
    "DryRun": "boolean",
    "CapacityTaskStatus": "REQUESTED|IN_PROGRESS|COMPLETED|FAILED|CANCELLED|WAITING_FOR_EVACUATION",
    "Failed": {
        "Reason": "string"
    },
    "CreationDate": "timestamp",
    "CompletionDate": "timestamp",
    "LastModifiedDate": "timestamp"
}
```

---

### 4.2 `get-capacity-task`

Gets details of a capacity task.

**Synopsis:**
```bash
aws outposts get-capacity-task \
    --capacity-task-id <value> \
    --outpost-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--capacity-task-id` | **Yes** | string | -- | ID of the capacity task |
| `--outpost-identifier` | **Yes** | string | -- | ID or ARN of the Outpost |

**Output Schema:**
```json
{
    "CapacityTaskId": "string",
    "OutpostId": "string",
    "OrderId": "string",
    "RequestedInstancePools": [
        {
            "InstanceType": "string",
            "Count": "integer"
        }
    ],
    "InstancesToExclude": {
        "Instances": ["string"],
        "AccountIds": ["string"],
        "Services": ["string"]
    },
    "DryRun": "boolean",
    "CapacityTaskStatus": "REQUESTED|IN_PROGRESS|COMPLETED|FAILED|CANCELLED|WAITING_FOR_EVACUATION",
    "Failed": {
        "Reason": "string"
    },
    "CreationDate": "timestamp",
    "CompletionDate": "timestamp",
    "LastModifiedDate": "timestamp"
}
```

---

### 4.3 `list-capacity-tasks`

Lists the capacity tasks for your AWS account. **Paginated operation.**

**Synopsis:**
```bash
aws outposts list-capacity-tasks \
    [--outpost-identifier-filter <value>] \
    [--capacity-task-status-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-identifier-filter` | No | string | None | Filter by Outpost ID or ARN |
| `--capacity-task-status-filter` | No | list(string) | None | Filter by status: `REQUESTED`, `IN_PROGRESS`, `COMPLETED`, `FAILED`, `CANCELLED`, `WAITING_FOR_EVACUATION` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CapacityTasks": [
        {
            "CapacityTaskId": "string",
            "OutpostId": "string",
            "OrderId": "string",
            "CapacityTaskStatus": "REQUESTED|IN_PROGRESS|COMPLETED|FAILED|CANCELLED|WAITING_FOR_EVACUATION",
            "CreationDate": "timestamp",
            "CompletionDate": "timestamp",
            "LastModifiedDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `cancel-capacity-task`

Cancels a capacity task.

**Synopsis:**
```bash
aws outposts cancel-capacity-task \
    --capacity-task-id <value> \
    --outpost-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--capacity-task-id` | **Yes** | string | -- | ID of the capacity task to cancel |
| `--outpost-identifier` | **Yes** | string | -- | ID or ARN of the Outpost |

**Output Schema:**
```json
{}
```
