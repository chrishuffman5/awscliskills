# Targets

### 3.1 `put-targets`

Adds the specified targets to a rule, or updates existing targets. Up to 5 targets per rule.

**Synopsis:**
```bash
aws events put-targets \
    --rule <value> \
    --targets <value> \
    [--event-bus-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule` | **Yes** | string | -- | Rule name to add targets to |
| `--targets` | **Yes** | list | -- | Target definitions (max 5 per rule) |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |

**Target Structure:**
```json
[
    {
        "Id": "string",
        "Arn": "string",
        "RoleArn": "string",
        "Input": "string",
        "InputPath": "string",
        "InputTransformer": {
            "InputPathsMap": {
                "key": "string"
            },
            "InputTemplate": "string"
        },
        "KinesisParameters": {
            "PartitionKeyPath": "string"
        },
        "RunCommandParameters": {
            "RunCommandTargets": [
                {
                    "Key": "string",
                    "Values": ["string"]
                }
            ]
        },
        "EcsParameters": {
            "TaskDefinitionArn": "string",
            "TaskCount": "integer",
            "LaunchType": "EC2|FARGATE|EXTERNAL",
            "NetworkConfiguration": {
                "awsvpcConfiguration": {
                    "Subnets": ["string"],
                    "SecurityGroups": ["string"],
                    "AssignPublicIp": "ENABLED|DISABLED"
                }
            },
            "PlatformVersion": "string",
            "Group": "string",
            "CapacityProviderStrategy": [],
            "EnableECSManagedTags": true|false,
            "EnableExecuteCommand": true|false,
            "PlacementConstraints": [],
            "PlacementStrategy": [],
            "PropagateTags": "TASK_DEFINITION",
            "ReferenceId": "string",
            "Tags": []
        },
        "BatchParameters": {
            "JobDefinition": "string",
            "JobName": "string",
            "ArrayProperties": {
                "Size": "integer"
            },
            "RetryStrategy": {
                "Attempts": "integer"
            }
        },
        "SqsParameters": {
            "MessageGroupId": "string"
        },
        "HttpParameters": {
            "PathParameterValues": ["string"],
            "HeaderParameters": {
                "key": "string"
            },
            "QueryStringParameters": {
                "key": "string"
            }
        },
        "RedshiftDataParameters": {
            "SecretManagerArn": "string",
            "Database": "string",
            "DbUser": "string",
            "Sql": "string",
            "StatementName": "string",
            "WithEvent": true|false,
            "Sqls": ["string"]
        },
        "SageMakerPipelineParameters": {
            "PipelineParameterList": [
                {
                    "Name": "string",
                    "Value": "string"
                }
            ]
        },
        "DeadLetterConfig": {
            "Arn": "string"
        },
        "RetryPolicy": {
            "MaximumRetryAttempts": "integer",
            "MaximumEventAgeInSeconds": "integer"
        },
        "AppSyncParameters": {
            "GraphQLOperation": "string"
        }
    }
]
```

**Output Schema:**
```json
{
    "FailedEntryCount": "integer",
    "FailedEntries": [
        {
            "TargetId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 3.2 `remove-targets`

Removes the specified targets from a rule. Targets must be removed before a rule can be deleted.

**Synopsis:**
```bash
aws events remove-targets \
    --rule <value> \
    --ids <value> \
    [--event-bus-name <value>] \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule` | **Yes** | string | -- | Rule name to remove targets from |
| `--ids` | **Yes** | list(string) | -- | Target IDs to remove |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |
| `--force` | No | boolean | false | Force remove targets from a managed rule |

**Output Schema:**
```json
{
    "FailedEntryCount": "integer",
    "FailedEntries": [
        {
            "TargetId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 3.3 `list-targets-by-rule`

Lists all targets for a specified rule. **Paginated operation.**

**Synopsis:**
```bash
aws events list-targets-by-rule \
    --rule <value> \
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
| `--rule` | **Yes** | string | -- | Rule name |
| `--event-bus-name` | No | string | `default` | Event bus name or ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Targets": [
        {
            "Id": "string",
            "Arn": "string",
            "RoleArn": "string",
            "Input": "string",
            "InputPath": "string",
            "InputTransformer": {},
            "KinesisParameters": {},
            "RunCommandParameters": {},
            "EcsParameters": {},
            "BatchParameters": {},
            "SqsParameters": {},
            "HttpParameters": {},
            "RedshiftDataParameters": {},
            "SageMakerPipelineParameters": {},
            "DeadLetterConfig": {},
            "RetryPolicy": {},
            "AppSyncParameters": {}
        }
    ],
    "NextToken": "string"
}
```
