# Clusters & Nodes

### 8.1 `create-cluster`

Creates an Anywhere cluster for on-premises MediaLive deployments.

**Synopsis:**
```bash
aws medialive create-cluster \
    [--cluster-type <value>] \
    [--instance-role-arn <value>] \
    [--name <value>] \
    [--network-settings <value>] \
    [--request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-type` | No | string | None | `ON_PREMISES` (only value) |
| `--instance-role-arn` | No | string | None | IAM role for nodes |
| `--name` | No | string | None | Cluster name (case-sensitive, unique) |
| `--network-settings` | No | structure | None | Network configuration |
| `--request-id` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Key-value tag pairs |

**NetworkSettings:**
```json
{
    "DefaultRoute": "string",
    "InterfaceMappings": [
        {
            "LogicalInterfaceName": "string",
            "NetworkId": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "ClusterType": "ON_PREMISES",
    "InstanceRoleArn": "string",
    "ChannelIds": ["string"],
    "NetworkSettings": {},
    "State": "CREATING|CREATE_FAILED|ACTIVE|DELETING|DELETE_FAILED|DELETED"
}
```

---

### 8.2 `describe-cluster`

Describes a cluster.

**Synopsis:**
```bash
aws medialive describe-cluster \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |

**Output Schema:** Same as `create-cluster` output.

---

### 8.3 `update-cluster`

Updates a cluster's settings.

**Synopsis:**
```bash
aws medialive update-cluster \
    --cluster-id <value> \
    [--name <value>] \
    [--network-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID to update |
| `--name` | No | string | None | Updated name |
| `--network-settings` | No | structure | None | Updated network settings |

**Output Schema:** Same as `create-cluster` output.

---

### 8.4 `delete-cluster`

Deletes a cluster.

**Synopsis:**
```bash
aws medialive delete-cluster \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "State": "DELETING"
}
```

---

### 8.5 `list-clusters`

Lists clusters. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-clusters \
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
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Clusters": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "ClusterType": "string",
            "InstanceRoleArn": "string",
            "NetworkSettings": {},
            "State": "string"
        }
    ]
}
```

---

### 8.6 `create-node`

Creates a node in a cluster.

**Synopsis:**
```bash
aws medialive create-node \
    --cluster-id <value> \
    [--name <value>] \
    [--node-interface-mappings <value>] \
    [--request-id <value>] \
    [--role <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--name` | No | string | None | Node name |
| `--node-interface-mappings` | No | list | None | Network interface mappings |
| `--request-id` | No | string | Auto | Idempotency token |
| `--role` | No | string | None | `BACKUP` or `ACTIVE` |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "ClusterId": "string",
    "ConnectionState": "CONNECTED|DISCONNECTED",
    "InstanceArn": "string",
    "NodeInterfaceMappings": [],
    "Role": "BACKUP|ACTIVE",
    "State": "CREATING|CREATE_FAILED|ACTIVE|DELETING|DELETE_FAILED|DELETED"
}
```

---

### 8.7 `describe-node`

Describes a node.

**Synopsis:**
```bash
aws medialive describe-node \
    --cluster-id <value> \
    --node-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--node-id` | **Yes** | string | -- | Node ID |

**Output Schema:** Same as `create-node` output.

---

### 8.8 `update-node`

Updates a node's configuration.

**Synopsis:**
```bash
aws medialive update-node \
    --cluster-id <value> \
    --node-id <value> \
    [--name <value>] \
    [--role <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--node-id` | **Yes** | string | -- | Node ID |
| `--name` | No | string | None | Updated name |
| `--role` | No | string | None | `BACKUP` or `ACTIVE` |

**Output Schema:** Same as `create-node` output.

---

### 8.9 `update-node-state`

Updates a node's operational state (e.g., for draining).

**Synopsis:**
```bash
aws medialive update-node-state \
    --cluster-id <value> \
    --node-id <value> \
    [--state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--node-id` | **Yes** | string | -- | Node ID |
| `--state` | No | string | None | `ACTIVE` or `DRAINING` |

**Output Schema:** Same as `create-node` output.

---

### 8.10 `delete-node`

Deletes a node from a cluster.

**Synopsis:**
```bash
aws medialive delete-node \
    --cluster-id <value> \
    --node-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--node-id` | **Yes** | string | -- | Node ID to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "State": "DELETING"
}
```

---

### 8.11 `list-nodes`

Lists nodes in a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-nodes \
    --cluster-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Nodes": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "ClusterId": "string",
            "ConnectionState": "string",
            "Role": "string",
            "State": "string"
        }
    ]
}
```

---

### 8.12 `create-node-registration-script`

Generates a registration script for adding nodes to a cluster.

**Synopsis:**
```bash
aws medialive create-node-registration-script \
    --cluster-id <value> \
    [--id <value>] \
    [--name <value>] \
    [--node-interface-mappings <value>] \
    [--request-id <value>] \
    [--role <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--id` | No | string | None | Node ID |
| `--name` | No | string | None | Node name |
| `--node-interface-mappings` | No | list | None | Interface mappings |
| `--request-id` | No | string | Auto | Idempotency token |
| `--role` | No | string | None | `BACKUP` or `ACTIVE` |

**Output Schema:**
```json
{
    "NodeRegistrationScript": "string"
}
```

---

### 8.13 `list-cluster-alerts`

Lists alerts for a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-cluster-alerts \
    --cluster-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Alerts": [
        {
            "AlertId": "string",
            "AlertMessage": "string",
            "AlertType": "string",
            "FirstTimestamp": "timestamp",
            "LastTimestamp": "timestamp"
        }
    ]
}
```
