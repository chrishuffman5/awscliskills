# Messaging Configuration

CLI namespace: `aws chime-sdk-messaging`

### 10.1 `get-messaging-session-endpoint`

Gets the messaging session endpoint URL for connecting a WebSocket client.

**Synopsis:**
```bash
aws chime-sdk-messaging get-messaging-session-endpoint
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

### 10.2 `get-messaging-streaming-configurations`

Gets the streaming configurations for an AppInstance (for streaming messages to Kinesis).

**Synopsis:**
```bash
aws chime-sdk-messaging get-messaging-streaming-configurations \
    --app-instance-arn <value>
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

### 10.3 `put-messaging-streaming-configurations`

Sets the streaming configurations for an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-messaging put-messaging-streaming-configurations \
    --app-instance-arn <value> \
    --streaming-configurations <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--streaming-configurations` | **Yes** | list | -- | Streaming configurations (1-2) |

**StreamingConfigurations structure:**
```json
[
    {
        "DataType": "Channel|ChannelMessage",
        "ResourceArn": "arn:aws:kinesis:us-east-1:123456789012:stream/my-stream"
    }
]
```

**Output Schema:**
```json
{
    "StreamingConfigurations": []
}
```

---

### 10.4 `delete-messaging-streaming-configurations`

Deletes streaming configurations for an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-messaging delete-messaging-streaming-configurations \
    --app-instance-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output:** None
