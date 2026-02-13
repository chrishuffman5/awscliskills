# Gateway Routes

### 7.1 `create-gateway-route`

Creates a gateway route associated with a virtual gateway. Gateway routes define how traffic entering the mesh through a virtual gateway is routed to virtual services.

**Synopsis:**
```bash
aws appmesh create-gateway-route \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
    --gateway-route-name <value> \
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
| `--gateway-route-name` | **Yes** | string | -- | The name of the gateway route (1-255 chars) |
| `--spec` | **Yes** | structure | -- | Gateway route specification (see below) |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner (12 digits) |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |
| `--client-token` | No | string | None | Idempotency token (max 36 chars) |

**Spec Structure:**
```json
{
    "priority": "integer (0-1000)",
    "httpRoute": {
        "match": {
            "prefix": "string",
            "path": {"exact": "string", "regex": "string"},
            "method": "GET|HEAD|POST|PUT|DELETE|CONNECT|OPTIONS|TRACE|PATCH",
            "hostname": {"exact": "string", "suffix": "string"},
            "headers": [
                {
                    "name": "string",
                    "invert": "boolean",
                    "match": {"exact": "string", "prefix": "string", "suffix": "string", "regex": "string", "range": {"start": "long", "end": "long"}}
                }
            ],
            "queryParameters": [{"name": "string", "match": {"exact": "string"}}],
            "port": "integer (1-65535)"
        },
        "action": {
            "target": {
                "virtualService": {"virtualServiceName": "string"},
                "port": "integer (1-65535)"
            },
            "rewrite": {
                "hostname": {"defaultTargetHostname": "ENABLED|DISABLED"},
                "path": {"exact": "string"},
                "prefix": {"defaultPrefix": "ENABLED|DISABLED", "value": "string"}
            }
        }
    },
    "http2Route": {},
    "grpcRoute": {
        "match": {
            "serviceName": "string",
            "hostname": {"exact": "string", "suffix": "string"},
            "metadata": [],
            "port": "integer"
        },
        "action": {
            "target": {"virtualService": {"virtualServiceName": "string"}, "port": "integer"},
            "rewrite": {"hostname": {"defaultTargetHostname": "ENABLED|DISABLED"}}
        }
    }
}
```

> **Note:** Specify exactly one of `httpRoute`, `http2Route`, or `grpcRoute`.

**Output Schema:**
```json
{
    "gatewayRoute": {
        "meshName": "string",
        "virtualGatewayName": "string",
        "gatewayRouteName": "string",
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

### 7.2 `delete-gateway-route`

Deletes a gateway route.

**Synopsis:**
```bash
aws appmesh delete-gateway-route \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
    --gateway-route-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-gateway-name` | **Yes** | string | -- | The name of the virtual gateway |
| `--gateway-route-name` | **Yes** | string | -- | The name of the gateway route |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-gateway-route` output.

---

### 7.3 `describe-gateway-route`

Describes a gateway route.

**Synopsis:**
```bash
aws appmesh describe-gateway-route \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
    --gateway-route-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-gateway-name` | **Yes** | string | -- | The name of the virtual gateway |
| `--gateway-route-name` | **Yes** | string | -- | The name of the gateway route |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-gateway-route` output.

---

### 7.4 `list-gateway-routes`

Lists the gateway routes for a virtual gateway. **Paginated.**

**Synopsis:**
```bash
aws appmesh list-gateway-routes \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
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
| `--virtual-gateway-name` | **Yes** | string | -- | The name of the virtual gateway |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "gatewayRoutes": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "gatewayRouteName": "string",
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

### 7.5 `update-gateway-route`

Updates a gateway route specification.

**Synopsis:**
```bash
aws appmesh update-gateway-route \
    --mesh-name <value> \
    --virtual-gateway-name <value> \
    --gateway-route-name <value> \
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
| `--gateway-route-name` | **Yes** | string | -- | The name of the gateway route |
| `--spec` | **Yes** | structure | -- | Updated gateway route specification |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
Same as `create-gateway-route` output.
