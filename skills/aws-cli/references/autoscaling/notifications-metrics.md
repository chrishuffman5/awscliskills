# Notifications & Metrics

### 9.1 `put-notification-configuration`

Configures an Auto Scaling group to send notifications to an SNS topic when specified events occur.

**Synopsis:**
```bash
aws autoscaling put-notification-configuration \
    --auto-scaling-group-name <value> \
    --topic-arn <value> \
    --notification-types <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--topic-arn` | **Yes** | string | -- | SNS topic ARN |
| `--notification-types` | **Yes** | list(string) | -- | Event types: `autoscaling:EC2_INSTANCE_LAUNCH`, `autoscaling:EC2_INSTANCE_TERMINATE`, `autoscaling:EC2_INSTANCE_LAUNCH_ERROR`, `autoscaling:EC2_INSTANCE_TERMINATE_ERROR`, `autoscaling:TEST_NOTIFICATION` |

**Output:** No output on success.

---

### 9.2 `delete-notification-configuration`

Deletes the specified notification configuration.

**Synopsis:**
```bash
aws autoscaling delete-notification-configuration \
    --auto-scaling-group-name <value> \
    --topic-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--topic-arn` | **Yes** | string | -- | SNS topic ARN |

**Output:** No output on success.

---

### 9.3 `describe-notification-configurations`

Describes the notification configurations for the specified Auto Scaling groups. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-notification-configurations \
    [--auto-scaling-group-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-names` | No | list(string) | None | Group names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "NotificationConfigurations": [
        {
            "AutoScalingGroupName": "string",
            "TopicARN": "string",
            "NotificationType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `enable-metrics-collection`

Enables group metrics collection for the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling enable-metrics-collection \
    --auto-scaling-group-name <value> \
    --granularity <value> \
    [--metrics <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--granularity` | **Yes** | string | -- | Collection interval: `1Minute` |
| `--metrics` | No | list(string) | None | Specific metrics to enable. Omit to enable all |

**Available Metrics:**
- `GroupMinSize`, `GroupMaxSize`, `GroupDesiredCapacity`
- `GroupInServiceInstances`, `GroupPendingInstances`, `GroupStandbyInstances`
- `GroupTerminatingInstances`, `GroupTotalInstances`
- `GroupInServiceCapacity`, `GroupPendingCapacity`, `GroupStandbyCapacity`
- `GroupTerminatingCapacity`, `GroupTotalCapacity`
- `WarmPoolDesiredCapacity`, `WarmPoolWarmedCapacity`
- `WarmPoolPendingCapacity`, `WarmPoolTerminatingCapacity`
- `WarmPoolTotalCapacity`, `GroupAndWarmPoolDesiredCapacity`, `GroupAndWarmPoolTotalCapacity`

**Output:** No output on success.

---

### 9.5 `disable-metrics-collection`

Disables group metrics collection for the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling disable-metrics-collection \
    --auto-scaling-group-name <value> \
    [--metrics <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--metrics` | No | list(string) | None | Metrics to disable. Omit to disable all |

**Output:** No output on success.

---

### 9.6 `describe-metric-collection-types`

Describes the available metrics and granularities.

**Synopsis:**
```bash
aws autoscaling describe-metric-collection-types \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "Metrics": [
        {
            "Metric": "string"
        }
    ],
    "Granularities": [
        {
            "Granularity": "1Minute"
        }
    ]
}
```

---

### 9.7 `describe-account-limits`

Describes the current Auto Scaling resource quotas for your account.

**Synopsis:**
```bash
aws autoscaling describe-account-limits \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "MaxNumberOfAutoScalingGroups": "integer",
    "MaxNumberOfLaunchConfigurations": "integer",
    "NumberOfAutoScalingGroups": "integer",
    "NumberOfLaunchConfigurations": "integer"
}
```
