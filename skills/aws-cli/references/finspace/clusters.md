# Clusters

### 3.1 `create-kx-cluster`

Creates a new KX cluster in the specified environment.

**Synopsis:**
```bash
aws finspace create-kx-cluster \
    --environment-id <value> \
    --cluster-name <value> \
    --cluster-type <value> \
    --release-label <value> \
    --az-mode <value> \
    [--availability-zone-id <value>] \
    [--cluster-description <value>] \
    [--capacity-configuration <value>] \
    [--vpc-configuration <value>] \
    [--initialization-script <value>] \
    [--command-line-arguments <value>] \
    [--code <value>] \
    [--execution-role <value>] \
    [--savedown-storage-configuration <value>] \
    [--databases <value>] \
    [--cache-storage-configurations <value>] \
    [--auto-scaling-configuration <value>] \
    [--scaling-group-configuration <value>] \
    [--tickerplant-log-configuration <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-name` | **Yes** | string | -- | Cluster name (3-63 chars) |
| `--cluster-type` | **Yes** | string | -- | Cluster type: `HDB`, `RDB`, `GATEWAY`, `GP`, `TICKERPLANT` |
| `--release-label` | **Yes** | string | -- | Release version label |
| `--az-mode` | **Yes** | string | -- | AZ mode: `SINGLE` or `MULTI` |
| `--availability-zone-id` | No | string | -- | AZ ID (required for SINGLE mode) |
| `--cluster-description` | No | string | None | Description |
| `--capacity-configuration` | No | structure | -- | Node type and count |
| `--vpc-configuration` | No | structure | -- | VPC, subnet, and security group config |
| `--initialization-script` | No | string | None | S3 path to initialization script |
| `--command-line-arguments` | No | list | None | Command-line arguments for kdb+ process |
| `--code` | No | structure | None | Code configuration (S3 path to kdb+ code) |
| `--execution-role` | No | string | -- | IAM role ARN for cluster execution |
| `--savedown-storage-configuration` | No | structure | -- | Savedown storage config |
| `--databases` | No | list | None | Database configurations for the cluster |
| `--cache-storage-configurations` | No | list | None | Cache storage configurations |
| `--auto-scaling-configuration` | No | structure | -- | Auto-scaling configuration |
| `--scaling-group-configuration` | No | structure | -- | Scaling group configuration |
| `--tickerplant-log-configuration` | No | structure | -- | Tickerplant log config |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**Capacity Configuration:**
```json
{
    "nodeType": "string",
    "nodeCount": "integer"
}
```

**Code Configuration:**
```json
{
    "s3Bucket": "string",
    "s3Key": "string",
    "s3ObjectVersion": "string"
}
```

**Database Configuration:**
```json
[
    {
        "databaseName": "string",
        "cacheConfigurations": [
            {
                "cacheType": "CACHE_1000|CACHE_250|CACHE_12",
                "dbPaths": ["string"],
                "dataviewName": "string"
            }
        ],
        "changesetId": "string",
        "dataviewName": "string",
        "dataviewConfiguration": {
            "dataviewName": "string",
            "dataviewVersionId": "string",
            "changesetId": "string",
            "segmentConfigurations": []
        }
    }
]
```

**Output Schema:**
```json
{
    "environmentId": "string",
    "status": "PENDING|CREATING|CREATE_FAILED|RUNNING|UPDATING|DELETING|DELETED|DELETE_FAILED",
    "statusReason": "string",
    "clusterName": "string",
    "clusterType": "HDB|RDB|GATEWAY|GP|TICKERPLANT",
    "databases": [],
    "cacheStorageConfigurations": [],
    "autoScalingConfiguration": {},
    "clusterDescription": "string",
    "capacityConfiguration": {
        "nodeType": "string",
        "nodeCount": "integer"
    },
    "releaseLabel": "string",
    "vpcConfiguration": {
        "vpcId": "string",
        "securityGroupIds": ["string"],
        "subnetIds": ["string"],
        "ipAddressType": "IP_V4"
    },
    "initializationScript": "string",
    "commandLineArguments": [
        {
            "key": "string",
            "value": "string"
        }
    ],
    "code": {
        "s3Bucket": "string",
        "s3Key": "string",
        "s3ObjectVersion": "string"
    },
    "executionRole": "string",
    "lastModifiedTimestamp": "timestamp",
    "savedownStorageConfiguration": {},
    "azMode": "SINGLE|MULTI",
    "availabilityZoneId": "string",
    "createdTimestamp": "timestamp",
    "scalingGroupConfiguration": {},
    "tickerplantLogConfiguration": {}
}
```

---

### 3.2 `delete-kx-cluster`

Deletes a KX cluster.

**Synopsis:**
```bash
aws finspace delete-kx-cluster \
    --environment-id <value> \
    --cluster-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-name` | **Yes** | string | -- | Cluster name to delete |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 3.3 `get-kx-cluster`

Returns information about a specific KX cluster.

**Synopsis:**
```bash
aws finspace get-kx-cluster \
    --environment-id <value> \
    --cluster-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-name` | **Yes** | string | -- | Cluster name |

**Output Schema:** Same as `create-kx-cluster` output, with additional fields for volumes and scaling group details.

---

### 3.4 `list-kx-clusters`

Returns a list of all KX clusters in the specified environment. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-clusters \
    --environment-id <value> \
    [--cluster-type <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-type` | No | string | All | Filter by cluster type |
| `--max-results` | No | integer | None | Maximum results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "kxClusterSummaries": [
        {
            "status": "string",
            "statusReason": "string",
            "clusterName": "string",
            "clusterType": "HDB|RDB|GATEWAY|GP|TICKERPLANT",
            "clusterDescription": "string",
            "releaseLabel": "string",
            "initializationScript": "string",
            "executionRole": "string",
            "azMode": "SINGLE|MULTI",
            "availabilityZoneId": "string",
            "lastModifiedTimestamp": "timestamp",
            "createdTimestamp": "timestamp",
            "volumes": []
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `update-kx-cluster-code-configuration`

Updates the code configuration on a KX cluster. Allows deploying new code to a running cluster.

**Synopsis:**
```bash
aws finspace update-kx-cluster-code-configuration \
    --environment-id <value> \
    --cluster-name <value> \
    [--client-token <value>] \
    [--code <value>] \
    [--initialization-script <value>] \
    [--command-line-arguments <value>] \
    [--deployment-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--client-token` | No | string | Auto | Idempotency token |
| `--code` | No | structure | -- | New code configuration |
| `--initialization-script` | No | string | -- | New initialization script path |
| `--command-line-arguments` | No | list | -- | New command-line arguments |
| `--deployment-configuration` | No | structure | -- | Deployment strategy |

**Deployment Configuration:**
```json
{
    "deploymentStrategy": "NO_RESTART|ROLLING|FORCE"
}
```

**Output:** None (HTTP 200 on success)

---

### 3.6 `update-kx-cluster-databases`

Updates the database caches on a KX cluster. Used to refresh data from the database.

**Synopsis:**
```bash
aws finspace update-kx-cluster-databases \
    --environment-id <value> \
    --cluster-name <value> \
    --databases <value> \
    [--client-token <value>] \
    [--deployment-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--databases` | **Yes** | list | -- | Database configurations to update |
| `--client-token` | No | string | Auto | Idempotency token |
| `--deployment-configuration` | No | structure | -- | Deployment strategy |

**Output:** None (HTTP 200 on success)

---

### 3.7 `delete-kx-cluster-node`

Deletes a specific node from a KX cluster. Useful for removing unhealthy nodes.

**Synopsis:**
```bash
aws finspace delete-kx-cluster-node \
    --environment-id <value> \
    --cluster-name <value> \
    --node-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--node-id` | **Yes** | string | -- | Node ID to delete |

**Output:** None (HTTP 200 on success)

---

### 3.8 `list-kx-cluster-nodes`

Returns a list of all nodes in the specified KX cluster. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-cluster-nodes \
    --environment-id <value> \
    --cluster-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results per page |

**Output Schema:**
```json
{
    "nodes": [
        {
            "nodeId": "string",
            "availabilityZoneId": "string",
            "launchTime": "timestamp",
            "status": "RUNNING|PROVISIONING"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.9 `get-kx-connection-string`

Returns a connection string for connecting to the specified KX cluster.

**Synopsis:**
```bash
aws finspace get-kx-connection-string \
    --environment-id <value> \
    --cluster-name <value> \
    --user-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--user-arn` | **Yes** | string | -- | ARN of the KX user |

**Output Schema:**
```json
{
    "signedConnectionString": "string"
}
```
