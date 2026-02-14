# Channel Flows

Commands from the `aws chime-sdk-messaging` service.

### 9.1 `create-channel-flow`

Creates a channel flow (message processing pipeline).

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel-flow \
    --app-instance-arn <value> \
    --processors <value> \
    --name <value> \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--processors` | **Yes** | list | -- | Processor Lambda functions (1-3) |
| `--name` | **Yes** | string | -- | Channel flow name (1-256 chars) |
| `--tags` | No | list | None | Tags (max 50) |
| `--client-request-token` | No | string | Auto | Idempotency token (2-64 chars) |

**Processors:**
```json
[
    {
        "Name": "string (1-256 chars, required)",
        "Configuration": {
            "Lambda": {
                "ResourceArn": "string (15-2048 chars, required)",
                "InvocationType": "ASYNC (required)"
            }
        },
        "ExecutionOrder": "integer (1-3, required)",
        "FallbackAction": "CONTINUE|ABORT (required)"
    }
]
```

**Output Schema:**
```json
{
    "ChannelFlowArn": "string"
}
```

---

### 9.2 `describe-channel-flow`

Describes a channel flow.

**Synopsis:**
```bash
aws chime-sdk-messaging describe-channel-flow \
    --channel-flow-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-flow-arn` | **Yes** | string | -- | Channel flow ARN |

**Output Schema:**
```json
{
    "ChannelFlow": {
        "ChannelFlowArn": "string",
        "Processors": [
            {
                "Name": "string",
                "Configuration": {
                    "Lambda": {
                        "ResourceArn": "string",
                        "InvocationType": "ASYNC"
                    }
                },
                "ExecutionOrder": "integer",
                "FallbackAction": "CONTINUE|ABORT"
            }
        ],
        "Name": "string",
        "CreatedTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp"
    }
}
```

---

### 9.3 `list-channel-flows`

Lists channel flows for an AppInstance. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-channel-flows \
    --app-instance-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ChannelFlows": [
        {
            "ChannelFlowArn": "string",
            "Name": "string",
            "Processors": [{ "..." }]
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `update-channel-flow`

Updates a channel flow's processors and name.

**Synopsis:**
```bash
aws chime-sdk-messaging update-channel-flow \
    --channel-flow-arn <value> \
    --processors <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-flow-arn` | **Yes** | string | -- | Channel flow ARN |
| `--processors` | **Yes** | list | -- | Updated processors (1-3) |
| `--name` | **Yes** | string | -- | Updated name (1-256 chars) |

**Output Schema:**
```json
{
    "ChannelFlowArn": "string"
}
```

---

### 9.5 `delete-channel-flow`

Deletes a channel flow.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-flow-arn` | **Yes** | string | -- | Channel flow ARN |

**Output:** None

---

### 9.6 `associate-channel-flow`

Associates a channel flow with a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging associate-channel-flow \
    --channel-arn <value> \
    --channel-flow-arn <value> \
    --chime-bearer <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--channel-flow-arn` | **Yes** | string | -- | Channel flow ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output:** None

---

### 9.7 `disassociate-channel-flow`

Removes a channel flow from a channel.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--channel-flow-arn` | **Yes** | string | -- | Channel flow ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output:** None

---

### 9.8 `list-channels-associated-with-channel-flow`

Lists channels associated with a channel flow. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-flow-arn` | **Yes** | string | -- | Channel flow ARN |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Channels": [
        {
            "Name": "string",
            "ChannelArn": "string",
            "Mode": "UNRESTRICTED|RESTRICTED",
            "Privacy": "PUBLIC|PRIVATE",
            "Metadata": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.9 `channel-flow-callback`

Callback for a channel flow processor Lambda to send the processed message back.

**Synopsis:**
```bash
aws chime-sdk-messaging channel-flow-callback \
    --callback-id <value> \
    --channel-arn <value> \
    --channel-message <value> \
    [--delete-resource | --no-delete-resource] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--callback-id` | **Yes** | string | -- | Callback ID from Lambda invocation |
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--channel-message` | **Yes** | structure | -- | Processed message |
| `--delete-resource` | No | boolean | None | Whether to delete the message |

**ChannelMessage:**
```json
{
    "MessageId": "string (required)",
    "Content": "string",
    "Metadata": "string",
    "PushNotification": {
        "Title": "string",
        "Body": "string",
        "Type": "DEFAULT|VOIP"
    },
    "MessageAttributes": {},
    "SubChannelId": "string",
    "ContentType": "string"
}
```

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "CallbackId": "string"
}
```
