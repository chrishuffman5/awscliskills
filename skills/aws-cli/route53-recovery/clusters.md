# Clusters

Commands for managing Route 53 ARC recovery clusters via `aws route53-recovery-control-config`.

### 2.1 `create-cluster`

Creates a new recovery cluster with 5 redundant Regional endpoints.

**Synopsis:**
```bash
aws route53-recovery-control-config create-cluster \
    --cluster-name <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Name of the cluster (1-64 chars, non-whitespace) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |
| `--tags` | No | map | None | Tags as key-value pairs. Shorthand: `KeyName1=string,KeyName2=string` |
| `--network-type` | No | string | `IPV4` | Network type: `IPV4` or `DUALSTACK` |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterArn": "string",
        "ClusterEndpoints": [
            {
                "Endpoint": "string",
                "Region": "string"
            }
        ],
        "Name": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string",
        "NetworkType": "IPV4|DUALSTACK"
    }
}
```

---

### 2.2 `delete-cluster`

Deletes a recovery cluster. All control panels, routing controls, and safety rules must be deleted first.

**Synopsis:**
```bash
aws route53-recovery-control-config delete-cluster \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster to delete |

**Output:** None on success.

---

### 2.3 `describe-cluster`

Gets details about a recovery cluster including its endpoints.

**Synopsis:**
```bash
aws route53-recovery-control-config describe-cluster \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterArn": "string",
        "ClusterEndpoints": [
            {
                "Endpoint": "string",
                "Region": "string"
            }
        ],
        "Name": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string",
        "NetworkType": "IPV4|DUALSTACK"
    }
}
```

---

### 2.4 `list-clusters`

Lists all recovery clusters in the account. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-control-config list-clusters \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Clusters": [
        {
            "ClusterArn": "string",
            "ClusterEndpoints": [
                {
                    "Endpoint": "string",
                    "Region": "string"
                }
            ],
            "Name": "string",
            "Status": "PENDING|DEPLOYED|PENDING_DELETION",
            "Owner": "string",
            "NetworkType": "IPV4|DUALSTACK"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-cluster`

Updates cluster configuration (network type).

**Synopsis:**
```bash
aws route53-recovery-control-config update-cluster \
    --cluster-arn <value> \
    [--network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster to update |
| `--network-type` | No | string | None | Network type: `IPV4` or `DUALSTACK` |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterArn": "string",
        "ClusterEndpoints": [
            {
                "Endpoint": "string",
                "Region": "string"
            }
        ],
        "Name": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string",
        "NetworkType": "IPV4|DUALSTACK"
    }
}
```
