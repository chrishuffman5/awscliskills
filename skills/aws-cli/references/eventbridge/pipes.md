# Pipes

Commands use the `aws pipes` service namespace. EventBridge Pipes connects event sources to targets with optional filtering, enrichment, and transformation.

### 9.1 `create-pipe`

Creates a pipe that connects a source to a target.

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
    [--tags <value>] \
    [--log-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipe name (max 64 chars) |
| `--source` | **Yes** | string | -- | Source ARN (SQS, Kinesis, DynamoDB Streams, MSK, self-managed Kafka, MQ) |
| `--target` | **Yes** | string | -- | Target ARN (Lambda, Step Functions, API Gateway, EventBridge, etc.) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for the pipe |
| `--description` | No | string | None | Pipe description |
| `--desired-state` | No | string | `RUNNING` | Desired state: `RUNNING` or `STOPPED` |
| `--source-parameters` | No | structure | None | Source-specific parameters |
| `--enrichment` | No | string | None | Enrichment ARN (Lambda, Step Functions, API Gateway, API destination) |
| `--enrichment-parameters` | No | structure | None | Enrichment parameters |
| `--target-parameters` | No | structure | None | Target-specific parameters |
| `--tags` | No | map | None | Tags |
| `--log-configuration` | No | structure | None | Logging configuration |

**Source Parameters Structure (SQS example):**
```json
{
    "SqsQueueParameters": {
        "BatchSize": "integer",
        "MaximumBatchingWindowInSeconds": "integer"
    },
    "FilterCriteria": {
        "Filters": [
            {
                "Pattern": "string"
            }
        ]
    }
}
```

**Source Parameters Structure (Kinesis example):**
```json
{
    "KinesisStreamParameters": {
        "BatchSize": "integer",
        "MaximumBatchingWindowInSeconds": "integer",
        "MaximumRetryAttempts": "integer",
        "MaximumRecordAgeInSeconds": "integer",
        "OnPartialBatchItemFailure": "AUTOMATIC_BISECT",
        "ParallelizationFactor": "integer",
        "StartingPosition": "TRIM_HORIZON|LATEST|AT_TIMESTAMP",
        "StartingPositionTimestamp": "timestamp",
        "DeadLetterConfig": {
            "Arn": "string"
        }
    },
    "FilterCriteria": {
        "Filters": [
            {
                "Pattern": "string"
            }
        ]
    }
}
```

**Source Parameters Structure (DynamoDB Streams example):**
```json
{
    "DynamoDBStreamParameters": {
        "BatchSize": "integer",
        "MaximumBatchingWindowInSeconds": "integer",
        "MaximumRetryAttempts": "integer",
        "MaximumRecordAgeInSeconds": "integer",
        "OnPartialBatchItemFailure": "AUTOMATIC_BISECT",
        "ParallelizationFactor": "integer",
        "StartingPosition": "TRIM_HORIZON|LATEST",
        "DeadLetterConfig": {
            "Arn": "string"
        }
    },
    "FilterCriteria": {}
}
```

**Target Parameters Structure (Lambda example):**
```json
{
    "LambdaFunctionParameters": {
        "InvocationType": "REQUEST_RESPONSE|FIRE_AND_FORGET"
    },
    "InputTemplate": "string"
}
```

**Target Parameters Structure (Step Functions example):**
```json
{
    "StepFunctionStateMachineParameters": {
        "InvocationType": "REQUEST_RESPONSE|FIRE_AND_FORGET"
    },
    "InputTemplate": "string"
}
```

**Log Configuration Structure:**
```json
{
    "S3LogDestination": {
        "BucketName": "string",
        "BucketOwner": "string",
        "OutputFormat": "json|plain|w3c",
        "Prefix": "string"
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
    "CurrentState": "CREATING|STARTING|RUNNING|STOPPING|STOPPED|CREATE_FAILED",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 9.2 `delete-pipe`

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
| `--name` | **Yes** | string | -- | Pipe name or ARN to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "DesiredState": "RUNNING|STOPPED",
    "CurrentState": "DELETING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 9.3 `describe-pipe`

Retrieves details about a pipe.

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
| `--name` | **Yes** | string | -- | Pipe name or ARN |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "Description": "string",
    "DesiredState": "RUNNING|STOPPED",
    "CurrentState": "RUNNING|STOPPED|CREATING|UPDATING|DELETING|STARTING|STOPPING|CREATE_FAILED|UPDATE_FAILED|START_FAILED|STOP_FAILED|DELETE_FAILED",
    "StateReason": "string",
    "Source": "string",
    "SourceParameters": {},
    "Enrichment": "string",
    "EnrichmentParameters": {},
    "Target": "string",
    "TargetParameters": {},
    "RoleArn": "string",
    "Tags": {},
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LogConfiguration": {}
}
```

---

### 9.4 `list-pipes`

Lists all pipes. Supports filtering. **Paginated operation.**

**Synopsis:**
```bash
aws pipes list-pipes \
    [--name-prefix <value>] \
    [--desired-state <value>] \
    [--current-state <value>] \
    [--source-prefix <value>] \
    [--target-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by pipe name prefix |
| `--desired-state` | No | string | None | Filter by desired state: `RUNNING`, `STOPPED` |
| `--current-state` | No | string | None | Filter by current state |
| `--source-prefix` | No | string | None | Filter by source ARN prefix |
| `--target-prefix` | No | string | None | Filter by target ARN prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

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
            "Source": "string",
            "Enrichment": "string",
            "Target": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `start-pipe`

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
| `--name` | **Yes** | string | -- | Pipe name or ARN to start |

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

### 9.6 `stop-pipe`

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
| `--name` | **Yes** | string | -- | Pipe name or ARN to stop |

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

---

### 9.7 `update-pipe`

Updates a pipe's configuration.

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
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipe name or ARN |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--description` | No | string | None | Updated description |
| `--desired-state` | No | string | None | Updated desired state |
| `--source-parameters` | No | structure | None | Updated source parameters |
| `--enrichment` | No | string | None | Updated enrichment ARN |
| `--enrichment-parameters` | No | structure | None | Updated enrichment parameters |
| `--target` | No | string | None | Updated target ARN |
| `--target-parameters` | No | structure | None | Updated target parameters |
| `--log-configuration` | No | structure | None | Updated log configuration |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "DesiredState": "RUNNING|STOPPED",
    "CurrentState": "UPDATING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```
