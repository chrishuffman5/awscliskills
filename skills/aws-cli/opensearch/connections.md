# Connections

### 4.1 `create-outbound-connection`

Creates a cross-cluster connection from a local domain to a remote domain.

**Synopsis:**
```bash
aws opensearch create-outbound-connection \
    --local-domain-info <value> \
    --remote-domain-info <value> \
    --connection-alias <value> \
    [--connection-mode <value>] \
    [--connection-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--local-domain-info` | **Yes** | structure | -- | Local domain info. Shorthand: `OwnerId=string,DomainName=string,Region=string` |
| `--remote-domain-info` | **Yes** | structure | -- | Remote domain info. Shorthand: `OwnerId=string,DomainName=string,Region=string` |
| `--connection-alias` | **Yes** | string | -- | Connection name |
| `--connection-mode` | No | string | -- | `DIRECT` or `VPC_ENDPOINT` |
| `--connection-properties` | No | structure | None | Connection properties |

**Output Schema:**
```json
{
    "LocalDomainInfo": {"OwnerId": "string", "DomainName": "string", "Region": "string"},
    "RemoteDomainInfo": {"OwnerId": "string", "DomainName": "string", "Region": "string"},
    "ConnectionAlias": "string",
    "ConnectionStatus": {
        "StatusCode": "PENDING_ACCEPTANCE|APPROVED|PROVISIONING|ACTIVE|REJECTING|REJECTED|DELETING|DELETED",
        "Message": "string"
    },
    "ConnectionId": "string",
    "ConnectionMode": "DIRECT|VPC_ENDPOINT"
}
```

---

### 4.2 `delete-outbound-connection`

Deletes an outbound cross-cluster connection.

**Synopsis:**
```bash
aws opensearch delete-outbound-connection \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | Connection ID |

**Output Schema:**
```json
{
    "Connection": {
        "ConnectionId": "string",
        "ConnectionAlias": "string",
        "ConnectionStatus": {"StatusCode": "DELETING"}
    }
}
```

---

### 4.3 `describe-outbound-connections`

Lists outbound cross-cluster connections. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch describe-outbound-connections \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |

**Output Schema:**
```json
{
    "Connections": [
        {
            "LocalDomainInfo": {},
            "RemoteDomainInfo": {},
            "ConnectionId": "string",
            "ConnectionAlias": "string",
            "ConnectionStatus": {"StatusCode": "string", "Message": "string"},
            "ConnectionMode": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `accept-inbound-connection`

Accepts an inbound cross-cluster connection request.

**Synopsis:**
```bash
aws opensearch accept-inbound-connection \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | Connection ID to accept |

**Output Schema:**
```json
{
    "Connection": {
        "ConnectionId": "string",
        "LocalDomainInfo": {},
        "RemoteDomainInfo": {},
        "ConnectionStatus": {"StatusCode": "APPROVED"}
    }
}
```

---

### 4.5 `delete-inbound-connection`

Deletes an inbound cross-cluster connection.

**Synopsis:**
```bash
aws opensearch delete-inbound-connection \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | Connection ID to delete |

**Output Schema:**
```json
{
    "Connection": {
        "ConnectionId": "string",
        "ConnectionStatus": {"StatusCode": "DELETING"}
    }
}
```

---

### 4.6 `describe-inbound-connections`

Lists inbound cross-cluster connections. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch describe-inbound-connections \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |

**Output Schema:**
```json
{
    "Connections": [
        {
            "ConnectionId": "string",
            "LocalDomainInfo": {},
            "RemoteDomainInfo": {},
            "ConnectionStatus": {"StatusCode": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

### 4.7 `reject-inbound-connection`

Rejects an inbound cross-cluster connection request.

**Synopsis:**
```bash
aws opensearch reject-inbound-connection \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | Connection ID to reject |

**Output Schema:**
```json
{
    "Connection": {
        "ConnectionId": "string",
        "ConnectionStatus": {"StatusCode": "REJECTED"}
    }
}
```
