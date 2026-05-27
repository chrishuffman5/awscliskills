# Logging

## 6.1 `describe-logging-options`

Describes the IoT Events logging options.

**Synopsis:**
```bash
aws iotevents describe-logging-options \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "loggingOptions": {
        "roleArn": "string",
        "level": "ERROR|INFO|DEBUG",
        "enabled": "boolean",
        "detectorDebugOptions": [
            {
                "detectorModelName": "string",
                "keyValue": "string"
            }
        ]
    }
}
```

---

## 6.2 `put-logging-options`

Sets the IoT Events logging options.

**Synopsis:**
```bash
aws iotevents put-logging-options \
    --logging-options <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--logging-options` | **Yes** | structure | -- | Logging configuration |

**LoggingOptions:**
```json
{
    "roleArn": "string",
    "level": "ERROR|INFO|DEBUG",
    "enabled": true,
    "detectorDebugOptions": [
        {
            "detectorModelName": "string",
            "keyValue": "string"
        }
    ]
}
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `roleArn` | **Yes** | string | IAM role ARN for CloudWatch Logs (1-2048 chars) |
| `level` | **Yes** | string | Log level: `ERROR`, `INFO`, `DEBUG` |
| `enabled` | **Yes** | boolean | Enable/disable logging |
| `detectorDebugOptions` | No | list | Detector-specific debug logging |

**Output:** None
