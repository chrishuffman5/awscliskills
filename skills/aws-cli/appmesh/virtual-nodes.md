# Virtual Nodes

### 2.1 `create-virtual-node`

Creates a virtual node within a service mesh. A virtual node acts as a logical pointer to a service (e.g., an ECS service or Kubernetes deployment).

**Synopsis:**
```bash
aws appmesh create-virtual-node \
    --mesh-name <value> \
    --virtual-node-name <value> \
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
| `--virtual-node-name` | **Yes** | string | -- | The name of the virtual node (1-255 chars) |
| `--spec` | **Yes** | structure | -- | Virtual node specification (see below) |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner (12 digits) |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |
| `--client-token` | No | string | None | Idempotency token (max 36 chars) |

**Spec Structure:**
```json
{
    "serviceDiscovery": {
        "dns": {
            "hostname": "string",
            "ipPreference": "IPv6_PREFERRED|IPv4_PREFERRED|IPv4_ONLY|IPv6_ONLY",
            "responseType": "LOADBALANCER|ENDPOINTS"
        },
        "awsCloudMap": {
            "namespaceName": "string",
            "serviceName": "string",
            "ipPreference": "IPv6_PREFERRED|IPv4_PREFERRED|IPv4_ONLY|IPv6_ONLY",
            "attributes": [{"key": "string", "value": "string"}]
        }
    },
    "listeners": [
        {
            "portMapping": {"port": "integer", "protocol": "http|tcp|http2|grpc"},
            "healthCheck": {
                "protocol": "http|tcp|http2|grpc",
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
                "grpc": {"maxRequests": "integer"},
                "tcp": {"maxConnections": "integer"}
            },
            "outlierDetection": {
                "maxServerErrors": "long",
                "maxEjectionPercent": "integer",
                "interval": {"value": "long", "unit": "s|ms"},
                "baseEjectionDuration": {"value": "long", "unit": "s|ms"}
            },
            "timeout": {
                "http": {"idle": {"value": "long", "unit": "s|ms"}, "perRequest": {"value": "long", "unit": "s|ms"}},
                "http2": {"idle": {}, "perRequest": {}},
                "grpc": {"idle": {}, "perRequest": {}},
                "tcp": {"idle": {"value": "long", "unit": "s|ms"}}
            },
            "tls": {
                "mode": "STRICT|PERMISSIVE|DISABLED",
                "certificate": {
                    "acm": {"certificateArn": "string"},
                    "file": {"certificateChain": "string", "privateKey": "string"},
                    "sds": {"secretName": "string"}
                }
            }
        }
    ],
    "backends": [
        {
            "virtualService": {
                "virtualServiceName": "string",
                "clientPolicy": {
                    "tls": {
                        "enforce": "boolean",
                        "ports": ["integer"],
                        "validation": {
                            "trust": {
                                "acm": {"certificateAuthorityArns": ["string"]},
                                "file": {"certificateChain": "string"},
                                "sds": {"secretName": "string"}
                            }
                        }
                    }
                }
            }
        }
    ],
    "backendDefaults": {
        "clientPolicy": {"tls": {"enforce": "boolean", "ports": [], "validation": {}}}
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

**Output Schema:**
```json
{
    "virtualNode": {
        "meshName": "string",
        "virtualNodeName": "string",
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

### 2.2 `delete-virtual-node`

Deletes a virtual node. Must remove all routes that reference the node first.

**Synopsis:**
```bash
aws appmesh delete-virtual-node \
    --mesh-name <value> \
    --virtual-node-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-node-name` | **Yes** | string | -- | The name of the virtual node |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-virtual-node` output.

---

### 2.3 `describe-virtual-node`

Describes a virtual node.

**Synopsis:**
```bash
aws appmesh describe-virtual-node \
    --mesh-name <value> \
    --virtual-node-name <value> \
    [--mesh-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mesh-name` | **Yes** | string | -- | The name of the service mesh |
| `--virtual-node-name` | **Yes** | string | -- | The name of the virtual node |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |

**Output Schema:**
Same as `create-virtual-node` output.

---

### 2.4 `list-virtual-nodes`

Lists the virtual nodes in a service mesh. **Paginated.**

**Synopsis:**
```bash
aws appmesh list-virtual-nodes \
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
    "virtualNodes": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "meshName": "string",
            "meshOwner": "string",
            "resourceOwner": "string",
            "version": "long",
            "virtualNodeName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `update-virtual-node`

Updates a virtual node specification.

**Synopsis:**
```bash
aws appmesh update-virtual-node \
    --mesh-name <value> \
    --virtual-node-name <value> \
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
| `--virtual-node-name` | **Yes** | string | -- | The name of the virtual node |
| `--spec` | **Yes** | structure | -- | Updated virtual node specification |
| `--mesh-owner` | No | string | None | Account ID of the mesh owner |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
Same as `create-virtual-node` output.
