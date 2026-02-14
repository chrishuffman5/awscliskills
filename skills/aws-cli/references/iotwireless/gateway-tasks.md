# Gateway Tasks

### 3.1 `create-wireless-gateway-task`

Creates a task for a wireless gateway (e.g., firmware update).

**Synopsis:**
```bash
aws iotwireless create-wireless-gateway-task \
    --id <value> \
    --wireless-gateway-task-definition-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless gateway ID (max 256 chars) |
| `--wireless-gateway-task-definition-id` | **Yes** | string | -- | Task definition ID (max 36 chars) |

**Output Schema:**
```json
{
    "WirelessGatewayTaskDefinitionId": "string",
    "Status": "PENDING|IN_PROGRESS|FIRST_RETRY|SECOND_RETRY|COMPLETED|FAILED"
}
```

---

### 3.2 `get-wireless-gateway-task`

Gets information about a wireless gateway task.

**Synopsis:**
```bash
aws iotwireless get-wireless-gateway-task \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless gateway ID |

**Output Schema:**
```json
{
    "WirelessGatewayId": "string",
    "WirelessGatewayTaskDefinitionId": "string",
    "LastUplinkReceivedAt": "string",
    "TaskCreatedAt": "string",
    "Status": "PENDING|IN_PROGRESS|FIRST_RETRY|SECOND_RETRY|COMPLETED|FAILED"
}
```

---

### 3.3 `delete-wireless-gateway-task`

Deletes a wireless gateway task.

**Synopsis:**
```bash
aws iotwireless delete-wireless-gateway-task \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless gateway ID |

**Output:** None

---

### 3.4 `create-wireless-gateway-task-definition`

Creates a gateway task definition for firmware updates.

**Synopsis:**
```bash
aws iotwireless create-wireless-gateway-task-definition \
    --auto-create-tasks <value> \
    [--name <value>] \
    [--update <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-create-tasks` | **Yes** | boolean | -- | Whether to auto-create tasks for gateways |
| `--name` | No | string | None | Task definition name (max 2048 chars) |
| `--update` | No | structure | None | Update configuration with firmware versions |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (max 200) |

**Update structure:**
```json
{
    "UpdateDataSource": "string",
    "UpdateDataRole": "string",
    "LoRaWAN": {
        "UpdateSignature": "string",
        "SigKeyCrc": "long",
        "CurrentVersion": {
            "PackageVersion": "string",
            "Model": "string",
            "Station": "string"
        },
        "UpdateVersion": {
            "PackageVersion": "string",
            "Model": "string",
            "Station": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string"
}
```

---

### 3.5 `get-wireless-gateway-task-definition`

Gets a wireless gateway task definition.

**Synopsis:**
```bash
aws iotwireless get-wireless-gateway-task-definition \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Task definition ID |

**Output Schema:**
```json
{
    "AutoCreateTasks": "boolean",
    "Name": "string",
    "Update": {
        "UpdateDataSource": "string",
        "UpdateDataRole": "string",
        "LoRaWAN": {}
    },
    "Arn": "string"
}
```

---

### 3.6 `delete-wireless-gateway-task-definition`

Deletes a wireless gateway task definition.

**Synopsis:**
```bash
aws iotwireless delete-wireless-gateway-task-definition \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Task definition ID |

**Output:** None

---

### 3.7 `list-wireless-gateway-task-definitions`

Lists wireless gateway task definitions. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-wireless-gateway-task-definitions \
    [--max-results <value>] \
    [--next-token <value>] \
    [--task-definition-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (0-1) |
| `--next-token` | No | string | None | Pagination token |
| `--task-definition-type` | No | string | None | `UPDATE` |

**Output Schema:**
```json
{
    "NextToken": "string",
    "TaskDefinitions": [
        {
            "Id": "string",
            "LoRaWAN": {
                "CurrentVersion": {
                    "PackageVersion": "string",
                    "Model": "string",
                    "Station": "string"
                },
                "UpdateVersion": {}
            },
            "Arn": "string"
        }
    ]
}
```
