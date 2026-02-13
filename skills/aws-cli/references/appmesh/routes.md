# Routes

### 5.1 `create-route`

Creates a route associated with a virtual router. Routes match incoming requests and forward them to virtual nodes.

**Synopsis:**
```bash
aws appmesh create-route \
    --mesh-name <value> \
    --virtual-router-name <value> \
    --route-name <value> \
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
| `--virtual-router-name` | **Yes** | string | -- | The name of the virtual router (1-255 chars) |
| `--route-name` | **Yes** | string | -- | The name of the route (1-255 chars) |
| `--spec` | **Yes** | structure | -- | Route specification (see below) |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner (12 digits) |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |
| `--client-token` | No | string | None | Idempotency token (max 36 chars) |

**Spec Structure:**
```json
{
    "priority": "integer (0-1000)",
    "httpRoute": {
        "match": {
            "prefix": "string (must start with /)",
            "path": {"exact": "string", "regex": "string"},
            "method": "GET|HEAD|POST|PUT|DELETE|CONNECT|OPTIONS|TRACE|PATCH",
            "headers": [
                {
                    "name": "string",
                    "invert": "boolean",
                    "match": {
                        "exact": "string",
                        "prefix": "string",
                        "suffix": "string",
                        "regex": "string",
                        "range": {"start": "long", "end": "long"}
                    }
                }
            ],
            "queryParameters": [{"name": "string", "match": {"exact": "string"}}],
            "port": "integer (1-65535)"
        },
        "action": {
            "weightedTargets": [
                {"virtualNode": "string", "weight": "integer (0-100)", "port": "integer"}
            ]
        },
        "retryPolicy": {
            "maxRetries": "long",
            "perRetryTimeout": {"unit": "s|ms", "value": "long"},
            "httpRetryEvents": ["server-error", "gateway-error", "client-error", "stream-error"],
            "tcpRetryEvents": ["connection-error"]
        },
        "timeout": {
            "idle": {"unit": "s|ms", "value": "long"},
            "perRequest": {"unit": "s|ms", "value": "long"}
        }
    },
    "http2Route": {},
    "grpcRoute": {
        "match": {
            "serviceName": "string",
            "methodName": "string",
            "metadata": [],
            "port": "integer"
        },
        "action": {"weightedTargets": []},
        "retryPolicy": {
            "maxRetries": "long",
            "perRetryTimeout": {},
            "grpcRetryEvents": ["cancelled", "deadline-exceeded", "internal", "resource-exhausted", "unavailable"],
            "httpRetryEvents": [],
            "tcpRetryEvents": []
        },
        "timeout": {}
    },
    "tcpRoute": {
        "match": {"port": "integer"},
        "action": {"weightedTargets": []},
        "timeout": {"idle": {"unit": "s|ms", "value": "long"}}
    }
}
```

> **Note:** Specify exactly one of `httpRoute`, `http2Route`, `grpcRoute`, or `tcpRoute`.

**Output Schema:**
```json
{
    "route": {
        "meshName": "string",
        "virtualRouterName": "string",
        "routeName": "string",
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

### 5.2 `delete-route`

Deletes a route.

**Synopsis:**
```bash
aws appmesh delete-route \
    --mesh-name <value> \
    --virtual-router-name <value> \
    --route-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-router-name` | **Yes** | string | -- | The name of the virtual router |
| `--route-name` | **Yes** | string | -- | The name of the route |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-route` output.

---

### 5.3 `describe-route`

Describes a route.

**Synopsis:**
```bash
aws appmesh describe-route \
    --mesh-name <value> \
    --virtual-router-name <value> \
    --route-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-router-name` | **Yes** | string | -- | The name of the virtual router |
| `--route-name` | **Yes** | string | -- | The name of the route |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-route` output.

---

### 5.4 `list-routes`

Lists the routes in a virtual router. **Paginated.**

**Synopsis:**
```bash
aws appmesh list-routes \
    --mesh-name <value> \
    --virtual-router-name <value> \
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
| `--virtual-router-name` | **Yes** | string | -- | The name of the virtual router |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "routes": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "meshName": "string",
            "meshOwner": "string",
            "resourceOwner": "string",
            "routeName": "string",
            "version": "long",
            "virtualRouterName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `update-route`

Updates a route specification.

**Synopsis:**
```bash
aws appmesh update-route \
    --mesh-name <value> \
    --virtual-router-name <value> \
    --route-name <value> \
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
| `--virtual-router-name` | **Yes** | string | -- | The name of the virtual router |
| `--route-name` | **Yes** | string | -- | The name of the route |
| `--spec` | **Yes** | structure | -- | Updated route specification |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
Same as `create-route` output.
