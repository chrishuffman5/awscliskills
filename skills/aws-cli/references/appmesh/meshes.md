# Meshes

### 1.1 `create-mesh`

Creates a service mesh. A service mesh is a logical boundary for network traffic between services.

**Synopsis:**
```bash
aws appmesh create-mesh \
    --mesh-name <value> \
    [--spec <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh (1-255 chars) |
| `--spec` | No | structure | None | Mesh specification (see below) |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |
| `--client-token` | No | string | None | Idempotency token (max 36 chars) |

**Spec Structure:**
```json
{
    "egressFilter": {
        "type": "ALLOW_ALL|DROP_ALL"
    },
    "serviceDiscovery": {
        "ipPreference": "IPv6_PREFERRED|IPv4_PREFERRED|IPv4_ONLY|IPv6_ONLY"
    }
}
```

**Output Schema:**
```json
{
    "mesh": {
        "meshName": "string",
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
            "egressFilter": {"type": "ALLOW_ALL|DROP_ALL"},
            "serviceDiscovery": {"ipPreference": "string"}
        },
        "status": {"status": "ACTIVE|INACTIVE|DELETED"}
    }
}
```

---

### 1.2 `delete-mesh`

Deletes a service mesh. Must delete all resources within the mesh first.

**Synopsis:**
```bash
aws appmesh delete-mesh \
    --mesh-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |

**Output Schema:**
Same as `create-mesh` output.

---

### 1.3 `describe-mesh`

Describes an existing service mesh.

**Synopsis:**
```bash
aws appmesh describe-mesh \
    --mesh-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--mesh-owner` | No | string | None | The account ID of the mesh owner (12 digits) |

**Output Schema:**
Same as `create-mesh` output.

---

### 1.4 `list-meshes`

Lists all service meshes in the account. **Paginated.**

**Synopsis:**
```bash
aws appmesh list-meshes \
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
    "meshes": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "meshName": "string",
            "meshOwner": "string",
            "resourceOwner": "string",
            "version": "long"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-mesh`

Updates an existing service mesh.

**Synopsis:**
```bash
aws appmesh update-mesh \
    --mesh-name <value> \
    [--spec <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--spec` | No | structure | None | Updated mesh specification |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
Same as `create-mesh` output.
