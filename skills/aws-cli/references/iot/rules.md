# Rules

## 4.1 `create-topic-rule`

Creates a topic rule to route messages to AWS services based on SQL queries.

**Synopsis:**
```bash
aws iot create-topic-rule \
    --rule-name <value> \
    --topic-rule-payload <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Rule name (1-128 chars, pattern `^[a-zA-Z0-9_]+$`) |
| `--topic-rule-payload` | **Yes** | structure | -- | Rule payload with SQL, actions, and options |
| `--tags` | No | string | None | Tags (format: `key1=value1&key2=value2`) |

**TopicRulePayload:**
```json
{
    "sql": "string",
    "description": "string",
    "actions": [
        {
            "dynamoDB": {},
            "dynamoDBv2": {},
            "lambda": {"functionArn": "string"},
            "sns": {"targetArn": "string", "roleArn": "string", "messageFormat": "RAW|JSON"},
            "sqs": {"roleArn": "string", "queueUrl": "string", "useBase64": "boolean"},
            "kinesis": {"roleArn": "string", "streamName": "string", "partitionKey": "string"},
            "republish": {"roleArn": "string", "topic": "string", "qos": "integer"},
            "s3": {"roleArn": "string", "bucketName": "string", "key": "string"},
            "firehose": {"roleArn": "string", "deliveryStreamName": "string"},
            "cloudwatchMetric": {},
            "cloudwatchAlarm": {},
            "cloudwatchLogs": {"roleArn": "string", "logGroupName": "string"},
            "elasticsearch": {},
            "iotAnalytics": {"channelArn": "string", "channelName": "string", "roleArn": "string"},
            "iotEvents": {"inputName": "string", "messageId": "string", "roleArn": "string"},
            "iotSiteWise": {},
            "stepFunctions": {"executionNamePrefix": "string", "stateMachineName": "string", "roleArn": "string"},
            "timestream": {},
            "http": {"url": "string", "confirmationUrl": "string", "headers": []},
            "kafka": {},
            "openSearch": {},
            "location": {}
        }
    ],
    "ruleDisabled": "boolean",
    "awsIotSqlVersion": "string",
    "errorAction": {}
}
```

**Output:** None

---

## 4.2 `get-topic-rule`

Gets a topic rule.

**Synopsis:**
```bash
aws iot get-topic-rule \
    --rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Rule name |

**Output Schema:**
```json
{
    "ruleArn": "string",
    "rule": {
        "ruleName": "string",
        "sql": "string",
        "description": "string",
        "createdAt": "timestamp",
        "actions": [],
        "ruleDisabled": "boolean",
        "awsIotSqlVersion": "string",
        "errorAction": {}
    }
}
```

---

## 4.3 `list-topic-rules`

Lists topic rules. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-topic-rules \
    [--topic <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--rule-disabled | --no-rule-disabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic` | No | string | None | Filter by topic pattern |
| `--max-results` | No | integer | None | Max results (1-10000) |
| `--next-token` | No | string | None | Pagination token |
| `--rule-disabled` | No | boolean | None | Filter by enabled/disabled |

**Output Schema:**
```json
{
    "rules": [
        {
            "ruleArn": "string",
            "ruleName": "string",
            "topicPattern": "string",
            "createdAt": "timestamp",
            "ruleDisabled": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

## 4.4 `replace-topic-rule`

Replaces a topic rule with a new definition.

**Synopsis:**
```bash
aws iot replace-topic-rule \
    --rule-name <value> \
    --topic-rule-payload <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Rule name |
| `--topic-rule-payload` | **Yes** | structure | -- | New rule payload |

**Output:** None

---

## 4.5 `delete-topic-rule`

Deletes a topic rule.

**Synopsis:**
```bash
aws iot delete-topic-rule \
    --rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Rule name |

**Output:** None

---

## 4.6 `enable-topic-rule`

Enables a topic rule.

**Synopsis:**
```bash
aws iot enable-topic-rule \
    --rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Rule name |

**Output:** None

---

## 4.7 `disable-topic-rule`

Disables a topic rule.

**Synopsis:**
```bash
aws iot disable-topic-rule \
    --rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Rule name |

**Output:** None

---

## 4.8 `create-topic-rule-destination`

Creates a topic rule destination (HTTP URL, VPC, or other).

**Synopsis:**
```bash
aws iot create-topic-rule-destination \
    --destination-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-configuration` | **Yes** | structure | -- | Destination config (httpUrlConfiguration or vpcConfiguration) |

**DestinationConfiguration:**
```json
{
    "httpUrlConfiguration": {
        "confirmationUrl": "string"
    },
    "vpcConfiguration": {
        "subnetIds": ["string"],
        "securityGroups": ["string"],
        "vpcId": "string",
        "roleArn": "string"
    }
}
```

**Output Schema:**
```json
{
    "topicRuleDestination": {
        "arn": "string",
        "status": "ENABLED|IN_PROGRESS|DISABLED|ERROR|DELETING",
        "createdAt": "timestamp",
        "lastUpdatedAt": "timestamp",
        "statusReason": "string",
        "httpUrlProperties": {"confirmationUrl": "string"},
        "vpcProperties": {
            "subnetIds": ["string"],
            "securityGroups": ["string"],
            "vpcId": "string",
            "roleArn": "string"
        }
    }
}
```

---

## 4.9 `get-topic-rule-destination`

Gets a topic rule destination.

**Synopsis:**
```bash
aws iot get-topic-rule-destination \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Destination ARN |

**Output Schema:**
```json
{
    "topicRuleDestination": {
        "arn": "string",
        "status": "ENABLED|IN_PROGRESS|DISABLED|ERROR|DELETING",
        "createdAt": "timestamp",
        "lastUpdatedAt": "timestamp",
        "statusReason": "string",
        "httpUrlProperties": {},
        "vpcProperties": {}
    }
}
```

---

## 4.10 `list-topic-rule-destinations`

Lists topic rule destinations. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-topic-rule-destinations \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "destinationSummaries": [
        {
            "arn": "string",
            "status": "ENABLED|IN_PROGRESS|DISABLED|ERROR|DELETING",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "statusReason": "string",
            "httpUrlSummary": {"confirmationUrl": "string"},
            "vpcDestinationSummary": {}
        }
    ],
    "nextToken": "string"
}
```

---

## 4.11 `update-topic-rule-destination`

Updates a topic rule destination status.

**Synopsis:**
```bash
aws iot update-topic-rule-destination \
    --arn <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Destination ARN |
| `--status` | **Yes** | string | -- | `ENABLED`, `IN_PROGRESS`, `DISABLED` |

**Output:** None

---

## 4.12 `delete-topic-rule-destination`

Deletes a topic rule destination.

**Synopsis:**
```bash
aws iot delete-topic-rule-destination \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Destination ARN |

**Output:** None

---

## 4.13 `confirm-topic-rule-destination`

Confirms a topic rule destination (verifies ownership of HTTP endpoint).

**Synopsis:**
```bash
aws iot confirm-topic-rule-destination \
    --confirmation-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--confirmation-token` | **Yes** | string | -- | Confirmation token from the HTTP endpoint |

**Output:** None
