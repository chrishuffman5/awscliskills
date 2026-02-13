# Run Command

### 3.1 `send-command`

Sends a command to one or more managed instances. Specify targets by instance IDs, tags, or resource groups.

**Synopsis:**
```bash
aws ssm send-command \
    --document-name <value> \
    [--document-version <value>] \
    [--document-hash <value>] \
    [--document-hash-type <value>] \
    [--instance-ids <value>] \
    [--targets <value>] \
    [--parameters <value>] \
    [--comment <value>] \
    [--timeout-seconds <value>] \
    [--max-concurrency <value>] \
    [--max-errors <value>] \
    [--output-s3-bucket-name <value>] \
    [--output-s3-key-prefix <value>] \
    [--output-s3-region <value>] \
    [--service-role-arn <value>] \
    [--notification-config <value>] \
    [--cloud-watch-output-config <value>] \
    [--alarm-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-name` | **Yes** | string | -- | SSM document to run (e.g. `AWS-RunShellScript`) |
| `--document-version` | No | string | default | Document version |
| `--instance-ids` | No | list(string) | None | Target instance IDs (max 50). Use this OR `--targets` |
| `--targets` | No | list | None | Targets using tags or resource groups |
| `--parameters` | No | map | None | Document parameters as key-value map |
| `--comment` | No | string | None | Description for the command (max 100 chars) |
| `--timeout-seconds` | No | integer | 3600 | Overall command timeout |
| `--max-concurrency` | No | string | None | Max concurrent targets (number or percentage, e.g. `10` or `10%`) |
| `--max-errors` | No | string | None | Max errors before stopping (number or percentage) |
| `--output-s3-bucket-name` | No | string | None | S3 bucket for command output |
| `--output-s3-key-prefix` | No | string | None | S3 key prefix for output |
| `--service-role-arn` | No | string | None | IAM role ARN for SNS notifications |
| `--notification-config` | No | structure | None | SNS notification configuration |
| `--cloud-watch-output-config` | No | structure | None | CloudWatch Logs output configuration |

**Targets Structure:**
```json
[
    {
        "Key": "InstanceIds|tag:TagName|resource-groups:Name",
        "Values": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "Command": {
        "CommandId": "string",
        "DocumentName": "string",
        "DocumentVersion": "string",
        "Comment": "string",
        "ExpiresAfter": "timestamp",
        "Parameters": {},
        "InstanceIds": ["string"],
        "Targets": [],
        "RequestedDateTime": "timestamp",
        "Status": "Pending|InProgress|Success|Cancelled|Failed|TimedOut|Cancelling",
        "StatusDetails": "string",
        "OutputS3Region": "string",
        "OutputS3BucketName": "string",
        "OutputS3KeyPrefix": "string",
        "MaxConcurrency": "string",
        "MaxErrors": "string",
        "TargetCount": "integer",
        "CompletedCount": "integer",
        "ErrorCount": "integer",
        "DeliveryTimedOutCount": "integer",
        "ServiceRole": "string",
        "NotificationConfig": {},
        "CloudWatchOutputConfig": {},
        "TimeoutSeconds": "integer",
        "AlarmConfiguration": {},
        "TriggeredAlarms": []
    }
}
```

---

### 3.2 `list-commands`

Lists commands sent to managed instances. **Paginated operation.**

**Synopsis:**
```bash
aws ssm list-commands \
    [--command-id <value>] \
    [--instance-id <value>] \
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
| `--command-id` | No | string | None | Filter by specific command ID |
| `--instance-id` | No | string | None | Filter by instance ID |
| `--filters` | No | list | None | Filters: `InvokedAfter`, `InvokedBefore`, `Status`, `ExecutionStage`, `DocumentName` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Commands": [
        {
            "CommandId": "string",
            "DocumentName": "string",
            "DocumentVersion": "string",
            "Comment": "string",
            "ExpiresAfter": "timestamp",
            "Parameters": {},
            "InstanceIds": ["string"],
            "Targets": [],
            "RequestedDateTime": "timestamp",
            "Status": "Pending|InProgress|Success|Cancelled|Failed|TimedOut|Cancelling",
            "StatusDetails": "string",
            "MaxConcurrency": "string",
            "MaxErrors": "string",
            "TargetCount": "integer",
            "CompletedCount": "integer",
            "ErrorCount": "integer",
            "DeliveryTimedOutCount": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.3 `list-command-invocations`

Lists the invocations of a command on individual instances. **Paginated operation.**

**Synopsis:**
```bash
aws ssm list-command-invocations \
    [--command-id <value>] \
    [--instance-id <value>] \
    [--filters <value>] \
    [--details | --no-details] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--command-id` | No | string | None | Filter by command ID |
| `--instance-id` | No | string | None | Filter by instance ID |
| `--filters` | No | list | None | Filters |
| `--details` | No | boolean | false | Include command plugin details in output |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CommandInvocations": [
        {
            "CommandId": "string",
            "InstanceId": "string",
            "InstanceName": "string",
            "Comment": "string",
            "DocumentName": "string",
            "DocumentVersion": "string",
            "RequestedDateTime": "timestamp",
            "Status": "Pending|InProgress|Delayed|Success|Cancelled|TimedOut|Failed|Cancelling",
            "StatusDetails": "string",
            "StandardOutputUrl": "string",
            "StandardErrorUrl": "string",
            "CommandPlugins": [
                {
                    "Name": "string",
                    "Status": "string",
                    "StatusDetails": "string",
                    "ResponseCode": "integer",
                    "ResponseStartDateTime": "timestamp",
                    "ResponseFinishDateTime": "timestamp",
                    "Output": "string",
                    "StandardOutputUrl": "string",
                    "StandardErrorUrl": "string",
                    "OutputS3Region": "string",
                    "OutputS3BucketName": "string",
                    "OutputS3KeyPrefix": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `get-command-invocation`

Gets detailed information about a specific command invocation on a specific instance.

**Synopsis:**
```bash
aws ssm get-command-invocation \
    --command-id <value> \
    --instance-id <value> \
    [--plugin-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--command-id` | **Yes** | string | -- | Command ID |
| `--instance-id` | **Yes** | string | -- | Instance ID |
| `--plugin-name` | No | string | None | Specific plugin to get results for |

**Output Schema:**
```json
{
    "CommandId": "string",
    "InstanceId": "string",
    "Comment": "string",
    "DocumentName": "string",
    "DocumentVersion": "string",
    "PluginName": "string",
    "ResponseCode": "integer",
    "ExecutionStartDateTime": "string",
    "ExecutionElapsedTime": "string",
    "ExecutionEndDateTime": "string",
    "Status": "Pending|InProgress|Delayed|Success|Cancelled|TimedOut|Failed|Cancelling",
    "StatusDetails": "string",
    "StandardOutputContent": "string",
    "StandardOutputUrl": "string",
    "StandardErrorContent": "string",
    "StandardErrorUrl": "string",
    "CloudWatchOutputConfig": {
        "CloudWatchLogGroupName": "string",
        "CloudWatchOutputEnabled": true
    }
}
```

---

### 3.5 `cancel-command`

Cancels a command. Instances that have already started executing the command are not affected.

**Synopsis:**
```bash
aws ssm cancel-command \
    --command-id <value> \
    [--instance-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--command-id` | **Yes** | string | -- | Command ID to cancel |
| `--instance-ids` | No | list(string) | None | Cancel on specific instances only |

**Output Schema:**
```json
{}
```
