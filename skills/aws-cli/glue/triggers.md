# Triggers

### 8.1 `create-trigger`

Creates a new trigger.

**Synopsis:**
```bash
aws glue create-trigger \
    --name <value> \
    --type <value> \
    --actions <value> \
    [--workflow-name <value>] \
    [--schedule <value>] \
    [--predicate <value>] \
    [--description <value>] \
    [--start-on-creation | --no-start-on-creation] \
    [--tags <value>] \
    [--event-batching-condition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trigger name |
| `--type` | **Yes** | string | -- | `SCHEDULED`, `CONDITIONAL`, `ON_DEMAND`, `EVENT` |
| `--actions` | **Yes** | list | -- | Actions to trigger. Shorthand: `JobName=string,Arguments={key=value},Timeout=integer,SecurityConfiguration=string,NotificationProperty={NotifyDelayAfter=integer},CrawlerName=string ...` |
| `--workflow-name` | No | string | -- | Associated workflow |
| `--schedule` | No | string | -- | Cron expression (for SCHEDULED type) |
| `--predicate` | No | structure | -- | Predicate conditions (for CONDITIONAL type). JSON |
| `--description` | No | string | -- | Description |
| `--start-on-creation` | No | boolean | false | Start trigger immediately after creation |
| `--tags` | No | map | -- | Tags as JSON |
| `--event-batching-condition` | No | structure | -- | Event batching. Shorthand: `BatchSize=integer,BatchWindow=integer` |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 8.2 `delete-trigger`

Deletes a trigger.

**Synopsis:**
```bash
aws glue delete-trigger \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trigger name |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 8.3 `get-trigger`

Retrieves a trigger definition.

**Synopsis:**
```bash
aws glue get-trigger \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trigger name |

**Output Schema:**
```json
{
    "Trigger": {
        "Name": "string",
        "WorkflowName": "string",
        "Id": "string",
        "Type": "SCHEDULED|CONDITIONAL|ON_DEMAND|EVENT",
        "State": "CREATING|CREATED|ACTIVATING|ACTIVATED|DEACTIVATING|DEACTIVATED|DELETING|UPDATING",
        "Description": "string",
        "Schedule": "string",
        "Actions": [
            {
                "JobName": "string",
                "Arguments": {},
                "Timeout": "integer",
                "SecurityConfiguration": "string",
                "NotificationProperty": {
                    "NotifyDelayAfter": "integer"
                },
                "CrawlerName": "string"
            }
        ],
        "Predicate": {
            "Logical": "AND|ANY",
            "Conditions": [
                {
                    "LogicalOperator": "EQUALS",
                    "JobName": "string",
                    "State": "STARTING|RUNNING|STOPPING|STOPPED|SUCCEEDED|FAILED|TIMEOUT|ERROR|WAITING",
                    "CrawlerName": "string",
                    "CrawlState": "RUNNING|CANCELLING|CANCELLED|SUCCEEDED|FAILED|ERROR"
                }
            ]
        },
        "EventBatchingCondition": {
            "BatchSize": "integer",
            "BatchWindow": "integer"
        }
    }
}
```

---

### 8.4 `get-triggers`

Retrieves all triggers. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-triggers \
    [--dependent-job-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dependent-job-name` | No | string | -- | Filter by dependent job |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Triggers": ["<Trigger structure>"],
    "NextToken": "string"
}
```

---

### 8.5 `update-trigger`

Updates a trigger definition.

**Synopsis:**
```bash
aws glue update-trigger \
    --name <value> \
    --trigger-update <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trigger name |
| `--trigger-update` | **Yes** | structure | -- | Updated trigger definition (JSON) |

**Output Schema:**
```json
{
    "Trigger": "<Trigger structure>"
}
```

---

### 8.6 `start-trigger`

Starts an existing trigger (activates it).

**Synopsis:**
```bash
aws glue start-trigger \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trigger name |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 8.7 `stop-trigger`

Stops an active trigger (deactivates it).

**Synopsis:**
```bash
aws glue stop-trigger \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trigger name |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 8.8 `batch-get-triggers`

Returns detailed information for a list of triggers.

**Synopsis:**
```bash
aws glue batch-get-triggers \
    --trigger-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trigger-names` | **Yes** | list(string) | -- | Trigger names |

**Output Schema:**
```json
{
    "Triggers": ["<Trigger structure>"],
    "TriggersNotFound": ["string"]
}
```

---

### 8.9 `list-triggers`

Lists trigger names. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-triggers \
    [--dependent-job-name <value>] \
    [--tags <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dependent-job-name` | No | string | -- | Filter by dependent job |
| `--tags` | No | map | -- | Filter by tags |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "TriggerNames": ["string"],
    "NextToken": "string"
}
```
