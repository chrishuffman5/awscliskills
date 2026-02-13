# Topics

### 1.1 `create-topic`

Creates an SNS topic. Idempotent -- calling with an existing topic name returns that topic's ARN.

**Synopsis:**
```bash
aws sns create-topic \
    --name <value> \
    [--attributes <value>] \
    [--tags <value>] \
    [--data-protection-policy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Topic name (1-256 chars). Alphanumeric, hyphens, underscores. FIFO topics must end with `.fifo` |
| `--attributes` | No | map | None | Topic attributes: `DeliveryPolicy`, `DisplayName`, `Policy`, `TracingConfig`, `KmsMasterKeyId`, `SignatureVersion`, `ContentBasedDeduplication` (FIFO), `FifoThroughputScope` (FIFO), `ArchivePolicy` (FIFO), plus feedback role ARNs for HTTP/Lambda/SQS/Firehose/Application |
| `--tags` | No | list | None | Key-value tags. Key 1-128 chars, Value 0-256 chars. Shorthand: `Key=string,Value=string ...` |
| `--data-protection-policy` | No | string | None | JSON data protection policy document. Max 30,720 chars |

**Output Schema:**
```json
{
    "TopicArn": "string"
}
```

---

### 1.2 `delete-topic`

Deletes a topic and all its subscriptions. Idempotent -- deleting a non-existent topic does not error.

**Synopsis:**
```bash
aws sns delete-topic \
    --topic-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic to delete |

**Output Schema:** None

---

### 1.3 `list-topics`

Lists all topics in the account. **Paginated operation** (max 100 per page).

**Synopsis:**
```bash
aws sns list-topics \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--no-paginate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "Topics": [
        {
            "TopicArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `get-topic-attributes`

Returns all attributes of a topic.

**Synopsis:**
```bash
aws sns get-topic-attributes \
    --topic-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic |

**Output Schema:**
```json
{
    "Attributes": {
        "TopicArn": "string",
        "Owner": "string",
        "Policy": "string (JSON)",
        "DisplayName": "string",
        "SubscriptionsConfirmed": "string",
        "SubscriptionsPending": "string",
        "SubscriptionsDeleted": "string",
        "DeliveryPolicy": "string (JSON)",
        "EffectiveDeliveryPolicy": "string (JSON)",
        "SignatureVersion": "1|2",
        "TracingConfig": "PassThrough|Active",
        "KmsMasterKeyId": "string",
        "FifoTopic": "true|false",
        "ContentBasedDeduplication": "true|false",
        "ArchivePolicy": "string (JSON)",
        "BeginningArchiveTime": "string"
    }
}
```

---

### 1.5 `set-topic-attributes`

Sets an attribute of a topic to a new value.

**Synopsis:**
```bash
aws sns set-topic-attributes \
    --topic-arn <value> \
    --attribute-name <value> \
    [--attribute-value <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic |
| `--attribute-name` | **Yes** | string | -- | Attribute to set (see supported list below) |
| `--attribute-value` | No | string | None | New value for the attribute |

**Supported Attribute Names:**

| Attribute | Description |
|-----------|-------------|
| `DeliveryPolicy` | Retry policy for HTTP/S endpoints (JSON) |
| `DisplayName` | Display name for SMS subscriptions |
| `Policy` | Topic access control policy (JSON) |
| `TracingConfig` | `PassThrough` or `Active` |
| `KmsMasterKeyId` | KMS key ID for server-side encryption |
| `SignatureVersion` | `1` (SHA1, default) or `2` (SHA256) |
| `HTTPSuccessFeedbackRoleArn` | IAM role for HTTP delivery logging |
| `HTTPFailureFeedbackRoleArn` | IAM role for HTTP failure logging |
| `HTTPSuccessFeedbackSampleRate` | 0-100 percentage |
| `LambdaSuccessFeedbackRoleArn` | IAM role for Lambda delivery logging |
| `LambdaFailureFeedbackRoleArn` | IAM role for Lambda failure logging |
| `LambdaSuccessFeedbackSampleRate` | 0-100 percentage |
| `SQSSuccessFeedbackRoleArn` | IAM role for SQS delivery logging |
| `SQSFailureFeedbackRoleArn` | IAM role for SQS failure logging |
| `SQSSuccessFeedbackSampleRate` | 0-100 percentage |
| `FirehoseSuccessFeedbackRoleArn` | IAM role for Firehose delivery logging |
| `FirehoseFailureFeedbackRoleArn` | IAM role for Firehose failure logging |
| `FirehoseSuccessFeedbackSampleRate` | 0-100 percentage |
| `ApplicationSuccessFeedbackRoleArn` | IAM role for push delivery logging |
| `ApplicationFailureFeedbackRoleArn` | IAM role for push failure logging |
| `ApplicationSuccessFeedbackSampleRate` | 0-100 percentage |
| `ArchivePolicy` | FIFO: message archive retention (JSON) |
| `ContentBasedDeduplication` | FIFO: `true` or `false` |
| `FifoThroughputScope` | FIFO: `Topic` (default) or `MessageGroup` |

**Output Schema:** None
