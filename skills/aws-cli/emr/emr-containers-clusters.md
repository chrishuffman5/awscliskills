# EMR Containers — Virtual Clusters (`aws emr-containers`)

### 11.1 `create-virtual-cluster`

Creates a virtual cluster on an EKS cluster.

**Synopsis:**
```bash
aws emr-containers create-virtual-cluster \
    --name <value> \
    --container-provider <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--security-configuration-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Virtual cluster name |
| `--container-provider` | **Yes** | structure | -- | Container provider configuration |
| `--client-token` | No | string | -- | Idempotency token |
| `--tags` | No | map | -- | Tags as key-value pairs |
| `--security-configuration-id` | No | string | -- | Security configuration ID |

**Container Provider Shorthand:**
```
type=EKS,id=my-eks-cluster,info={eksInfo={namespace=emr}}
```

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string"
}
```

---

### 11.2 `delete-virtual-cluster`

Deletes a virtual cluster.

**Synopsis:**
```bash
aws emr-containers delete-virtual-cluster \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Virtual cluster ID to delete |

**Output Schema:**
```json
{
    "id": "string"
}
```

---

### 11.3 `describe-virtual-cluster`

Describes a virtual cluster.

**Synopsis:**
```bash
aws emr-containers describe-virtual-cluster \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Virtual cluster ID |

**Output Schema:**
```json
{
    "virtualCluster": {
        "id": "string",
        "name": "string",
        "arn": "string",
        "state": "RUNNING|TERMINATING|TERMINATED|ARRESTED",
        "containerProvider": {
            "type": "EKS",
            "id": "string",
            "info": {
                "eksInfo": {
                    "namespace": "string"
                }
            }
        },
        "createdAt": "timestamp",
        "tags": {"string": "string"},
        "securityConfigurationId": "string"
    }
}
```

---

### 11.4 `list-virtual-clusters`

Lists virtual clusters. **Paginated operation.**

**Synopsis:**
```bash
aws emr-containers list-virtual-clusters \
    [--container-provider-id <value>] \
    [--container-provider-type <value>] \
    [--created-after <value>] \
    [--created-before <value>] \
    [--states <value>] \
    [--eks-access-entry-integrated | --no-eks-access-entry-integrated] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-provider-id` | No | string | -- | Filter by EKS cluster ID |
| `--container-provider-type` | No | string | -- | Filter by type: `EKS` |
| `--created-after` | No | timestamp | -- | Filter after this time |
| `--created-before` | No | timestamp | -- | Filter before this time |
| `--states` | No | list(string) | -- | Filter: `RUNNING`, `TERMINATING`, `TERMINATED`, `ARRESTED` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "virtualClusters": [
        {
            "id": "string",
            "name": "string",
            "arn": "string",
            "state": "string",
            "containerProvider": {},
            "createdAt": "timestamp",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```
