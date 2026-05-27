# Pipes

### 1.1 `create-pipe`

Creates a new EventBridge Pipe that connects a source to a target, with optional filtering and enrichment.

**Synopsis:**
```bash
aws pipes create-pipe \
    --name <value> \
    --source <value> \
    --target <value> \
    --role-arn <value> \
    [--description <value>] \
    [--desired-state <value>] \
    [--source-parameters <value>] \
    [--enrichment <value>] \
    [--enrichment-parameters <value>] \
    [--target-parameters <value>] \
    [--log-configuration <value>] \
    [--kms-key-identifier <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipe name (1-64 chars, pattern: `[\.\-_A-Za-z0-9]+`) |
| `--source` | **Yes** | string | -- | Source resource ARN (1-1600 chars) |
| `--target` | **Yes** | string | -- | Target resource ARN (1-1600 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN (1-1600 chars) |
| `--description` | No | string | None | Description (0-512 chars) |
| `--desired-state` | No | string | None | `RUNNING` or `STOPPED` |
| `--source-parameters` | No | structure | None | Source-specific parameters |
| `--enrichment` | No | string | None | Enrichment resource ARN (0-1600 chars) |
| `--enrichment-parameters` | No | structure | None | Enrichment parameters |
| `--target-parameters` | No | structure | None | Target-specific parameters |
| `--log-configuration` | No | structure | None | Logging configuration |
| `--kms-key-identifier` | No | string | None | KMS key for encryption (0-2048 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**SourceParameters — FilterCriteria:**
```json
{
    "FilterCriteria": {
        "Filters": [{"Pattern": "string"}]
    }
}
```

**SourceParameters — SQS:**
```json
{
    "SqsQueueParameters": {
        "BatchSize": 10,
        "MaximumBatchingWindowInSeconds": 5
    }
}
```

**SourceParameters — Kinesis:**
```json
{
    "KinesisStreamParameters": {
        "StartingPosition": "TRIM_HORIZON|LATEST|AT_TIMESTAMP",
        "StartingPositionTimestamp": "timestamp",
        "BatchSize": 100,
        "MaximumBatchingWindowInSeconds": 10,
        "MaximumRecordAgeInSeconds": -1,
        "MaximumRetryAttempts": -1,
        "ParallelizationFactor": 1,
        "OnPartialBatchItemFailure": "AUTOMATIC_BISECT",
        "DeadLetterConfig": {"Arn": "string"}
    }
}
```

**SourceParameters — DynamoDB Streams:**
```json
{
    "DynamoDBStreamParameters": {
        "StartingPosition": "TRIM_HORIZON|LATEST",
        "BatchSize": 100,
        "MaximumBatchingWindowInSeconds": 10,
        "MaximumRecordAgeInSeconds": -1,
        "MaximumRetryAttempts": -1,
        "ParallelizationFactor": 1,
        "OnPartialBatchItemFailure": "AUTOMATIC_BISECT",
        "DeadLetterConfig": {"Arn": "string"}
    }
}
```

**SourceParameters — Amazon MSK:**
```json
{
    "ManagedStreamingKafkaParameters": {
        "TopicName": "string",
        "StartingPosition": "TRIM_HORIZON|LATEST",
        "BatchSize": 100,
        "MaximumBatchingWindowInSeconds": 10,
        "ConsumerGroupID": "string",
        "Credentials": {
            "SaslScram512Auth": "string",
            "ClientCertificateTlsAuth": "string"
        }
    }
}
```

**SourceParameters — Self-managed Kafka:**
```json
{
    "SelfManagedKafkaParameters": {
        "TopicName": "string",
        "StartingPosition": "TRIM_HORIZON|LATEST",
        "AdditionalBootstrapServers": ["string"],
        "BatchSize": 100,
        "MaximumBatchingWindowInSeconds": 10,
        "ConsumerGroupID": "string",
        "Credentials": {
            "BasicAuth": "string",
            "SaslScram512Auth": "string",
            "SaslScram256Auth": "string",
            "ClientCertificateTlsAuth": "string"
        },
        "ServerRootCaCertificate": "string",
        "Vpc": {"Subnets": ["string"], "SecurityGroup": ["string"]}
    }
}
```

**SourceParameters — ActiveMQ:**
```json
{
    "ActiveMQBrokerParameters": {
        "Credentials": {"BasicAuth": "string"},
        "QueueName": "string",
        "BatchSize": 10,
        "MaximumBatchingWindowInSeconds": 5
    }
}
```

**SourceParameters — RabbitMQ:**
```json
{
    "RabbitMQBrokerParameters": {
        "Credentials": {"BasicAuth": "string"},
        "QueueName": "string",
        "VirtualHost": "string",
        "BatchSize": 10,
        "MaximumBatchingWindowInSeconds": 5
    }
}
```

**EnrichmentParameters:**
```json
{
    "InputTemplate": "string",
    "HttpParameters": {
        "PathParameterValues": ["string"],
        "HeaderParameters": {"string": "string"},
        "QueryStringParameters": {"string": "string"}
    }
}
```

**TargetParameters — Lambda:**
```json
{
    "LambdaFunctionParameters": {
        "InvocationType": "REQUEST_RESPONSE|FIRE_AND_FORGET"
    }
}
```

**TargetParameters — Step Functions:**
```json
{
    "StepFunctionStateMachineParameters": {
        "InvocationType": "REQUEST_RESPONSE|FIRE_AND_FORGET"
    }
}
```

**TargetParameters — ECS:**
```json
{
    "EcsTaskParameters": {
        "TaskDefinitionArn": "string",
        "TaskCount": 1,
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
        "EnableECSManagedTags": false,
        "EnableExecuteCommand": false,
        "PlacementConstraints": [],
        "PlacementStrategy": [],
        "PropagateTags": "TASK_DEFINITION",
        "Overrides": {},
        "Tags": []
    }
}
```

**TargetParameters — Batch:**
```json
{
    "BatchJobParameters": {
        "JobDefinition": "string",
        "JobName": "string",
        "ArrayProperties": {"Size": 1},
        "RetryStrategy": {"Attempts": 1},
        "ContainerOverrides": {},
        "DependsOn": [],
        "Parameters": {}
    }
}
```

**TargetParameters — SQS:**
```json
{
    "SqsQueueParameters": {
        "MessageGroupId": "string",
        "MessageDeduplicationId": "string"
    }
}
```

**TargetParameters — Kinesis:**
```json
{
    "KinesisStreamParameters": {
        "PartitionKey": "string"
    }
}
```

**TargetParameters — EventBridge:**
```json
{
    "EventBridgeEventBusParameters": {
        "EndpointId": "string",
        "DetailType": "string",
        "Source": "string",
        "Resources": ["string"],
        "Time": "string"
    }
}
```

**TargetParameters — CloudWatch Logs:**
```json
{
    "CloudWatchLogsParameters": {
        "LogStreamName": "string",
        "Timestamp": "string"
    }
}
```

**TargetParameters — Redshift:**
```json
{
    "RedshiftDataParameters": {
        "SecretManagerArn": "string",
        "Database": "string",
        "DbUser": "string",
        "StatementName": "string",
        "WithEvent": false,
        "Sqls": ["string"]
    }
}
```

**TargetParameters — SageMaker:**
```json
{
    "SageMakerPipelineParameters": {
        "PipelineParameterList": [{"Name": "string", "Value": "string"}]
    }
}
```

**TargetParameters — Timestream:**
```json
{
    "TimestreamParameters": {
        "TimeValue": "string",
        "EpochTimeUnit": "MILLISECONDS|SECONDS|MICROSECONDS|NANOSECONDS",
        "TimeFieldType": "EPOCH|TIMESTAMP_FORMAT",
        "TimestampFormat": "string",
        "VersionValue": "string",
        "DimensionMappings": [{"DimensionValue":"string","DimensionValueType":"VARCHAR","DimensionName":"string"}],
        "SingleMeasureMappings": [{"MeasureValue":"string","MeasureValueType":"DOUBLE|BIGINT|VARCHAR|BOOLEAN|TIMESTAMP","MeasureName":"string"}],
        "MultiMeasureMappings": []
    }
}
```

**TargetParameters — HTTP (API Gateway / API Destination):**
```json
{
    "HttpParameters": {
        "PathParameterValues": ["string"],
        "HeaderParameters": {"string": "string"},
        "QueryStringParameters": {"string": "string"}
    }
}
```

**LogConfiguration:**
```json
{
    "S3LogDestination": {
        "BucketName": "string",
        "Prefix": "string",
        "BucketOwner": "string",
        "OutputFormat": "json|plain|w3c"
    },
    "FirehoseLogDestination": {
        "DeliveryStreamArn": "string"
    },
    "CloudwatchLogsLogDestination": {
        "LogGroupArn": "string"
    },
    "Level": "OFF|ERROR|INFO|TRACE",
    "IncludeExecutionData": ["ALL"]
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "DesiredState": "RUNNING|STOPPED",
    "CurrentState": "RUNNING|STOPPED|CREATING|UPDATING|DELETING|STARTING|STOPPING|CREATE_FAILED|UPDATE_FAILED|START_FAILED|STOP_FAILED|DELETE_FAILED|CREATE_ROLLBACK_FAILED|DELETE_ROLLBACK_FAILED|UPDATE_ROLLBACK_FAILED",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 1.2 `describe-pipe`

Retrieves detailed information about a pipe including all source, enrichment, target, and logging configuration.

**Synopsis:**
```bash
aws pipes describe-pipe \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipe name (1-64 chars) |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "Description": "string",
    "DesiredState": "RUNNING|STOPPED|DELETED",
    "CurrentState": "RUNNING|STOPPED|CREATING|UPDATING|DELETING|STARTING|STOPPING|CREATE_FAILED|UPDATE_FAILED|START_FAILED|STOP_FAILED|DELETE_FAILED|CREATE_ROLLBACK_FAILED|DELETE_ROLLBACK_FAILED|UPDATE_ROLLBACK_FAILED",
    "StateReason": "string",
    "Source": "string",
    "SourceParameters": {
        "FilterCriteria": {"Filters": [{"Pattern": "string"}]},
        "KinesisStreamParameters": {},
        "DynamoDBStreamParameters": {},
        "SqsQueueParameters": {},
        "ActiveMQBrokerParameters": {},
        "RabbitMQBrokerParameters": {},
        "ManagedStreamingKafkaParameters": {},
        "SelfManagedKafkaParameters": {}
    },
    "Enrichment": "string",
    "EnrichmentParameters": {
        "InputTemplate": "string",
        "HttpParameters": {}
    },
    "Target": "string",
    "TargetParameters": {
        "InputTemplate": "string",
        "LambdaFunctionParameters": {},
        "StepFunctionStateMachineParameters": {},
        "KinesisStreamParameters": {},
        "EcsTaskParameters": {},
        "BatchJobParameters": {},
        "SqsQueueParameters": {},
        "HttpParameters": {},
        "RedshiftDataParameters": {},
        "SageMakerPipelineParameters": {},
        "EventBridgeEventBusParameters": {},
        "CloudWatchLogsParameters": {},
        "TimestreamParameters": {}
    },
    "RoleArn": "string",
    "Tags": {},
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LogConfiguration": {
        "S3LogDestination": {},
        "FirehoseLogDestination": {},
        "CloudwatchLogsLogDestination": {},
        "Level": "OFF|ERROR|INFO|TRACE",
        "IncludeExecutionData": ["ALL"]
    },
    "KmsKeyIdentifier": "string"
}
```

---

### 1.3 `list-pipes`

Lists all pipes. **Paginated operation.**

**Synopsis:**
```bash
aws pipes list-pipes \
    [--name-prefix <value>] \
    [--desired-state <value>] \
    [--current-state <value>] \
    [--source-prefix <value>] \
    [--target-prefix <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by pipe name prefix (1-64 chars) |
| `--desired-state` | No | string | None | Filter: `RUNNING` or `STOPPED` |
| `--current-state` | No | string | None | Filter by current state |
| `--source-prefix` | No | string | None | Filter by source ARN prefix (1-1600 chars) |
| `--target-prefix` | No | string | None | Filter by target ARN prefix (1-1600 chars) |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Current state values:** `RUNNING`, `STOPPED`, `CREATING`, `UPDATING`, `DELETING`, `STARTING`, `STOPPING`, `CREATE_FAILED`, `UPDATE_FAILED`, `START_FAILED`, `STOP_FAILED`, `DELETE_FAILED`, `CREATE_ROLLBACK_FAILED`, `DELETE_ROLLBACK_FAILED`, `UPDATE_ROLLBACK_FAILED`

**Output Schema:**
```json
{
    "Pipes": [
        {
            "Name": "string",
            "Arn": "string",
            "DesiredState": "RUNNING|STOPPED",
            "CurrentState": "string",
            "StateReason": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "Source": "string",
            "Target": "string",
            "Enrichment": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-pipe`

Updates an existing pipe. Only specified fields are updated; unspecified fields remain unchanged. Source and target service-specific parameters are updated atomically.

**Synopsis:**
```bash
aws pipes update-pipe \
    --name <value> \
    --role-arn <value> \
    [--description <value>] \
    [--desired-state <value>] \
    [--source-parameters <value>] \
    [--enrichment <value>] \
    [--enrichment-parameters <value>] \
    [--target <value>] \
    [--target-parameters <value>] \
    [--log-configuration <value>] \
    [--kms-key-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipe name (1-64 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN (1-1600 chars) |
| `--description` | No | string | None | Updated description (0-512 chars) |
| `--desired-state` | No | string | None | `RUNNING` or `STOPPED` |
| `--source-parameters` | No | structure | None | Updated source parameters |
| `--enrichment` | No | string | None | Updated enrichment ARN |
| `--enrichment-parameters` | No | structure | None | Updated enrichment parameters |
| `--target` | No | string | None | Updated target ARN (1-1600 chars) |
| `--target-parameters` | No | structure | None | Updated target parameters |
| `--log-configuration` | No | structure | None | Updated logging configuration |
| `--kms-key-identifier` | No | string | None | Updated KMS key (0-2048 chars) |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "DesiredState": "RUNNING|STOPPED",
    "CurrentState": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 1.5 `delete-pipe`

Deletes a pipe.

**Synopsis:**
```bash
aws pipes delete-pipe \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipe name (1-64 chars) |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "DesiredState": "DELETED",
    "CurrentState": "DELETING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 1.6 `start-pipe`

Starts a stopped pipe.

**Synopsis:**
```bash
aws pipes start-pipe \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipe name (1-64 chars) |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "DesiredState": "RUNNING",
    "CurrentState": "STARTING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 1.7 `stop-pipe`

Stops a running pipe.

**Synopsis:**
```bash
aws pipes stop-pipe \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipe name (1-64 chars) |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "DesiredState": "STOPPED",
    "CurrentState": "STOPPING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```
