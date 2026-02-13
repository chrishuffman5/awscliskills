# Virtual Gateways

### 6.1 `create-virtual-gateway`

Creates a virtual gateway. A virtual gateway allows resources outside of the mesh to communicate with resources inside the mesh through an Envoy proxy.

**Synopsis:**
```bash
aws appmesh create-virtual-gateway \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
    --spec <value> \
    [--mesh-owner <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh (1-255 chars) |
| `--virtual-gateway-name` | **Yes** | string | -- | The name of the virtual gateway (1-255 chars) |
| `--spec` | **Yes** | structure | -- | Virtual gateway specification (see below) |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner (12 digits) |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |
| `--client-token` | No | string | None | Idempotency token (max 36 chars) |

**Spec Structure:**
```json
{
    "listeners": [
        {
            "portMapping": {
                "port": "integer (1-65535)",
                "protocol": "http|http2|grpc"
            },
            "healthCheck": {
                "protocol": "http|http2|grpc",
                "port": "integer",
                "path": "string",
                "healthyThreshold": "integer",
                "unhealthyThreshold": "integer",
                "intervalMillis": "long",
                "timeoutMillis": "long"
            },
            "connectionPool": {
                "http": {"maxConnections": "integer", "maxPendingRequests": "integer"},
                "http2": {"maxRequests": "integer"},
                "grpc": {"maxRequests": "integer"}
            },
            "tls": {
                "mode": "STRICT|PERMISSIVE|DISABLED",
                "certificate": {
                    "acm": {"certificateArn": "string"},
                    "file": {"certificateChain": "string", "privateKey": "string"},
                    "sds": {"secretName": "string"}
                },
                "validation": {
                    "subjectAlternativeNames": {"match": {"exact": ["string"]}},
                    "trust": {
                        "file": {"certificateChain": "string"},
                        "sds": {"secretName": "string"}
                    }
                }
            }
        }
    ],
    "backendDefaults": {
        "clientPolicy": {
            "tls": {
                "enforce": "boolean",
                "ports": ["integer"],
                "certificate": {},
                "validation": {}
            }
        }
    },
    "logging": {
        "accessLog": {
            "file": {
                "path": "string",
                "format": {
                    "text": "string",
                    "json": [{"key": "string", "value": "string"}]
                }
            }
        }
    }
}
```

> **Note:** Virtual gateways support `http`, `http2`, and `grpc` protocols only (not `tcp`).

**Output Schema:**
```json
{
    "virtualGateway": {
        "meshName": "string",
        "virtualGatewayName": "string",
        "metadata": {
            "arn": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "meshOwner": "string",
            "resourceOwner": "string",
            "uid": "string",
            "version": "long"
        },
        "spec": {},
        "status": {"status": "ACTIVE|INACTIVE|DELETED"}
    }
}
```

---

### 6.2 `delete-virtual-gateway`

Deletes a virtual gateway. Must delete all gateway routes first.

**Synopsis:**
```bash
aws appmesh delete-virtual-gateway \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-gateway-name` | **Yes** | string | -- | The name of the virtual gateway |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-virtual-gateway` output.

---

### 6.3 `describe-virtual-gateway`

Describes a virtual gateway.

**Synopsis:**
```bash
aws appmesh describe-virtual-gateway \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-gateway-name` | **Yes** | string | -- | The name of the virtual gateway |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-virtual-gateway` output.

---

### 6.4 `list-virtual-gateways`

Lists the virtual gateways in a service mesh. **Paginated.**

**Synopsis:**
```bash
aws appmesh list-virtual-gateways \
    --mesh-name <value> \
    [--mesh-owner <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "virtualGateways": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "meshName": "string",
            "meshOwner": "string",
            "resourceOwner": "string",
            "version": "long",
            "virtualGatewayName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.5 `update-virtual-gateway`

Updates a virtual gateway specification.

**Synopsis:**
```bash
aws appmesh update-virtual-gateway \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
    --spec <value> \
    [--mesh-owner <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-gateway-name` | **Yes** | string | -- | The name of the virtual gateway |
| `--spec` | **Yes** | structure | -- | Updated virtual gateway specification |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
Same as `create-virtual-gateway` output.
