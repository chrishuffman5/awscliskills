# Virtual Routers

### 4.1 `create-virtual-router`

Creates a virtual router within a service mesh. Virtual routers handle traffic for virtual services and contain routes that define how to route requests.

**Synopsis:**
```bash
aws appmesh create-virtual-router \
    --mesh-name <value> \
    --virtual-router-name <value> \
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
| `--spec` | **Yes** | structure | -- | Virtual router specification (see below) |
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
                "protocol": "http|tcp|http2|grpc"
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "virtualRouter": {
        "meshName": "string",
        "virtualRouterName": "string",
        "metadata": {
            "arn": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "meshOwner": "string",
            "resourceOwner": "string",
            "uid": "string",
            "version": "long"
        },
        "spec": {
            "listeners": [
                {"portMapping": {"port": "integer", "protocol": "string"}}
            ]
        },
        "status": {"status": "ACTIVE|INACTIVE|DELETED"}
    }
}
```

---

### 4.2 `delete-virtual-router`

Deletes a virtual router. Must delete all routes in the router first.

**Synopsis:**
```bash
aws appmesh delete-virtual-router \
    --mesh-name <value> \
    --virtual-router-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-router-name` | **Yes** | string | -- | The name of the virtual router |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-virtual-router` output.

---

### 4.3 `describe-virtual-router`

Describes a virtual router.

**Synopsis:**
```bash
aws appmesh describe-virtual-router \
    --mesh-name <value> \
    --virtual-router-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-router-name` | **Yes** | string | -- | The name of the virtual router |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-virtual-router` output.

---

### 4.4 `list-virtual-routers`

Lists the virtual routers in a service mesh. **Paginated.**

**Synopsis:**
```bash
aws appmesh list-virtual-routers \
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
    "virtualRouters": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "meshName": "string",
            "meshOwner": "string",
            "resourceOwner": "string",
            "version": "long",
            "virtualRouterName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `update-virtual-router`

Updates a virtual router specification.

**Synopsis:**
```bash
aws appmesh update-virtual-router \
    --mesh-name <value> \
    --virtual-router-name <value> \
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
| `--spec` | **Yes** | structure | -- | Updated virtual router specification |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
Same as `create-virtual-router` output.
