# Clusters

### 1.1 `create-cluster`

Creates a new Amazon ECS cluster.

**Synopsis:**
```bash
aws ecs create-cluster \
    [--cluster-name <value>] \
    [--tags <value>] \
    [--settings <value>] \
    [--configuration <value>] \
    [--capacity-providers <value>] \
    [--default-capacity-provider-strategy <value>] \
    [--service-connect-defaults <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | No | string | `default` | Cluster name (up to 255 chars: letters, numbers, hyphens, underscores) |
| `--tags` | No | list | None | Metadata tags (max 50). Shorthand: `key=string,value=string ...` |
| `--settings` | No | list | None | Cluster settings. Structure: `name=containerInsights,value=enhanced\|enabled\|disabled` |
| `--configuration` | No | structure | None | Execute command and managed storage configuration |
| `--capacity-providers` | No | list(string) | None | Capacity provider names to associate (e.g., `FARGATE`, `FARGATE_SPOT`, or custom) |
| `--default-capacity-provider-strategy` | No | list | None | Default strategy. Shorthand: `capacityProvider=string,weight=integer,base=integer ...` |
| `--service-connect-defaults` | No | structure | None | Default Service Connect namespace. Shorthand: `namespace=string` |

**Configuration Structure:**
```json
{
    "executeCommandConfiguration": {
        "kmsKeyId": "string",
        "logging": "NONE|DEFAULT|OVERRIDE",
        "logConfiguration": {
            "cloudWatchLogGroupName": "string",
            "cloudWatchEncryptionEnabled": true|false,
            "s3BucketName": "string",
            "s3EncryptionEnabled": true|false,
            "s3KeyPrefix": "string"
        }
    },
    "managedStorageConfiguration": {
        "kmsKeyId": "string",
        "fargateEphemeralStorageKmsKeyId": "string"
    }
}
```

**Output Schema:**
```json
{
    "cluster": {
        "clusterArn": "string",
        "clusterName": "string",
        "status": "ACTIVE|PROVISIONING|DEPROVISIONING|FAILED|INACTIVE",
        "registeredContainerInstancesCount": "integer",
        "runningTasksCount": "integer",
        "pendingTasksCount": "integer",
        "activeServicesCount": "integer",
        "statistics": [
            {
                "name": "string",
                "value": "string"
            }
        ],
        "tags": [
            {
                "key": "string",
                "value": "string"
            }
        ],
        "settings": [
            {
                "name": "containerInsights",
                "value": "enhanced|enabled|disabled"
            }
        ],
        "capacityProviders": ["string"],
        "defaultCapacityProviderStrategy": [
            {
                "capacityProvider": "string",
                "weight": "integer",
                "base": "integer"
            }
        ],
        "attachments": [
            {
                "id": "string",
                "type": "string",
                "status": "PRECREATED|CREATED|ATTACHING|ATTACHED|DETACHING|DETACHED|DELETED|FAILED",
                "details": [
                    {
                        "name": "string",
                        "value": "string"
                    }
                ]
            }
        ],
        "attachmentsStatus": "UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_FAILED",
        "serviceConnectDefaults": {
            "namespace": "string"
        },
        "configuration": {
            "executeCommandConfiguration": {
                "kmsKeyId": "string",
                "logging": "NONE|DEFAULT|OVERRIDE",
                "logConfiguration": {
                    "cloudWatchLogGroupName": "string",
                    "cloudWatchEncryptionEnabled": true|false,
                    "s3BucketName": "string",
                    "s3EncryptionEnabled": true|false,
                    "s3KeyPrefix": "string"
                }
            },
            "managedStorageConfiguration": {
                "kmsKeyId": "string",
                "fargateEphemeralStorageKmsKeyId": "string"
            }
        }
    }
}
```

---

### 1.2 `delete-cluster`

Deletes the specified cluster. The cluster must be empty (no registered container instances, active tasks, or active services).

**Synopsis:**
```bash
aws ecs delete-cluster \
    --cluster <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Short name or full ARN of the cluster to delete |

**Output Schema:**
```json
{
    "cluster": {
        "clusterArn": "string",
        "clusterName": "string",
        "status": "ACTIVE|PROVISIONING|DEPROVISIONING|FAILED|INACTIVE",
        "registeredContainerInstancesCount": "integer",
        "runningTasksCount": "integer",
        "pendingTasksCount": "integer",
        "activeServicesCount": "integer",
        "statistics": [],
        "tags": [],
        "settings": [],
        "capacityProviders": [],
        "defaultCapacityProviderStrategy": []
    }
}
```

---

### 1.3 `describe-clusters`

Describes one or more of your clusters.

**Synopsis:**
```bash
aws ecs describe-clusters \
    [--clusters <value>] \
    [--include <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--clusters` | No | list(string) | `["default"]` | Up to 100 cluster names or ARNs |
| `--include` | No | list(string) | None | Additional info: `ATTACHMENTS`, `CONFIGURATIONS`, `SETTINGS`, `STATISTICS`, `TAGS` |

**Output Schema:**
```json
{
    "clusters": [
        {
            "clusterArn": "string",
            "clusterName": "string",
            "status": "ACTIVE|PROVISIONING|DEPROVISIONING|FAILED|INACTIVE",
            "registeredContainerInstancesCount": "integer",
            "runningTasksCount": "integer",
            "pendingTasksCount": "integer",
            "activeServicesCount": "integer",
            "statistics": [
                {
                    "name": "string",
                    "value": "string"
                }
            ],
            "tags": [
                {
                    "key": "string",
                    "value": "string"
                }
            ],
            "settings": [
                {
                    "name": "containerInsights",
                    "value": "enhanced|enabled|disabled"
                }
            ],
            "capacityProviders": ["string"],
            "defaultCapacityProviderStrategy": [
                {
                    "capacityProvider": "string",
                    "weight": "integer",
                    "base": "integer"
                }
            ],
            "attachments": [],
            "attachmentsStatus": "string",
            "serviceConnectDefaults": {
                "namespace": "string"
            },
            "configuration": {
                "executeCommandConfiguration": {},
                "managedStorageConfiguration": {}
            }
        }
    ],
    "failures": [
        {
            "arn": "string",
            "reason": "string",
            "detail": "string"
        }
    ]
}
```

---

### 1.4 `list-clusters`

Returns a list of existing clusters. **Paginated operation.**

**Synopsis:**
```bash
aws ecs list-clusters \
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
    "clusterArns": ["string"],
    "nextToken": "string"
}
```

---

### 1.5 `update-cluster`

Updates the cluster configuration. Can modify execute command configuration, Service Connect defaults, and managed storage.

**Synopsis:**
```bash
aws ecs update-cluster \
    --cluster <value> \
    [--settings <value>] \
    [--configuration <value>] \
    [--service-connect-defaults <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Short name or full ARN of the cluster |
| `--settings` | No | list | None | Cluster settings (containerInsights) |
| `--configuration` | No | structure | None | Execute command and managed storage configuration |
| `--service-connect-defaults` | No | structure | None | Service Connect namespace default |

**Output Schema:**
```json
{
    "cluster": {
        "clusterArn": "string",
        "clusterName": "string",
        "status": "string",
        "configuration": {},
        "settings": [],
        "serviceConnectDefaults": {}
    }
}
```

---

### 1.6 `update-cluster-settings`

Modifies the settings for a cluster. Currently supports enabling/disabling CloudWatch Container Insights.

**Synopsis:**
```bash
aws ecs update-cluster-settings \
    --cluster <value> \
    --settings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Short name or full ARN of the cluster |
| `--settings` | **Yes** | list | -- | Cluster settings. Shorthand: `name=containerInsights,value=enhanced\|enabled\|disabled` |

**Output Schema:**
```json
{
    "cluster": {
        "clusterArn": "string",
        "clusterName": "string",
        "status": "string",
        "settings": [
            {
                "name": "containerInsights",
                "value": "enhanced|enabled|disabled"
            }
        ]
    }
}
```

---

### 1.7 `put-cluster-capacity-providers`

Modifies the capacity providers associated with a cluster and updates the default capacity provider strategy.

**Synopsis:**
```bash
aws ecs put-cluster-capacity-providers \
    --cluster <value> \
    --capacity-providers <value> \
    --default-capacity-provider-strategy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Short name or full ARN of the cluster |
| `--capacity-providers` | **Yes** | list(string) | -- | Capacity provider names. Pass empty list to remove all |
| `--default-capacity-provider-strategy` | **Yes** | list | -- | Default strategy. Shorthand: `capacityProvider=string,weight=integer,base=integer ...` |

**Output Schema:**
```json
{
    "cluster": {
        "clusterArn": "string",
        "clusterName": "string",
        "status": "string",
        "capacityProviders": ["string"],
        "defaultCapacityProviderStrategy": [
            {
                "capacityProvider": "string",
                "weight": "integer",
                "base": "integer"
            }
        ]
    }
}
```
