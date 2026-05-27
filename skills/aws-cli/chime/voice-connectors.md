# Voice Connectors

CLI namespace: `aws chime-sdk-voice`

### 11.1 `create-voice-connector`

Creates an Amazon Chime SDK Voice Connector for SIP-based calling.

**Synopsis:**
```bash
aws chime-sdk-voice create-voice-connector \
    --name <value> \
    --require-encryption | --no-require-encryption \
    [--aws-region <value>] \
    [--tags <value>] \
    [--integration-type <value>] \
    [--network-type <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name (1-256 chars) |
| `--require-encryption` | **Yes** | boolean | -- | Enable TLS encryption |
| `--aws-region` | No | string | us-east-1 | AWS region for the connector |
| `--tags` | No | list | None | Tags (1-50) |
| `--integration-type` | No | string | None | `CONNECT_CALL_TRANSFER_CONNECTOR` or `CONNECT_ANALYTICS_CONNECTOR` |
| `--network-type` | No | string | None | `IPV4_ONLY` or `DUAL_STACK` |

**Output Schema:**
```json
{
    "VoiceConnector": {
        "VoiceConnectorId": "string",
        "AwsRegion": "string",
        "Name": "string",
        "OutboundHostName": "string",
        "RequireEncryption": "boolean",
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "VoiceConnectorArn": "string",
        "IntegrationType": "string",
        "NetworkType": "string"
    }
}
```

---

### 11.2 `get-voice-connector` / `list-voice-connectors` / `update-voice-connector` / `delete-voice-connector`

**Synopsis:**
```bash
aws chime-sdk-voice get-voice-connector --voice-connector-id <value>

aws chime-sdk-voice list-voice-connectors [--next-token <value>] [--max-results <value>]

aws chime-sdk-voice update-voice-connector --voice-connector-id <value> --name <value> --require-encryption | --no-require-encryption

aws chime-sdk-voice delete-voice-connector --voice-connector-id <value>
```

---

### 11.3 `create-voice-connector-group`

Creates a Voice Connector group for high availability across regions.

**Synopsis:**
```bash
aws chime-sdk-voice create-voice-connector-group \
    --name <value> \
    [--voice-connector-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name (1-256 chars) |
| `--voice-connector-items` | No | list | None | Voice connectors with priority |

**VoiceConnectorItems structure:**
```json
[
    {"VoiceConnectorId": "string", "Priority": 1}
]
```

**Output Schema:**
```json
{
    "VoiceConnectorGroup": {
        "VoiceConnectorGroupId": "string",
        "Name": "string",
        "VoiceConnectorItems": [],
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "VoiceConnectorGroupArn": "string"
    }
}
```

---

### 11.4 `get-voice-connector-group` / `list-voice-connector-groups` / `update-voice-connector-group` / `delete-voice-connector-group`

**Synopsis:**
```bash
aws chime-sdk-voice get-voice-connector-group --voice-connector-group-id <value>

aws chime-sdk-voice list-voice-connector-groups [--next-token <value>] [--max-results <value>]

aws chime-sdk-voice update-voice-connector-group --voice-connector-group-id <value> --name <value> --voice-connector-items <value>

aws chime-sdk-voice delete-voice-connector-group --voice-connector-group-id <value>
```

---

### 11.5 `list-available-voice-connector-regions`

Lists available AWS regions for Voice Connectors.

**Synopsis:**
```bash
aws chime-sdk-voice list-available-voice-connector-regions
```

**Output Schema:**
```json
{
    "VoiceConnectorRegions": ["us-east-1", "us-west-2", "eu-central-1", "..."]
}
```
