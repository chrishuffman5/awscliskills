# Node Groups

### 2.1 `create-nodegroup`

Creates a managed node group for an Amazon EKS cluster.

**Synopsis:**
```bash
aws eks create-nodegroup \
    --cluster-name <value> \
    --nodegroup-name <value> \
    --node-role <value> \
    --subnets <value> \
    [--scaling-config <value>] \
    [--disk-size <value>] \
    [--instance-types <value>] \
    [--ami-type <value>] \
    [--remote-access <value>] \
    [--labels <value>] \
    [--taints <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--launch-template <value>] \
    [--update-config <value>] \
    [--node-repair-config <value>] \
    [--capacity-type <value>] \
    [--release-version <value>] \
    [--version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | **Yes** | string | -- | Node group name |
| `--node-role` | **Yes** | string | -- | IAM role ARN for the node group |
| `--subnets` | **Yes** | list(string) | -- | Subnet IDs for the nodes |
| `--scaling-config` | No | structure | None | Scaling config. Shorthand: `minSize=integer,maxSize=integer,desiredSize=integer` |
| `--disk-size` | No | integer | 20 | Root disk size in GiB |
| `--instance-types` | No | list(string) | `["t3.medium"]` | EC2 instance types |
| `--ami-type` | No | string | `AL2_x86_64` | AMI type: `AL2_x86_64`, `AL2_x86_64_GPU`, `AL2_ARM_64`, `AL2023_x86_64_STANDARD`, `AL2023_ARM_64_STANDARD`, `BOTTLEROCKET_ARM_64`, `BOTTLEROCKET_x86_64`, `CUSTOM`, `WINDOWS_CORE_2019_x86_64`, `WINDOWS_FULL_2019_x86_64`, `WINDOWS_CORE_2022_x86_64`, `WINDOWS_FULL_2022_x86_64` |
| `--remote-access` | No | structure | None | SSH access config. Shorthand: `ec2SshKey=string,sourceSecurityGroups=string,string` |
| `--labels` | No | map | None | Kubernetes labels as key=value |
| `--taints` | No | list | None | Kubernetes taints. Shorthand: `key=string,value=string,effect=NO_SCHEDULE\|NO_EXECUTE\|PREFER_NO_SCHEDULE ...` |
| `--tags` | No | map | None | Tags as key=value |
| `--client-request-token` | No | string | None | Idempotency token |
| `--launch-template` | No | structure | None | Launch template. Shorthand: `name=string,version=string,id=string` |
| `--update-config` | No | structure | None | Update config. Shorthand: `maxUnavailable=integer,maxUnavailablePercentage=integer` |
| `--node-repair-config` | No | structure | None | Node repair. Shorthand: `enabled=boolean` |
| `--capacity-type` | No | string | `ON_DEMAND` | `ON_DEMAND` or `SPOT` or `CAPACITY_BLOCK` |
| `--release-version` | No | string | latest | AMI release version |
| `--version` | No | string | cluster version | Kubernetes version |

**Output Schema:**
```json
{
    "nodegroup": {
        "nodegroupName": "string",
        "nodegroupArn": "string",
        "clusterName": "string",
        "version": "string",
        "releaseVersion": "string",
        "createdAt": "timestamp",
        "modifiedAt": "timestamp",
        "status": "CREATING|ACTIVE|UPDATING|DELETING|CREATE_FAILED|DELETE_FAILED|DEGRADED",
        "capacityType": "ON_DEMAND|SPOT|CAPACITY_BLOCK",
        "scalingConfig": {
            "minSize": "integer",
            "maxSize": "integer",
            "desiredSize": "integer"
        },
        "instanceTypes": ["string"],
        "subnets": ["string"],
        "remoteAccess": {},
        "amiType": "string",
        "nodeRole": "string",
        "labels": {"string": "string"},
        "taints": [
            {
                "key": "string",
                "value": "string",
                "effect": "NO_SCHEDULE|NO_EXECUTE|PREFER_NO_SCHEDULE"
            }
        ],
        "resources": {
            "autoScalingGroups": [
                {
                    "name": "string"
                }
            ],
            "remoteAccessSecurityGroup": "string"
        },
        "diskSize": "integer",
        "health": {
            "issues": [
                {
                    "code": "string",
                    "message": "string",
                    "resourceIds": ["string"]
                }
            ]
        },
        "updateConfig": {
            "maxUnavailable": "integer",
            "maxUnavailablePercentage": "integer"
        },
        "launchTemplate": {
            "name": "string",
            "version": "string",
            "id": "string"
        },
        "tags": {"string": "string"},
        "nodeRepairConfig": {
            "enabled": true|false
        }
    }
}
```

---

### 2.2 `delete-nodegroup`

Deletes an Amazon EKS node group.

**Synopsis:**
```bash
aws eks delete-nodegroup \
    --cluster-name <value> \
    --nodegroup-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | **Yes** | string | -- | Node group name |

**Output Schema:** Same nodegroup object with status `DELETING`.

---

### 2.3 `describe-nodegroup`

Returns descriptive information about an Amazon EKS node group.

**Synopsis:**
```bash
aws eks describe-nodegroup \
    --cluster-name <value> \
    --nodegroup-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | **Yes** | string | -- | Node group name |

**Output Schema:** Same as `create-nodegroup` output.

---

### 2.4 `list-nodegroups`

Lists the Amazon EKS managed node groups for a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-nodegroups \
    --cluster-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "nodegroups": ["string"],
    "nextToken": "string"
}
```

---

### 2.5 `update-nodegroup-config`

Updates an Amazon EKS managed node group configuration (scaling, labels, taints, update strategy).

**Synopsis:**
```bash
aws eks update-nodegroup-config \
    --cluster-name <value> \
    --nodegroup-name <value> \
    [--labels <value>] \
    [--taints <value>] \
    [--scaling-config <value>] \
    [--update-config <value>] \
    [--node-repair-config <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | **Yes** | string | -- | Node group name |
| `--labels` | No | structure | None | Labels to add/remove. Shorthand: `addOrUpdateLabels={key=value},removeLabels=string,string` |
| `--taints` | No | list | None | Taints to add/remove |
| `--scaling-config` | No | structure | None | Updated scaling config |
| `--update-config` | No | structure | None | Updated update config |
| `--node-repair-config` | No | structure | None | Updated node repair config |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:** Update object (same as cluster update).

---

### 2.6 `update-nodegroup-version`

Updates the Kubernetes version or AMI version of an Amazon EKS managed node group.

**Synopsis:**
```bash
aws eks update-nodegroup-version \
    --cluster-name <value> \
    --nodegroup-name <value> \
    [--version <value>] \
    [--release-version <value>] \
    [--launch-template <value>] \
    [--force | --no-force] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | **Yes** | string | -- | Node group name |
| `--version` | No | string | None | Target Kubernetes version |
| `--release-version` | No | string | latest | Target AMI release version |
| `--launch-template` | No | structure | None | Updated launch template |
| `--force` | No | boolean | false | Force update even if pod disruption budget check fails |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:** Update object (same as cluster update).
