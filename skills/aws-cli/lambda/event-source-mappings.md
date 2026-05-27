# Event Source Mappings

### 4.1 `create-event-source-mapping`

Creates a mapping between an event source and a Lambda function. Supported sources: SQS, Kinesis, DynamoDB Streams, Amazon MSK, self-managed Apache Kafka, Amazon MQ, and DocumentDB.

**Synopsis:**
```bash
aws lambda create-event-source-mapping \
    --function-name <value> \
    [--event-source-arn <value>] \
    [--enabled | --no-enabled] \
    [--batch-size <value>] \
    [--maximum-batching-window-in-seconds <value>] \
    [--starting-position <value>] \
    [--starting-position-timestamp <value>] \
    [--parallelization-factor <value>] \
    [--maximum-retry-attempts <value>] \
    [--maximum-record-age-in-seconds <value>] \
    [--bisect-batch-on-function-error | --no-bisect-batch-on-function-error] \
    [--destination-config <value>] \
    [--filter-criteria <value>] \
    [--function-response-types <value>] \
    [--topics <value>] \
    [--queues <value>] \
    [--source-access-configurations <value>] \
    [--self-managed-event-source <value>] \
    [--self-managed-kafka-event-source-config <value>] \
    [--amazon-managed-kafka-event-source-config <value>] \
    [--scaling-config <value>] \
    [--document-db-event-source-config <value>] \
    [--kms-key-arn <value>] \
    [--metrics-config <value>] \
    [--tags <value>] \
    [--tumbling-window-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN |
| `--event-source-arn` | No | string | -- | Event source ARN (Kinesis, DynamoDB, SQS, MSK, MQ, DocumentDB) |
| `--enabled` / `--no-enabled` | No | boolean | `true` | Enable/disable the mapping |
| `--batch-size` | No | integer | varies | Max records per batch. SQS: 10 (1-10000); Kinesis/DynamoDB: 100 (1-10000); MSK/Kafka: 100 (1-10000) |
| `--maximum-batching-window-in-seconds` | No | integer | `0` | Batching window (0-300 seconds) |
| `--starting-position` | Cond. | string | -- | Required for stream sources. Values: `TRIM_HORIZON`, `LATEST`, `AT_TIMESTAMP` |
| `--starting-position-timestamp` | No | timestamp | -- | Timestamp for `AT_TIMESTAMP` starting position |
| `--parallelization-factor` | No | integer | `1` | Concurrent batches per shard (1-10). Kinesis/DynamoDB only |
| `--maximum-retry-attempts` | No | integer | `-1` | Max retries for stream sources (-1 = infinite, 0-10000) |
| `--maximum-record-age-in-seconds` | No | integer | `-1` | Max record age (-1 = infinite, 60-604800) |
| `--bisect-batch-on-function-error` | No | boolean | `false` | Split batch on error (stream sources only) |
| `--destination-config` | No | structure | -- | Failed record destination. Shorthand: `OnFailure={Destination=string}` |
| `--filter-criteria` | No | structure | -- | Event filter patterns. JSON: `{"Filters":[{"Pattern":"string"}]}` |
| `--function-response-types` | No | list | -- | Values: `ReportBatchItemFailures` |
| `--topics` | No | list | -- | Kafka topic names |
| `--queues` | No | list | -- | MQ queue names |
| `--source-access-configurations` | No | list | -- | Auth config for Kafka/MQ. Shorthand: `Type=string,URI=string` |
| `--self-managed-event-source` | No | structure | -- | Self-managed Kafka bootstrap servers |
| `--scaling-config` | No | structure | -- | SQS scaling. Shorthand: `MaximumConcurrency=integer` (2-1000) |
| `--document-db-event-source-config` | No | structure | -- | DocumentDB config. Shorthand: `DatabaseName=string,CollectionName=string,FullDocument=UpdateLookup\|Default` |
| `--kms-key-arn` | No | string | -- | KMS key for encrypting filter criteria |
| `--metrics-config` | No | structure | -- | Metrics config. Values: `EventCount`, `ErrorCount` |
| `--tags` | No | map | -- | Tags for the event source mapping |
| `--tumbling-window-in-seconds` | No | integer | -- | Tumbling window (0-900). Kinesis/DynamoDB only |

**Output Schema:**
```json
{
    "UUID": "string",
    "EventSourceArn": "string",
    "FunctionArn": "string",
    "State": "Creating|Enabling|Enabled|Disabling|Disabled|Updating|Deleting",
    "StateTransitionReason": "string",
    "LastModified": "timestamp",
    "LastProcessingResult": "string",
    "BatchSize": "integer",
    "MaximumBatchingWindowInSeconds": "integer",
    "ParallelizationFactor": "integer",
    "StartingPosition": "TRIM_HORIZON|LATEST|AT_TIMESTAMP",
    "StartingPositionTimestamp": "timestamp",
    "MaximumRecordAgeInSeconds": "integer",
    "BisectBatchOnFunctionError": true|false,
    "MaximumRetryAttempts": "integer",
    "TumblingWindowInSeconds": "integer",
    "FunctionResponseTypes": ["ReportBatchItemFailures"],
    "Topics": ["string"],
    "Queues": ["string"],
    "SourceAccessConfigurations": [
        {"Type": "string", "URI": "string"}
    ],
    "SelfManagedEventSource": {
        "Endpoints": {"KAFKA_BOOTSTRAP_SERVERS": ["string"]}
    },
    "FilterCriteria": {
        "Filters": [{"Pattern": "string"}]
    },
    "DestinationConfig": {
        "OnSuccess": {"Destination": "string"},
        "OnFailure": {"Destination": "string"}
    },
    "ScalingConfig": {"MaximumConcurrency": "integer"},
    "DocumentDBEventSourceConfig": {
        "DatabaseName": "string",
        "CollectionName": "string",
        "FullDocument": "UpdateLookup|Default"
    },
    "KMSKeyArn": "string",
    "EventSourceMappingArn": "string",
    "MetricsConfig": {"Metrics": ["EventCount"]}
}
```

---

### 4.2 `get-event-source-mapping`

Returns details about an event source mapping.

**Synopsis:**
```bash
aws lambda get-event-source-mapping \
    --uuid <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--uuid` | **Yes** | string | -- | Event source mapping UUID |

**Output Schema:** Same as `create-event-source-mapping`.

---

### 4.3 `list-event-source-mappings`

Lists event source mappings. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-event-source-mappings \
    [--event-source-arn <value>] \
    [--function-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-source-arn` | No | string | -- | Filter by event source ARN |
| `--function-name` | No | string | -- | Filter by function name or ARN |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "EventSourceMappings": [
        { "...same as create-event-source-mapping output..." }
    ],
    "NextMarker": "string"
}
```

---

### 4.4 `update-event-source-mapping`

Updates an event source mapping. Only the fields you specify are updated.

**Synopsis:**
```bash
aws lambda update-event-source-mapping \
    --uuid <value> \
    [--function-name <value>] \
    [--enabled | --no-enabled] \
    [--batch-size <value>] \
    [--maximum-batching-window-in-seconds <value>] \
    [--parallelization-factor <value>] \
    [--maximum-retry-attempts <value>] \
    [--maximum-record-age-in-seconds <value>] \
    [--bisect-batch-on-function-error | --no-bisect-batch-on-function-error] \
    [--destination-config <value>] \
    [--filter-criteria <value>] \
    [--function-response-types <value>] \
    [--source-access-configurations <value>] \
    [--scaling-config <value>] \
    [--document-db-event-source-config <value>] \
    [--kms-key-arn <value>] \
    [--metrics-config <value>] \
    [--tumbling-window-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--uuid` | **Yes** | string | -- | Event source mapping UUID |
| `--function-name` | No | string | -- | Function name or ARN to re-target |
| Other params | No | -- | -- | Same as `create-event-source-mapping` (only updated fields need to be specified) |

**Output Schema:** Same as `create-event-source-mapping`.

---

### 4.5 `delete-event-source-mapping`

Deletes an event source mapping.

**Synopsis:**
```bash
aws lambda delete-event-source-mapping \
    --uuid <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--uuid` | **Yes** | string | -- | Event source mapping UUID |

**Output Schema:** Same as `create-event-source-mapping` (returns final state).

---
