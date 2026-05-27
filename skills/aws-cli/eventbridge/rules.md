# Rules

### 2.1 `put-rule`

Creates or updates an EventBridge rule. Rules match incoming events and route them to targets.

**Synopsis:**
```bash
aws events put-rule \
    --name <value> \
    [--schedule-expression <value>] \
    [--event-pattern <value>] \
    [--state <value>] \
    [--description <value>] \
    [--role-arn <value>] \
    [--tags <value>] \
    [--event-bus-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule name (max 64 chars) |
| `--schedule-expression` | No | string | None | Schedule expression (e.g., `rate(5 minutes)` or `cron(0 12 * * ? *)`) |
| `--event-pattern` | No | string | None | JSON event pattern for matching events |
| `--state` | No | string | `ENABLED` | Rule state: `ENABLED` or `DISABLED` |
| `--description` | No | string | None | Rule description (max 512 chars) |
| `--role-arn` | No | string | None | IAM role ARN for the rule to assume when invoking targets |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |

**Output Schema:**
```json
{
    "RuleArn": "string"
}
```

---

### 2.2 `delete-rule`

Deletes an EventBridge rule. You must remove all targets from the rule before deleting it.

**Synopsis:**
```bash
aws events delete-rule \
    --name <value> \
    [--event-bus-name <value>] \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule name to delete |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |
| `--force` | No | boolean | false | Force delete a managed rule (use with caution) |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-rule`

Describes the specified rule, including event pattern, schedule, state, and targets.

**Synopsis:**
```bash
aws events describe-rule \
    --name <value> \
    [--event-bus-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule name |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |

**Output Schema:**
```json
{
    "Name": "string",
    "Arn": "string",
    "EventPattern": "string",
    "ScheduleExpression": "string",
    "State": "ENABLED|DISABLED|ENABLED_WITH_ALL_CLOUDTRAIL_MANAGEMENT_EVENTS",
    "Description": "string",
    "RoleArn": "string",
    "ManagedBy": "string",
    "EventBusName": "string",
    "CreatedBy": "string"
}
```

---

### 2.4 `disable-rule`

Disables the specified rule. Events no longer match the rule after it is disabled.

**Synopsis:**
```bash
aws events disable-rule \
    --name <value> \
    [--event-bus-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule name to disable |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |

**Output Schema:**
```json
{}
```

---

### 2.5 `enable-rule`

Enables the specified rule.

**Synopsis:**
```bash
aws events enable-rule \
    --name <value> \
    [--event-bus-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule name to enable |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |

**Output Schema:**
```json
{}
```

---

### 2.6 `list-rules`

Lists all rules on an event bus. Supports filtering by name prefix. **Paginated operation.**

**Synopsis:**
```bash
aws events list-rules \
    [--name-prefix <value>] \
    [--event-bus-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by rule name prefix |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Rules": [
        {
            "Name": "string",
            "Arn": "string",
            "EventPattern": "string",
            "State": "ENABLED|DISABLED|ENABLED_WITH_ALL_CLOUDTRAIL_MANAGEMENT_EVENTS",
            "Description": "string",
            "ScheduleExpression": "string",
            "RoleArn": "string",
            "ManagedBy": "string",
            "EventBusName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `list-rule-names-by-target`

Lists the rules that have a specific target ARN. **Paginated operation.**

**Synopsis:**
```bash
aws events list-rule-names-by-target \
    --target-arn <value> \
    [--event-bus-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | **Yes** | string | -- | ARN of the target to search for |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RuleNames": ["string"],
    "NextToken": "string"
}
```

---

### 2.8 `test-event-pattern`

Tests whether an event pattern matches the provided event. Useful for debugging patterns.

**Synopsis:**
```bash
aws events test-event-pattern \
    --event-pattern <value> \
    --event <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-pattern` | **Yes** | string | -- | JSON event pattern to test |
| `--event` | **Yes** | string | -- | JSON event to test against the pattern |

**Output Schema:**
```json
{
    "Result": true|false
}
```
