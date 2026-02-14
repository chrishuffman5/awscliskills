# Messaging Configuration

Commands from the `aws chime-sdk-messaging` service.

### 11.1 `get-messaging-session-endpoint`

Gets the endpoint for messaging session connections.

**Synopsis:**
```bash
aws chime-sdk-messaging get-messaging-session-endpoint \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "Endpoint": {
        "Url": "string"
    }
}
```

---

### 11.2 `get-messaging-streaming-configurations`

Gets the streaming configuration for an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-messaging get-messaging-streaming-configurations \
    --app-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output Schema:**
```json
{
    "StreamingConfigurations": [
        {
            "DataType": "Channel|ChannelMessage",
            "ResourceArn": "string"
        }
    ]
}
```

---

### 11.3 `put-messaging-streaming-configurations`

Sets the streaming configuration for an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-messaging put-messaging-streaming-configurations \
    --app-instance-arn <value> \
    --streaming-configurations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--streaming-configurations` | **Yes** | list | -- | Streaming configurations (1-2) |

**StreamingConfigurations:**
```json
[
    {
        "DataType": "Channel|ChannelMessage (required)",
        "ResourceArn": "string (required, Kinesis stream ARN)"
    }
]
```

**Output Schema:**
```json
{
    "StreamingConfigurations": [
        {
            "DataType": "Channel|ChannelMessage",
            "ResourceArn": "string"
        }
    ]
}
```

---

### 11.4 `delete-messaging-streaming-configurations`

Deletes the streaming configuration for an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-messaging delete-messaging-streaming-configurations \
    --app-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output:** None
