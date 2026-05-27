# Counting

### 7.1 `count-open-workflow-executions`

Returns the number of open workflow executions within a domain matching the specified filtering criteria.

**Synopsis:**
```bash
aws swf count-open-workflow-executions \
    --domain <value> \
    --start-time-filter <value> \
    [--type-filter <value>] \
    [--tag-filter <value>] \
    [--execution-filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--start-time-filter` | **Yes** | structure | -- | Start time range. Shorthand: `oldestDate=timestamp,latestDate=timestamp` |
| `--type-filter` | No | structure | None | Filter by workflow type. Shorthand: `name=string,version=string`. Mutually exclusive with `--tag-filter` and `--execution-filter` |
| `--tag-filter` | No | structure | None | Filter by tag. Shorthand: `tag=string`. Mutually exclusive with others |
| `--execution-filter` | No | structure | None | Filter by workflow ID. Shorthand: `workflowId=string`. Mutually exclusive with others |

**Output Schema:**
```json
{
    "count": "integer",
    "truncated": "boolean"
}
```

---

### 7.2 `count-closed-workflow-executions`

Returns the number of closed workflow executions within a domain matching the specified filtering criteria.

**Synopsis:**
```bash
aws swf count-closed-workflow-executions \
    --domain <value> \
    [--start-time-filter <value>] \
    [--close-time-filter <value>] \
    [--type-filter <value>] \
    [--tag-filter <value>] \
    [--execution-filter <value>] \
    [--close-status-filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--start-time-filter` | No | structure | None | Filter by start time. Mutually exclusive with `--close-time-filter` |
| `--close-time-filter` | No | structure | None | Filter by close time. Mutually exclusive with `--start-time-filter` |
| `--type-filter` | No | structure | None | Filter by workflow type. Mutually exclusive with `--tag-filter`, `--execution-filter`, `--close-status-filter` |
| `--tag-filter` | No | structure | None | Filter by tag. Mutually exclusive with others |
| `--execution-filter` | No | structure | None | Filter by workflow ID. Mutually exclusive with others |
| `--close-status-filter` | No | structure | None | Filter by close status. Shorthand: `status=COMPLETED|FAILED|CANCELED|TERMINATED|CONTINUED_AS_NEW|TIMED_OUT` |

**Output Schema:**
```json
{
    "count": "integer",
    "truncated": "boolean"
}
```

---

### 7.3 `count-pending-activity-tasks`

Returns the estimated number of pending activity tasks in the specified task list.

**Synopsis:**
```bash
aws swf count-pending-activity-tasks \
    --domain <value> \
    --task-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--task-list` | **Yes** | structure | -- | Task list to count. Shorthand: `name=string` |

**Output Schema:**
```json
{
    "count": "integer",
    "truncated": "boolean"
}
```

---

### 7.4 `count-pending-decision-tasks`

Returns the estimated number of pending decision tasks in the specified task list.

**Synopsis:**
```bash
aws swf count-pending-decision-tasks \
    --domain <value> \
    --task-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--task-list` | **Yes** | structure | -- | Task list to count. Shorthand: `name=string` |

**Output Schema:**
```json
{
    "count": "integer",
    "truncated": "boolean"
}
```
