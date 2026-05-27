# Routers

## Router Inputs

### 9.1 `create-router-input`

Creates a router input.

**Synopsis:**
```bash
aws mediaconnect create-router-input \
    --gateway-arn <value> \
    --name <value> \
    [--source-flow-arn <value>] \
    [--source-bridge-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--name` | **Yes** | string | -- | Name for the router input |
| `--source-flow-arn` | No | string | None | ARN of the source flow |
| `--source-bridge-arn` | No | string | None | ARN of the source bridge |

**Output Schema:**
```json
{
    "GatewayArn": "string",
    "RouterInput": {
        "RouterInputArn": "string",
        "Name": "string",
        "State": "string"
    }
}
```

---

### 9.2 `get-router-input`

Gets details for a router input.

**Synopsis:**
```bash
aws mediaconnect get-router-input \
    --gateway-arn <value> \
    --router-input-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-input-arn` | **Yes** | string | -- | ARN of the router input |

---

### 9.3 `list-router-inputs`

Lists router inputs for a gateway. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconnect list-router-inputs \
    --gateway-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--max-results` | No | integer | None | Max results per page |
| `--next-token` | No | string | None | Pagination token |

---

### 9.4 `update-router-input`

Updates a router input configuration.

**Synopsis:**
```bash
aws mediaconnect update-router-input \
    --gateway-arn <value> \
    --router-input-arn <value> \
    [--name <value>] \
    [--source-flow-arn <value>] \
    [--source-bridge-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-input-arn` | **Yes** | string | -- | ARN of the router input |
| `--name` | No | string | None | Updated name |
| `--source-flow-arn` | No | string | None | Updated source flow ARN |
| `--source-bridge-arn` | No | string | None | Updated source bridge ARN |

---

### 9.5 `delete-router-input`

Deletes a router input.

**Synopsis:**
```bash
aws mediaconnect delete-router-input \
    --gateway-arn <value> \
    --router-input-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-input-arn` | **Yes** | string | -- | ARN of the router input to delete |

---

### 9.6 `start-router-input` / `stop-router-input` / `restart-router-input`

Controls the state of a router input.

**Synopsis:**
```bash
aws mediaconnect start-router-input \
    --gateway-arn <value> \
    --router-input-arn <value>

aws mediaconnect stop-router-input \
    --gateway-arn <value> \
    --router-input-arn <value>

aws mediaconnect restart-router-input \
    --gateway-arn <value> \
    --router-input-arn <value>
```

**Parameters (all three commands):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-input-arn` | **Yes** | string | -- | ARN of the router input |

---

### 9.7 `take-router-input`

Takes over a router input.

**Synopsis:**
```bash
aws mediaconnect take-router-input \
    --gateway-arn <value> \
    --router-input-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-input-arn` | **Yes** | string | -- | ARN of the router input |

---

### 9.8 `batch-get-router-input`

Retrieves details for multiple router inputs in a single call.

**Synopsis:**
```bash
aws mediaconnect batch-get-router-input \
    --gateway-arn <value> \
    --router-input-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-input-arns` | **Yes** | list | -- | List of router input ARNs |

---

### 9.9 `get-router-input-source-metadata` / `get-router-input-thumbnail`

Retrieves source metadata or a thumbnail for a router input.

**Synopsis:**
```bash
aws mediaconnect get-router-input-source-metadata \
    --gateway-arn <value> \
    --router-input-arn <value>

aws mediaconnect get-router-input-thumbnail \
    --gateway-arn <value> \
    --router-input-arn <value>
```

---

## Router Outputs

### 9.10 `create-router-output`

Creates a router output.

**Synopsis:**
```bash
aws mediaconnect create-router-output \
    --gateway-arn <value> \
    --name <value> \
    [--destination-flow-arn <value>] \
    [--destination-bridge-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--name` | **Yes** | string | -- | Name for the router output |
| `--destination-flow-arn` | No | string | None | ARN of the destination flow |
| `--destination-bridge-arn` | No | string | None | ARN of the destination bridge |

---

### 9.11 `get-router-output` / `list-router-outputs` / `update-router-output` / `delete-router-output`

Manage router outputs. All require `--gateway-arn` and `--router-output-arn` (except list which uses `--gateway-arn` only).

**Common Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--gateway-arn` | **Yes** | string | ARN of the gateway |
| `--router-output-arn` | **Yes** | string | ARN of the router output |

---

### 9.12 `start-router-output` / `stop-router-output` / `restart-router-output`

Controls the state of a router output.

**Parameters (all three commands):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-output-arn` | **Yes** | string | -- | ARN of the router output |

---

### 9.13 `batch-get-router-output`

Retrieves details for multiple router outputs in a single call.

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-output-arns` | **Yes** | list | -- | List of router output ARNs |

---

## Router Network Interfaces

### 9.14 `create-router-network-interface`

Creates a router network interface.

**Synopsis:**
```bash
aws mediaconnect create-router-network-interface \
    --gateway-arn <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--name` | **Yes** | string | -- | Name for the network interface |

---

### 9.15 `get-router-network-interface` / `list-router-network-interfaces` / `update-router-network-interface` / `delete-router-network-interface`

Manage router network interfaces. All require `--gateway-arn`.

---

### 9.16 `batch-get-router-network-interface`

Retrieves details for multiple router network interfaces in a single call.

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | ARN of the gateway |
| `--router-network-interface-arns` | **Yes** | list | -- | List of network interface ARNs |
