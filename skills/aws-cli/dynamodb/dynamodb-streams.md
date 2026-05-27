# DynamoDB Streams (`aws dynamodbstreams`)

### 7.1 `describe-stream`

Returns information about a stream including the stream ARN, table name, creation time, key schema, and shard details.

**Synopsis:**
```bash
aws dynamodbstreams describe-stream \
    --stream-arn <value> \
    [--limit <value>] \
    [--exclusive-start-shard-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-arn` | **Yes** | string | -- | Stream ARN (37-1024 chars) |
| `--limit` | No | integer | -- | Max shard objects to return (1-100) |
| `--exclusive-start-shard-id` | No | string | -- | Shard ID to start from (use `LastEvaluatedShardId` from previous call) |

**Output Schema:**
```json
{
    "StreamDescription": {
        "StreamArn": "string",
        "StreamLabel": "string",
        "StreamStatus": "ENABLING|ENABLED|DISABLING|DISABLED",
        "StreamViewType": "NEW_IMAGE|OLD_IMAGE|NEW_AND_OLD_IMAGES|KEYS_ONLY",
        "CreationRequestDateTime": "timestamp",
        "TableName": "string",
        "KeySchema": [
            { "AttributeName": "string", "KeyType": "HASH|RANGE" }
        ],
        "Shards": [
            {
                "ShardId": "string",
                "SequenceNumberRange": {
                    "StartingSequenceNumber": "string",
                    "EndingSequenceNumber": "string"
                },
                "ParentShardId": "string"
            }
        ],
        "LastEvaluatedShardId": "string"
    }
}
```

---

### 7.2 `get-shard-iterator`

Returns a shard iterator used to retrieve stream records from a specific shard.

**Synopsis:**
```bash
aws dynamodbstreams get-shard-iterator \
    --stream-arn <value> \
    --shard-id <value> \
    --shard-iterator-type <value> \
    [--sequence-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-arn` | **Yes** | string | -- | Stream ARN (37-1024 chars) |
| `--shard-id` | **Yes** | string | -- | Shard identifier (28-65 chars) |
| `--shard-iterator-type` | **Yes** | string | -- | `TRIM_HORIZON` (oldest), `LATEST` (newest), `AT_SEQUENCE_NUMBER`, `AFTER_SEQUENCE_NUMBER` |
| `--sequence-number` | No | string | -- | Required for `AT_SEQUENCE_NUMBER` and `AFTER_SEQUENCE_NUMBER` types (21-40 chars) |

**Output Schema:**
```json
{
    "ShardIterator": "string"
}
```

---

### 7.3 `get-records`

Retrieves stream records from a shard using a shard iterator.

**Synopsis:**
```bash
aws dynamodbstreams get-records \
    --shard-iterator <value> \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--shard-iterator` | **Yes** | string | -- | Shard iterator from `get-shard-iterator` (1-2048 chars) |
| `--limit` | No | integer | -- | Max records to return (1-1000) |

**Output Schema:**
```json
{
    "Records": [
        {
            "eventID": "string",
            "eventName": "INSERT|MODIFY|REMOVE",
            "eventVersion": "string",
            "eventSource": "aws:dynamodb",
            "awsRegion": "string",
            "dynamodb": {
                "ApproximateCreationDateTime": "timestamp",
                "Keys": { "string": {} },
                "NewImage": { "string": {} },
                "OldImage": { "string": {} },
                "SequenceNumber": "string",
                "SizeBytes": "long",
                "StreamViewType": "NEW_IMAGE|OLD_IMAGE|NEW_AND_OLD_IMAGES|KEYS_ONLY"
            },
            "userIdentity": {
                "PrincipalId": "string",
                "Type": "string"
            }
        }
    ],
    "NextShardIterator": "string"
}
```

---

### 7.4 `list-streams`

Lists all DynamoDB streams, optionally filtered by table name.

**Synopsis:**
```bash
aws dynamodbstreams list-streams \
    [--table-name <value>] \
    [--limit <value>] \
    [--exclusive-start-stream-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | No | string | -- | Filter streams by table name (3-255 chars) |
| `--limit` | No | integer | -- | Max streams to return |
| `--exclusive-start-stream-arn` | No | string | -- | Stream ARN to start from for pagination |

**Output Schema:**
```json
{
    "Streams": [
        {
            "StreamArn": "string",
            "TableName": "string",
            "StreamLabel": "string"
        }
    ],
    "LastEvaluatedStreamArn": "string"
}
```

---
