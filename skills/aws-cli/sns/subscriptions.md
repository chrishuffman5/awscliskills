# Subscriptions

### 2.1 `subscribe`

Subscribes an endpoint to a topic. For protocols requiring confirmation (email, HTTP), the subscription remains pending until confirmed.

**Synopsis:**
```bash
aws sns subscribe \
    --topic-arn <value> \
    --protocol <value> \
    [--notification-endpoint <value>] \
    [--attributes <value>] \
    [--return-subscription-arn | --no-return-subscription-arn] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic to subscribe to |
| `--protocol` | **Yes** | string | -- | Protocol: `http`, `https`, `email`, `email-json`, `sms`, `sqs`, `application`, `lambda`, `firehose` |
| `--notification-endpoint` | No | string | None | Endpoint to receive notifications. Format varies by protocol: URL for http/https, email for email, phone for sms, ARN for sqs/application/lambda/firehose |
| `--attributes` | No | map | None | Subscription attributes: `DeliveryPolicy`, `FilterPolicy`, `FilterPolicyScope`, `RawMessageDelivery`, `RedrivePolicy`, `SubscriptionRoleArn` |
| `--return-subscription-arn` | No | boolean | false | Return subscription ARN even if not yet confirmed |

**Output Schema:**
```json
{
    "SubscriptionArn": "string"
}
```

> **Note:** For unconfirmed subscriptions, `SubscriptionArn` is `"pending confirmation"` unless `--return-subscription-arn` is `true`.

---

### 2.2 `unsubscribe`

Deletes a subscription. Rate limit: 100 TPS.

**Synopsis:**
```bash
aws sns unsubscribe \
    --subscription-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-arn` | **Yes** | string | -- | ARN of the subscription to delete |

**Output Schema:** None

---

### 2.3 `confirm-subscription`

Verifies an endpoint owner's intent to receive messages by validating the token sent during `subscribe`.

**Synopsis:**
```bash
aws sns confirm-subscription \
    --topic-arn <value> \
    --token <value> \
    [--authenticate-on-unsubscribe <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic |
| `--token` | **Yes** | string | -- | Short-lived token sent to the endpoint during subscribe |
| `--authenticate-on-unsubscribe` | No | string | None | If `true`, requires AWS authentication to unsubscribe |

**Output Schema:**
```json
{
    "SubscriptionArn": "string"
}
```

---

### 2.4 `list-subscriptions`

Lists all subscriptions in the account. **Paginated operation** (max 100 per page). Rate limit: 30 TPS.

**Synopsis:**
```bash
aws sns list-subscriptions \
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
    "Subscriptions": [
        {
            "SubscriptionArn": "string",
            "Owner": "string",
            "Protocol": "string",
            "Endpoint": "string",
            "TopicArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `list-subscriptions-by-topic`

Lists subscriptions for a specific topic. **Paginated operation** (max 100 per page). Rate limit: 30 TPS.

**Synopsis:**
```bash
aws sns list-subscriptions-by-topic \
    --topic-arn <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--no-paginate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "Subscriptions": [
        {
            "SubscriptionArn": "string",
            "Owner": "string",
            "Protocol": "string",
            "Endpoint": "string",
            "TopicArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `get-subscription-attributes`

Returns all attributes of a subscription.

**Synopsis:**
```bash
aws sns get-subscription-attributes \
    --subscription-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-arn` | **Yes** | string | -- | ARN of the subscription |

**Output Schema:**
```json
{
    "Attributes": {
        "SubscriptionArn": "string",
        "TopicArn": "string",
        "Owner": "string",
        "Protocol": "string",
        "Endpoint": "string",
        "ConfirmationWasAuthenticated": "true|false",
        "PendingConfirmation": "true|false",
        "DeliveryPolicy": "string (JSON)",
        "EffectiveDeliveryPolicy": "string (JSON)",
        "FilterPolicy": "string (JSON)",
        "FilterPolicyScope": "MessageAttributes|MessageBody",
        "RawMessageDelivery": "true|false",
        "RedrivePolicy": "string (JSON)",
        "SubscriptionRoleArn": "string"
    }
}
```

---

### 2.7 `set-subscription-attributes`

Sets an attribute of a subscription to a new value.

**Synopsis:**
```bash
aws sns set-subscription-attributes \
    --subscription-arn <value> \
    --attribute-name <value> \
    [--attribute-value <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-arn` | **Yes** | string | -- | ARN of the subscription |
| `--attribute-name` | **Yes** | string | -- | Attribute to set (see supported list below) |
| `--attribute-value` | No | string | None | New value for the attribute (JSON format where applicable) |

**Supported Attribute Names:**

| Attribute | Description |
|-----------|-------------|
| `DeliveryPolicy` | Retry policy for HTTP/S endpoints (JSON) |
| `FilterPolicy` | Message filtering policy (JSON). Set to `{}` to remove |
| `FilterPolicyScope` | `MessageAttributes` (default) or `MessageBody` |
| `RawMessageDelivery` | `true` or `false`. Enables raw message delivery to SQS/HTTP |
| `RedrivePolicy` | Dead-letter queue policy (JSON). Format: `{"deadLetterTargetArn":"arn:aws:sqs:..."}` |
| `SubscriptionRoleArn` | IAM role ARN (Firehose subscriptions only) |

**Output Schema:** None
