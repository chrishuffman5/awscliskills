# Destinations

### 4.1 `create-destination`

Creates a destination that routes device messages to an AWS IoT rule or MQTT topic.

**Synopsis:**
```bash
aws iotwireless create-destination \
    --name <value> \
    --expression-type <value> \
    --expression <value> \
    --role-arn <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Destination name (max 128 chars, pattern: `[a-zA-Z0-9-_]+`) |
| `--expression-type` | **Yes** | string | -- | `RuleName` or `MqttTopic` |
| `--expression` | **Yes** | string | -- | Rule name or MQTT topic (max 2048 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for authorization |
| `--description` | No | string | None | Description (max 2048 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string"
}
```

---

### 4.2 `get-destination`

Retrieves information about a destination.

**Synopsis:**
```bash
aws iotwireless get-destination \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Destination name |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "Expression": "string",
    "ExpressionType": "RuleName|MqttTopic",
    "Description": "string",
    "RoleArn": "string"
}
```

---

### 4.3 `list-destinations`

Lists destinations. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-destinations \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextToken": "string",
    "DestinationList": [
        {
            "Arn": "string",
            "Name": "string",
            "ExpressionType": "RuleName|MqttTopic",
            "Expression": "string",
            "Description": "string",
            "RoleArn": "string"
        }
    ]
}
```

---

### 4.4 `update-destination`

Updates a destination.

**Synopsis:**
```bash
aws iotwireless update-destination \
    --name <value> \
    [--expression-type <value>] \
    [--expression <value>] \
    [--description <value>] \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Destination name |
| `--expression-type` | No | string | None | `RuleName` or `MqttTopic` |
| `--expression` | No | string | None | Updated rule name or topic |
| `--description` | No | string | None | Updated description |
| `--role-arn` | No | string | None | Updated IAM role ARN |

**Output:** None

---

### 4.5 `delete-destination`

Deletes a destination.

**Synopsis:**
```bash
aws iotwireless delete-destination \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Destination name |

**Output:** None
