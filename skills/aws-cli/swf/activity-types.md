# Activity Types

### 3.1 `register-activity-type`

Registers a new activity type and its configuration in the specified domain.

**Synopsis:**
```bash
aws swf register-activity-type \
    --domain <value> \
    --name <value> \
    --activity-version <value> \
    [--description <value>] \
    [--default-task-start-to-close-timeout <value>] \
    [--default-task-heartbeat-timeout <value>] \
    [--default-task-list <value>] \
    [--default-task-priority <value>] \
    [--default-task-schedule-to-start-timeout <value>] \
    [--default-task-schedule-to-close-timeout <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--name` | **Yes** | string | -- | Activity type name (1-256 chars) |
| `--activity-version` | **Yes** | string | -- | Version string (1-64 chars). Name+version must be unique |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--default-task-start-to-close-timeout` | No | string | None | Default max duration a worker can take (seconds), or `NONE` |
| `--default-task-heartbeat-timeout` | No | string | None | Default max time before heartbeat required (seconds), or `NONE` |
| `--default-task-list` | No | structure | None | Default task list. Shorthand: `name=string` |
| `--default-task-priority` | No | string | `0` | Default task priority (integer) |
| `--default-task-schedule-to-start-timeout` | No | string | None | Default max wait time before assignment (seconds), or `NONE` |
| `--default-task-schedule-to-close-timeout` | No | string | None | Default max total duration (seconds), or `NONE` |

**Output:** None

---

### 3.2 `describe-activity-type`

Describes an activity type including its configuration settings.

**Synopsis:**
```bash
aws swf describe-activity-type \
    --domain <value> \
    --activity-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--activity-type` | **Yes** | structure | -- | Activity type. Shorthand: `name=string,version=string` |

**Output Schema:**
```json
{
    "typeInfo": {
        "activityType": {
            "name": "string",
            "version": "string"
        },
        "status": "REGISTERED|DEPRECATED",
        "description": "string",
        "creationDate": "timestamp",
        "deprecationDate": "timestamp"
    },
    "configuration": {
        "defaultTaskStartToCloseTimeout": "string",
        "defaultTaskHeartbeatTimeout": "string",
        "defaultTaskList": {
            "name": "string"
        },
        "defaultTaskPriority": "string",
        "defaultTaskScheduleToStartTimeout": "string",
        "defaultTaskScheduleToCloseTimeout": "string"
    }
}
```

---

### 3.3 `list-activity-types`

Lists activity types in a domain. **Paginated operation.**

**Synopsis:**
```bash
aws swf list-activity-types \
    --domain <value> \
    --registration-status <value> \
    [--name <value>] \
    [--reverse-order | --no-reverse-order] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--registration-status` | **Yes** | string | -- | `REGISTERED` or `DEPRECATED` |
| `--name` | No | string | None | Filter by activity type name |
| `--reverse-order` | No | boolean | false | Return results in reverse order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "typeInfos": [
        {
            "activityType": {
                "name": "string",
                "version": "string"
            },
            "status": "REGISTERED|DEPRECATED",
            "description": "string",
            "creationDate": "timestamp",
            "deprecationDate": "timestamp"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 3.4 `deprecate-activity-type`

Deprecates an activity type. No new tasks of this type can be scheduled, but existing ones continue.

**Synopsis:**
```bash
aws swf deprecate-activity-type \
    --domain <value> \
    --activity-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--activity-type` | **Yes** | structure | -- | Activity type. Shorthand: `name=string,version=string` |

**Output:** None

---

### 3.5 `undeprecate-activity-type`

Undeprecates a previously deprecated activity type.

**Synopsis:**
```bash
aws swf undeprecate-activity-type \
    --domain <value> \
    --activity-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--activity-type` | **Yes** | structure | -- | Activity type. Shorthand: `name=string,version=string` |

**Output:** None

---

### 3.6 `delete-activity-type`

Deletes an activity type. The type must be deprecated first and have no pending tasks.

**Synopsis:**
```bash
aws swf delete-activity-type \
    --domain <value> \
    --activity-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--activity-type` | **Yes** | structure | -- | Activity type. Shorthand: `name=string,version=string` |

**Output:** None
