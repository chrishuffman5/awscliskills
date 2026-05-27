# Channel Flows

CLI namespace: `aws chime-sdk-messaging`

### 9.1 `create-channel-flow`

Creates a channel flow. Channel flows are processor pipelines that run on channel messages (e.g., for content moderation).

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel-flow \
    --app-instance-arn <value> \
    --name <value> \
    --processors <value> \
    [--tags <value>] \
    [--client-request-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--name` | **Yes** | string | -- | Channel flow name (1-256 chars) |
| `--processors` | **Yes** | list | -- | Processor pipeline (1-3 processors) |
| `--tags` | No | list | None | Tags (1-50) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Processors structure:**
```json
[
    {
        "Name": "string",
        "Configuration": {
            "Lambda": {
                "ResourceArn": "string",
                "InvocationType": "ASYNC"
            }
        },
        "ExecutionOrder": 1,
        "FallbackAction": "CONTINUE|ABORT"
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

### 9.2 `describe-channel-flow` / `list-channel-flows` / `update-channel-flow` / `delete-channel-flow`

**Synopsis:**
```bash
aws chime-sdk-messaging describe-channel-flow --channel-flow-arn <value>

aws chime-sdk-messaging list-channel-flows --app-instance-arn <value> [--max-results <value>] [--next-token <value>]

aws chime-sdk-messaging update-channel-flow --channel-flow-arn <value> --name <value> --processors <value>

aws chime-sdk-messaging delete-channel-flow --channel-flow-arn <value>
```

---

### 9.3 `associate-channel-flow` / `disassociate-channel-flow`

Associate or disassociate a channel flow with a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging associate-channel-flow \
    --channel-arn <value> --channel-flow-arn <value> --chime-bearer <value>

aws chime-sdk-messaging disassociate-channel-flow \
    --channel-arn <value> --channel-flow-arn <value> --chime-bearer <value>
```

**Output:** None

---

### 9.4 `list-channels-associated-with-channel-flow`

Lists channels using a specific channel flow. **Paginated.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-channels-associated-with-channel-flow \
    --channel-flow-arn <value> [--max-results <value>] [--next-token <value>]
```

---

### 9.5 `channel-flow-callback`

Handles a callback from a channel flow processor Lambda function.

**Synopsis:**
```bash
aws chime-sdk-messaging channel-flow-callback \
    --channel-arn <value> \
    --callback-id <value> \
    --channel-message <value> \
    [--delete-resource]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--callback-id` | **Yes** | string | -- | Callback ID (idempotency token) |
| `--channel-message` | **Yes** | structure | -- | Processed message |
| `--delete-resource` | No | boolean | None | Delete the message |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "CallbackId": "string"
}
```
