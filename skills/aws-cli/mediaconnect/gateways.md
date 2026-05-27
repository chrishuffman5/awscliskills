# Gateways

### 8.1 `create-gateway`

Creates a gateway for on-premises MediaConnect deployment.

**Synopsis:**
```bash
aws mediaconnect create-gateway \
    --name <value> \
    --egress-cidr-blocks <value> \
    --networks <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Gateway name (immutable) |
| `--egress-cidr-blocks` | **Yes** | list | -- | CIDR blocks for egress traffic |
| `--networks` | **Yes** | list | -- | Network configurations (1-4 networks) |

**Network Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `CidrBlock` | **Yes** | string | Unique IP range in CIDR format |
| `Name` | **Yes** | string | Network name (unique within gateway) |

**Output Schema:**
```json
{
    "Gateway": {
        "GatewayArn": "string",
        "Name": "string",
        "EgressCidrBlocks": ["string"],
        "Networks": [{"CidrBlock": "string", "Name": "string"}],
        "GatewayState": "CREATING|ACTIVE|UPDATING|ERROR|DELETING|DELETED",
        "GatewayMessages": [{"Code": "string", "Message": "string"}]
    }
}
```

---

### 8.2 `describe-gateway`

Describes a gateway.

**Synopsis:**
```bash
aws mediaconnect describe-gateway \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |

**Output Schema:** Same as `create-gateway` output.

---

### 8.3 `list-gateways`

Lists all gateways. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconnect list-gateways \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Gateways": [
        {
            "GatewayArn": "string",
            "GatewayState": "string",
            "Name": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.4 `delete-gateway`

Deletes a gateway. All instances must be deregistered first.

**Synopsis:**
```bash
aws mediaconnect delete-gateway \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway to delete |

**Output Schema:**
```json
{
    "GatewayArn": "string"
}
```

---

### 8.5 `describe-gateway-instance`

Describes a gateway instance.

**Synopsis:**
```bash
aws mediaconnect describe-gateway-instance \
    --gateway-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-instance-arn` | **Yes** | string | -- | ARN of the gateway instance |

**Output Schema:**
```json
{
    "GatewayInstance": {
        "BridgePlacement": "AVAILABLE|LOCKED",
        "ConnectionStatus": "CONNECTED|DISCONNECTED",
        "GatewayArn": "string",
        "GatewayInstanceArn": "string",
        "InstanceId": "string",
        "InstanceMessages": [{"Code": "string", "Message": "string"}],
        "InstanceState": "REGISTERING|ACTIVE|DEREGISTERING|DEREGISTERED|REGISTRATION_ERROR|DEREGISTRATION_ERROR",
        "RunningBridgeCount": "integer"
    }
}
```

---

### 8.6 `list-gateway-instances`

Lists gateway instances. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconnect list-gateway-instances \
    [--filter-arn <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-arn` | No | string | None | Filter by gateway ARN |
| `--max-results` | No | integer | None | Max results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Instances": [
        {
            "GatewayArn": "string",
            "GatewayInstanceArn": "string",
            "InstanceId": "string",
            "InstanceState": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.7 `update-gateway-instance`

Updates a gateway instance's bridge placement setting.

**Synopsis:**
```bash
aws mediaconnect update-gateway-instance \
    --gateway-instance-arn <value> \
    [--bridge-placement <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-instance-arn` | **Yes** | string | -- | ARN of the gateway instance |
| `--bridge-placement` | No | string | None | `AVAILABLE` or `LOCKED` |

**Output Schema:**
```json
{
    "BridgePlacement": "AVAILABLE|LOCKED",
    "GatewayInstanceArn": "string"
}
```

---

### 8.8 `deregister-gateway-instance`

Deregisters a gateway instance from the gateway.

**Synopsis:**
```bash
aws mediaconnect deregister-gateway-instance \
    --gateway-instance-arn <value> \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-instance-arn` | **Yes** | string | -- | ARN of the gateway instance |
| `--force` | No | boolean | false | Force deregistration even if bridges are running |

**Output Schema:**
```json
{
    "GatewayInstanceArn": "string",
    "InstanceState": "DEREGISTERING"
}
```
