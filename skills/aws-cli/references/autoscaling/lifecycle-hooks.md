# Lifecycle Hooks

### 4.1 `put-lifecycle-hook`

Creates or updates a lifecycle hook for the specified Auto Scaling group. A lifecycle hook allows you to perform custom actions as the group launches or terminates instances.

**Synopsis:**
```bash
aws autoscaling put-lifecycle-hook \
    --lifecycle-hook-name <value> \
    --auto-scaling-group-name <value> \
    [--lifecycle-transition <value>] \
    [--role-arn <value>] \
    [--notification-target-arn <value>] \
    [--notification-metadata <value>] \
    [--heartbeat-timeout <value>] \
    [--default-result <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-hook-name` | **Yes** | string | -- | Hook name |
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--lifecycle-transition` | No | string | None | `autoscaling:EC2_INSTANCE_LAUNCHING` or `autoscaling:EC2_INSTANCE_TERMINATING` |
| `--role-arn` | No | string | None | IAM role ARN for publishing to notification target |
| `--notification-target-arn` | No | string | None | SNS topic or SQS queue ARN |
| `--notification-metadata` | No | string | None | Additional metadata to include in notification |
| `--heartbeat-timeout` | No | integer | 3600 | Heartbeat timeout in seconds (30-7200) |
| `--default-result` | No | string | `ABANDON` | `CONTINUE` or `ABANDON` |

**Output:** No output on success (empty JSON `{}`).

---

### 4.2 `delete-lifecycle-hook`

Deletes the specified lifecycle hook.

**Synopsis:**
```bash
aws autoscaling delete-lifecycle-hook \
    --lifecycle-hook-name <value> \
    --auto-scaling-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-hook-name` | **Yes** | string | -- | Hook name |
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |

**Output:** No output on success (empty JSON `{}`).

---

### 4.3 `describe-lifecycle-hooks`

Describes the lifecycle hooks for the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling describe-lifecycle-hooks \
    --auto-scaling-group-name <value> \
    [--lifecycle-hook-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--lifecycle-hook-names` | No | list(string) | None | Specific hook names |

**Output Schema:**
```json
{
    "LifecycleHooks": [
        {
            "LifecycleHookName": "string",
            "AutoScalingGroupName": "string",
            "LifecycleTransition": "autoscaling:EC2_INSTANCE_LAUNCHING|autoscaling:EC2_INSTANCE_TERMINATING",
            "NotificationTargetARN": "string",
            "RoleARN": "string",
            "NotificationMetadata": "string",
            "HeartbeatTimeout": "integer",
            "GlobalTimeout": "integer",
            "DefaultResult": "CONTINUE|ABANDON"
        }
    ]
}
```

---

### 4.4 `describe-lifecycle-hook-types`

Describes the available types of lifecycle hooks.

**Synopsis:**
```bash
aws autoscaling describe-lifecycle-hook-types \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "LifecycleHookTypes": [
        "autoscaling:EC2_INSTANCE_LAUNCHING",
        "autoscaling:EC2_INSTANCE_TERMINATING"
    ]
}
```

---

### 4.5 `complete-lifecycle-action`

Completes the lifecycle action for the specified token or instance.

**Synopsis:**
```bash
aws autoscaling complete-lifecycle-action \
    --lifecycle-hook-name <value> \
    --auto-scaling-group-name <value> \
    --lifecycle-action-result <value> \
    [--lifecycle-action-token <value>] \
    [--instance-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-hook-name` | **Yes** | string | -- | Hook name |
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--lifecycle-action-result` | **Yes** | string | -- | `CONTINUE` or `ABANDON` |
| `--lifecycle-action-token` | No | string | None | Token from the lifecycle notification |
| `--instance-id` | No | string | None | Instance ID (alternative to token) |

**Output:** No output on success (empty JSON `{}`).

---

### 4.6 `record-lifecycle-action-heartbeat`

Records a heartbeat for a lifecycle action, extending the timeout.

**Synopsis:**
```bash
aws autoscaling record-lifecycle-action-heartbeat \
    --lifecycle-hook-name <value> \
    --auto-scaling-group-name <value> \
    [--lifecycle-action-token <value>] \
    [--instance-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-hook-name` | **Yes** | string | -- | Hook name |
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--lifecycle-action-token` | No | string | None | Token from notification |
| `--instance-id` | No | string | None | Instance ID |

**Output:** No output on success (empty JSON `{}`).
