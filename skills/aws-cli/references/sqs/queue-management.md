# Queue Management

### 1.1 `create-queue`

Creates a new standard or FIFO queue. Queue names are case-sensitive and limited to 80 characters. FIFO queue names must end with `.fifo`.

**Synopsis:**
```bash
aws sqs create-queue \
    --queue-name <value> \
    [--attributes <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-name` | **Yes** | string | -- | Queue name (up to 80 chars). Alphanumeric, hyphens, underscores. FIFO queues must end with `.fifo`. Case-sensitive. |
| `--attributes` | No | map | -- | Queue attributes as key-value pairs (see attribute list below) |
| `--tags` | No | map | -- | Cost allocation tags. Max 50 tags. Case-sensitive. Shorthand: `Key1=Value1,Key2=Value2` |

**Queue Attributes (for `--attributes`):**

| Attribute | Type | Default | Description |
|-----------|------|---------|-------------|
| `DelaySeconds` | integer | `0` | Message delivery delay (0-900 seconds) |
| `MaximumMessageSize` | integer | `262144` | Max message size in bytes (1,024-1,048,576) |
| `MessageRetentionPeriod` | integer | `345600` | Retention in seconds (60-1,209,600). Default 4 days |
| `Policy` | string | -- | Queue policy (IAM policy JSON) |
| `ReceiveMessageWaitTimeSeconds` | integer | `0` | Long-poll wait time (0-20 seconds) |
| `VisibilityTimeout` | integer | `30` | Visibility timeout in seconds (0-43,200) |
| `RedrivePolicy` | JSON string | -- | DLQ config: `{"deadLetterTargetArn":"<arn>","maxReceiveCount":"<n>"}` |
| `RedriveAllowPolicy` | JSON string | -- | DLQ redrive permissions: `{"redrivePermission":"<value>","sourceQueueArns":["<arn>"]}` |
| `KmsMasterKeyId` | string | -- | KMS key ID for server-side encryption |
| `KmsDataKeyReusePeriodSeconds` | integer | `300` | KMS data key reuse period (60-86,400 seconds) |
| `SqsManagedSseEnabled` | boolean | -- | Enable SQS-managed server-side encryption |
| `FifoQueue` | boolean | `false` | Create a FIFO queue (cannot be changed after creation) |
| `ContentBasedDeduplication` | boolean | `false` | Enable content-based deduplication (FIFO only) |
| `DeduplicationScope` | string | `queue` | `messageGroup` or `queue` (high-throughput FIFO) |
| `FifoThroughputLimit` | string | `perQueue` | `perQueue` or `perMessageGroupId` (high-throughput FIFO) |

**Output Schema:**
```json
{
    "QueueUrl": "string"
}
```

---

### 1.2 `delete-queue`

Deletes the queue specified by the URL. All messages in the queue are permanently lost. Must wait 60 seconds before creating a queue with the same name.

**Synopsis:**
```bash
aws sqs delete-queue \
    --queue-url <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue to delete. Case-sensitive. |

**Output:** None

---

### 1.3 `list-queues`

Returns a list of queue URLs. **Paginated operation** (max 1,000 per response).

**Synopsis:**
```bash
aws sqs list-queues \
    [--queue-name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-name-prefix` | No | string | -- | Filter queues by name prefix. Case-sensitive. |
| `--starting-token` | No | string | -- | Pagination token from previous response |
| `--page-size` | No | integer | -- | Number of items per service call |
| `--max-items` | No | integer | 1000 | Maximum total items to return |

**Output Schema:**
```json
{
    "QueueUrls": [
        "string"
    ],
    "NextToken": "string"
}
```

---

### 1.4 `get-queue-url`

Returns the URL of an existing queue by name.

**Synopsis:**
```bash
aws sqs get-queue-url \
    --queue-name <value> \
    [--queue-owner-aws-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-name` | **Yes** | string | -- | Queue name (up to 80 chars). Case-sensitive. |
| `--queue-owner-aws-account-id` | No | string | caller's account | AWS account ID of queue owner. Required for cross-account access. |

**Output Schema:**
```json
{
    "QueueUrl": "string"
}
```

---

### 1.5 `get-queue-attributes`

Gets attributes for the specified queue.

**Synopsis:**
```bash
aws sqs get-queue-attributes \
    --queue-url <value> \
    [--attribute-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--attribute-names` | No | list | -- | List of attribute names to retrieve. Use `All` for all attributes. |

**Queryable Attribute Names:**
`All`, `Policy`, `VisibilityTimeout`, `MaximumMessageSize`, `MessageRetentionPeriod`, `ApproximateNumberOfMessages`, `ApproximateNumberOfMessagesNotVisible`, `ApproximateNumberOfMessagesDelayed`, `CreatedTimestamp`, `LastModifiedTimestamp`, `QueueArn`, `DelaySeconds`, `ReceiveMessageWaitTimeSeconds`, `RedrivePolicy`, `RedriveAllowPolicy`, `FifoQueue`, `ContentBasedDeduplication`, `KmsMasterKeyId`, `KmsDataKeyReusePeriodSeconds`, `SqsManagedSseEnabled`, `DeduplicationScope`, `FifoThroughputLimit`

**Output Schema:**
```json
{
    "Attributes": {
        "string": "string"
    }
}
```

---

### 1.6 `set-queue-attributes`

Sets the value of one or more queue attributes. Changes propagate in up to 60 seconds. `MessageRetentionPeriod` changes can take up to 15 minutes.

**Synopsis:**
```bash
aws sqs set-queue-attributes \
    --queue-url <value> \
    --attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--attributes` | **Yes** | map | -- | Attribute name-value pairs to set |

**Settable Attributes:**

| Attribute | Range | Default | Description |
|-----------|-------|---------|-------------|
| `DelaySeconds` | 0-900 | 0 | Message delivery delay |
| `MaximumMessageSize` | 1,024-1,048,576 | 262,144 | Max message size in bytes |
| `MessageRetentionPeriod` | 60-1,209,600 | 345,600 | Retention in seconds |
| `Policy` | -- | -- | Queue policy (IAM policy document) |
| `ReceiveMessageWaitTimeSeconds` | 0-20 | 0 | Long-poll wait time |
| `VisibilityTimeout` | 0-43,200 | 30 | Visibility timeout in seconds |
| `RedrivePolicy` | -- | -- | DLQ config JSON |
| `RedriveAllowPolicy` | -- | -- | DLQ redrive permissions JSON |
| `KmsMasterKeyId` | -- | -- | KMS key ID for SSE |
| `KmsDataKeyReusePeriodSeconds` | 60-86,400 | 300 | KMS data key reuse period |
| `SqsManagedSseEnabled` | true/false | -- | SQS-managed encryption |
| `ContentBasedDeduplication` | true/false | false | FIFO deduplication |
| `DeduplicationScope` | messageGroup/queue | queue | High-throughput FIFO |
| `FifoThroughputLimit` | perQueue/perMessageGroupId | perQueue | High-throughput FIFO |

**Output:** None

---

### 1.7 `purge-queue`

Deletes all messages in the specified queue. Deletion takes up to 60 seconds.

**Synopsis:**
```bash
aws sqs purge-queue \
    --queue-url <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue to purge. Case-sensitive. |

**Output:** None
