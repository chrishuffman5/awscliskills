# Shards & Records

### 2.1 `list-shards`

Lists the shards in a data stream. **Paginated operation.**

**Synopsis:**
```bash
aws kinesis list-shards \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    [--exclusive-start-shard-id <value>] \
    [--stream-creation-timestamp <value>] \
    [--shard-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--exclusive-start-shard-id` | No | string | -- | List shards starting after this shard ID |
| `--stream-creation-timestamp` | No | timestamp | -- | Distinguish streams with same name by creation time |
| `--shard-filter` | No | structure | -- | Filter shards by type, ID, or timestamp |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

*Either `--stream-name` or `--stream-arn` must be provided.

**Shard Filter Structure:**
```json
{
    "Type": "AFTER_SHARD_ID|AT_TRIM_HORIZON|FROM_TRIM_HORIZON|AT_LATEST|AT_TIMESTAMP|FROM_TIMESTAMP",
    "ShardId": "string",
    "Timestamp": "timestamp"
}
```

**Output Schema:**
```json
{
    "Shards": [
        {
            "ShardId": "string",
            "ParentShardId": "string",
            "AdjacentParentShardId": "string",
            "HashKeyRange": {
                "StartingHashKey": "string",
                "EndingHashKey": "string"
            },
            "SequenceNumberRange": {
                "StartingSequenceNumber": "string",
                "EndingSequenceNumber": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 2.2 `split-shard`

Splits a shard into two new shards. Only supported for provisioned capacity mode. Asynchronous operation.

**Synopsis:**
```bash
aws kinesis split-shard \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --shard-to-split <value> \
    --new-starting-hash-key <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--shard-to-split` | **Yes** | string | -- | Shard ID to split |
| `--new-starting-hash-key` | **Yes** | string | -- | Hash key for the starting position of one of the child shards |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 2.3 `merge-shards`

Merges two adjacent shards into a single shard. Only supported for provisioned capacity mode. Asynchronous operation.

**Synopsis:**
```bash
aws kinesis merge-shards \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --shard-to-merge <value> \
    --adjacent-shard-to-merge <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--shard-to-merge` | **Yes** | string | -- | Shard ID of the first shard to merge |
| `--adjacent-shard-to-merge` | **Yes** | string | -- | Shard ID of the adjacent shard to merge |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 2.4 `update-shard-count`

Updates the shard count of a provisioned data stream. Supports uniform scaling.

**Synopsis:**
```bash
aws kinesis update-shard-count \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --target-shard-count <value> \
    --scaling-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--target-shard-count` | **Yes** | integer | -- | New number of shards (min: 1) |
| `--scaling-type` | **Yes** | string | -- | Scaling type: `UNIFORM_SCALING` |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output Schema:**
```json
{
    "StreamName": "string",
    "CurrentShardCount": "integer",
    "TargetShardCount": "integer",
    "StreamARN": "string"
}
```

---

### 2.5 `get-shard-iterator`

Gets a shard iterator for reading data records from a specific position in a shard. The iterator expires after 5 minutes.

**Synopsis:**
```bash
aws kinesis get-shard-iterator \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --shard-id <value> \
    --shard-iterator-type <value> \
    [--starting-sequence-number <value>] \
    [--timestamp <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--shard-id` | **Yes** | string | -- | ID of the shard to get an iterator for |
| `--shard-iterator-type` | **Yes** | string | -- | `AT_SEQUENCE_NUMBER`, `AFTER_SEQUENCE_NUMBER`, `AT_TIMESTAMP`, `TRIM_HORIZON`, `LATEST` |
| `--starting-sequence-number` | No | string | -- | Sequence number (required for `AT_SEQUENCE_NUMBER` / `AFTER_SEQUENCE_NUMBER`) |
| `--timestamp` | No | timestamp | -- | Timestamp (required for `AT_TIMESTAMP`) |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output Schema:**
```json
{
    "ShardIterator": "string"
}
```

---

### 2.6 `get-records`

Gets data records from a shard using a shard iterator. Rate limit: 5 TPS per shard, max 10 MiB per call.

**Synopsis:**
```bash
aws kinesis get-records \
    --shard-iterator <value> \
    [--limit <value>] \
    [--stream-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--shard-iterator` | **Yes** | string | -- | Shard iterator from `get-shard-iterator` (max 512 chars) |
| `--limit` | No | integer | 10000 | Max records to return (1-10000) |
| `--stream-arn` | No | string | -- | ARN of the stream |

**Output Schema:**
```json
{
    "Records": [
        {
            "SequenceNumber": "string",
            "ApproximateArrivalTimestamp": "timestamp",
            "Data": "blob",
            "PartitionKey": "string",
            "EncryptionType": "NONE|KMS"
        }
    ],
    "NextShardIterator": "string",
    "MillisBehindLatest": "long",
    "ChildShards": [
        {
            "ShardId": "string",
            "ParentShards": ["string"],
            "HashKeyRange": {
                "StartingHashKey": "string",
                "EndingHashKey": "string"
            }
        }
    ]
}
```

---

### 2.7 `put-record`

Writes a single data record into a stream. Max record size: 1 MiB (including partition key).

**Synopsis:**
```bash
aws kinesis put-record \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --data <value> \
    --partition-key <value> \
    [--explicit-hash-key <value>] \
    [--sequence-number-for-ordering <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--data` | **Yes** | blob | -- | Data blob (base64-encoded, max 10 MiB with partition key) |
| `--partition-key` | **Yes** | string | -- | Determines shard placement (1-256 Unicode chars) |
| `--explicit-hash-key` | No | string | -- | Override partition key hashing |
| `--sequence-number-for-ordering` | No | string | -- | Guarantees strictly increasing sequence numbers |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output Schema:**
```json
{
    "ShardId": "string",
    "SequenceNumber": "string",
    "EncryptionType": "NONE|KMS"
}
```

---

### 2.8 `put-records`

Writes multiple data records into a stream in a single call. Max 500 records per call, max 5 MiB total payload.

**Synopsis:**
```bash
aws kinesis put-records \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --records <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--records` | **Yes** | list | -- | Records to write (1-500). Shorthand: `Data=blob,PartitionKey=string,ExplicitHashKey=string ...` |

*Either `--stream-name` or `--stream-arn` must be provided.

**Record Structure:**
```json
{
    "Data": "blob",
    "ExplicitHashKey": "string",
    "PartitionKey": "string"
}
```

**Output Schema:**
```json
{
    "FailedRecordCount": "integer",
    "Records": [
        {
            "SequenceNumber": "string",
            "ShardId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ],
    "EncryptionType": "NONE|KMS"
}
```
