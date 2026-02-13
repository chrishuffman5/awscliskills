# Connectors v2

### 10.1 `create-connector-v2`

Creates a v2 connector for integrating third-party findings.

**Synopsis:**
```bash
aws securityhub create-connector-v2 \
    --name <value> \
    --provider <value> \
    [--description <value>] \
    [--kms-key-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connector name |
| `--provider` | **Yes** | structure | -- | Provider configuration |
| `--description` | No | string | None | Connector description |
| `--kms-key-arn` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "ConnectorId": "string",
    "ConnectorArn": "string"
}
```

---

### 10.2 `delete-connector-v2`

Deletes a v2 connector.

**Synopsis:**
```bash
aws securityhub delete-connector-v2 \
    --connector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID to delete |

**Output:** None (HTTP 200 on success)

---

### 10.3 `get-connector-v2`

Returns details about a v2 connector.

**Synopsis:**
```bash
aws securityhub get-connector-v2 \
    --connector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |

**Output Schema:**
```json
{
    "ConnectorId": "string",
    "ConnectorArn": "string",
    "Name": "string",
    "Description": "string",
    "Provider": {},
    "CreatedAt": "timestamp",
    "LastUpdatedAt": "timestamp",
    "KmsKeyArn": "string",
    "Health": {
        "ConnectorStatus": "CONNECTED|PENDING|FAILED",
        "Message": "string"
    }
}
```

---

### 10.4 `list-connectors-v2`

Lists v2 connectors. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-connectors-v2 \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Connectors": [
        {
            "ConnectorId": "string",
            "ConnectorArn": "string",
            "Name": "string",
            "Description": "string",
            "CreatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.5 `update-connector-v2`

Updates a v2 connector.

**Synopsis:**
```bash
aws securityhub update-connector-v2 \
    --connector-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--provider <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID to update |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--provider` | No | structure | None | Updated provider configuration |

**Output Schema:**
```json
{
    "ConnectorId": "string",
    "ConnectorArn": "string",
    "Name": "string",
    "Description": "string",
    "CreatedAt": "timestamp",
    "LastUpdatedAt": "timestamp"
}
```

---

### 10.6 `register-connector-v2`

Registers a v2 connector with Security Hub.

**Synopsis:**
```bash
aws securityhub register-connector-v2 \
    --connector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID to register |

**Output Schema:**
```json
{
    "ConnectorId": "string",
    "ConnectorArn": "string"
}
```
