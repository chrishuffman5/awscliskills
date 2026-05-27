# Virtual Services

### 3.1 `create-virtual-service`

Creates a virtual service within a service mesh. A virtual service provides an abstraction backed by either a virtual node or a virtual router.

**Synopsis:**
```bash
aws appmesh create-virtual-service \
    --mesh-name <value> \
    --virtual-service-name <value> \
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
| `--virtual-service-name` | **Yes** | string | -- | The name of the virtual service |
| `--spec` | **Yes** | structure | -- | Virtual service specification (see below) |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner (12 digits) |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |
| `--client-token` | No | string | None | Idempotency token (max 36 chars) |

**Spec Structure:**
```json
{
    "provider": {
        "virtualNode": {"virtualNodeName": "string"},
        "virtualRouter": {"virtualRouterName": "string"}
    }
}
```

> **Note:** Specify either `virtualNode` or `virtualRouter` as the provider, not both.

**Output Schema:**
```json
{
    "virtualService": {
        "meshName": "string",
        "virtualServiceName": "string",
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
            "provider": {
                "virtualNode": {"virtualNodeName": "string"},
                "virtualRouter": {"virtualRouterName": "string"}
            }
        },
        "status": {"status": "ACTIVE|INACTIVE|DELETED"}
    }
}
```

---

### 3.2 `delete-virtual-service`

Deletes a virtual service.

**Synopsis:**
```bash
aws appmesh delete-virtual-service \
    --mesh-name <value> \
    --virtual-service-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-service-name` | **Yes** | string | -- | The name of the virtual service |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-virtual-service` output.

---

### 3.3 `describe-virtual-service`

Describes a virtual service.

**Synopsis:**
```bash
aws appmesh describe-virtual-service \
    --mesh-name <value> \
    --virtual-service-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-service-name` | **Yes** | string | -- | The name of the virtual service |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-virtual-service` output.

---

### 3.4 `list-virtual-services`

Lists the virtual services in a service mesh. **Paginated.**

**Synopsis:**
```bash
aws appmesh list-virtual-services \
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
    "virtualServices": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "meshName": "string",
            "meshOwner": "string",
            "resourceOwner": "string",
            "version": "long",
            "virtualServiceName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `update-virtual-service`

Updates a virtual service specification.

**Synopsis:**
```bash
aws appmesh update-virtual-service \
    --mesh-name <value> \
    --virtual-service-name <value> \
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
| `--virtual-service-name` | **Yes** | string | -- | The name of the virtual service |
| `--spec` | **Yes** | structure | -- | Updated virtual service specification |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
Same as `create-virtual-service` output.
