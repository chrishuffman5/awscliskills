# Capabilities

### 9.1 `create-capability`

Creates a capability for the specified EKS cluster.

**Synopsis:**
```bash
aws eks create-capability \
    --cluster-name <value> \
    --capability-type <value> \
    [--configuration <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--capability-type` | **Yes** | string | -- | Capability type |
| `--configuration` | No | string | None | Configuration for the capability (JSON) |
| `--tags` | No | map | None | Tags for the capability |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "capability": {
        "capabilityId": "string",
        "clusterName": "string",
        "capabilityType": "string",
        "configuration": "string",
        "status": "CREATING|ACTIVE|DELETING|CREATE_FAILED|DELETE_FAILED",
        "createdAt": "timestamp",
        "modifiedAt": "timestamp",
        "tags": {"key": "value"}
    }
}
```

---

### 9.2 `delete-capability`

Deletes a capability from the specified cluster.

**Synopsis:**
```bash
aws eks delete-capability \
    --cluster-name <value> \
    --capability-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--capability-id` | **Yes** | string | -- | Capability ID |

**Output Schema:**
```json
{
    "capability": {
        "capabilityId": "string",
        "clusterName": "string",
        "capabilityType": "string",
        "status": "DELETING",
        "createdAt": "timestamp",
        "modifiedAt": "timestamp"
    }
}
```

---

### 9.3 `describe-capability`

Describes a capability.

**Synopsis:**
```bash
aws eks describe-capability \
    --cluster-name <value> \
    --capability-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--capability-id` | **Yes** | string | -- | Capability ID |

**Output Schema:**
```json
{
    "capability": {
        "capabilityId": "string",
        "clusterName": "string",
        "capabilityType": "string",
        "configuration": "string",
        "status": "CREATING|ACTIVE|DELETING|CREATE_FAILED|DELETE_FAILED",
        "createdAt": "timestamp",
        "modifiedAt": "timestamp",
        "tags": {"key": "value"},
        "health": {
            "issues": [
                {
                    "code": "string",
                    "message": "string",
                    "resourceIds": ["string"]
                }
            ]
        }
    }
}
```

---

### 9.4 `list-capabilities`

Lists capabilities for the specified cluster. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-capabilities \
    --cluster-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "capabilities": [
        {
            "capabilityId": "string",
            "clusterName": "string",
            "capabilityType": "string",
            "status": "string",
            "createdAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.5 `update-capability`

Updates a capability configuration.

**Synopsis:**
```bash
aws eks update-capability \
    --cluster-name <value> \
    --capability-id <value> \
    [--configuration <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--capability-id` | **Yes** | string | -- | Capability ID |
| `--configuration` | No | string | None | Updated configuration (JSON) |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "capability": {
        "capabilityId": "string",
        "clusterName": "string",
        "capabilityType": "string",
        "configuration": "string",
        "status": "string",
        "createdAt": "timestamp",
        "modifiedAt": "timestamp"
    }
}
```
