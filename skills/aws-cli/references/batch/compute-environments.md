# Compute Environments

### 4.1 `create-compute-environment`

Creates a compute environment.

**Synopsis:**
```bash
aws batch create-compute-environment \
    --compute-environment-name <value> \
    --type <value> \
    [--state <value>] \
    [--unmanagedv-cpus <value>] \
    [--compute-resources <value>] \
    [--service-role <value>] \
    [--tags <value>] \
    [--eks-configuration <value>] \
    [--context <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compute-environment-name` | **Yes** | string | -- | Name for the compute environment |
| `--type` | **Yes** | string | -- | Type: `MANAGED`, `UNMANAGED` |
| `--state` | No | string | `ENABLED` | State: `ENABLED`, `DISABLED` |
| `--unmanagedv-cpus` | No | integer | None | Max vCPUs for unmanaged CE |
| `--compute-resources` | No | structure | None | Compute resources config (required for MANAGED) |
| `--service-role` | No | string | None | Service role ARN |
| `--tags` | No | map | None | Tags |
| `--eks-configuration` | No | structure | None | EKS cluster config. Shorthand: `eksClusterArn=string,kubernetesNamespace=string` |
| `--context` | No | string | None | Context string for update sequencing |

**Compute Resources Structure:**
```json
{
    "type": "EC2|SPOT|FARGATE|FARGATE_SPOT",
    "allocationStrategy": "BEST_FIT|BEST_FIT_PROGRESSIVE|SPOT_CAPACITY_OPTIMIZED|SPOT_PRICE_CAPACITY_OPTIMIZED",
    "minvCpus": "integer",
    "maxvCpus": "integer",
    "desiredvCpus": "integer",
    "instanceTypes": ["string"],
    "imageId": "string",
    "subnets": ["string"],
    "securityGroupIds": ["string"],
    "ec2KeyPair": "string",
    "instanceRole": "string",
    "tags": {},
    "placementGroup": "string",
    "bidPercentage": "integer",
    "spotIamFleetRole": "string",
    "launchTemplate": {
        "launchTemplateId": "string",
        "launchTemplateName": "string",
        "version": "string"
    },
    "ec2Configuration": [
        {
            "imageType": "ECS_AL2|ECS_AL2023|ECS_AL2_NVIDIA|ECS_AL2023_NVIDIA",
            "imageIdOverride": "string",
            "imageKubernetesVersion": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "computeEnvironmentName": "string",
    "computeEnvironmentArn": "string"
}
```

---

### 4.2 `update-compute-environment`

Updates a compute environment.

**Synopsis:**
```bash
aws batch update-compute-environment \
    --compute-environment <value> \
    [--state <value>] \
    [--unmanagedv-cpus <value>] \
    [--compute-resources <value>] \
    [--service-role <value>] \
    [--update-policy <value>] \
    [--context <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compute-environment` | **Yes** | string | -- | Compute environment name or ARN |
| `--state` | No | string | None | State: `ENABLED`, `DISABLED` |
| `--unmanagedv-cpus` | No | integer | None | Max vCPUs for unmanaged CE |
| `--compute-resources` | No | structure | None | Updated compute resources (minvCpus, maxvCpus, desiredvCpus, subnets, securityGroupIds, etc.) |
| `--service-role` | No | string | None | Service role ARN |
| `--update-policy` | No | structure | None | Update policy. Shorthand: `terminateJobsOnUpdate=boolean,jobExecutionTimeoutMinutes=long` |
| `--context` | No | string | None | Context string |

**Output Schema:**
```json
{
    "computeEnvironmentName": "string",
    "computeEnvironmentArn": "string"
}
```

---

### 4.3 `delete-compute-environment`

Deletes a compute environment. Must be disabled and have no associated job queues.

**Synopsis:**
```bash
aws batch delete-compute-environment \
    --compute-environment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compute-environment` | **Yes** | string | -- | Compute environment name or ARN |

**Output Schema:**
```json
{}
```

---

### 4.4 `describe-compute-environments`

Describes compute environments. **Paginated operation.**

**Synopsis:**
```bash
aws batch describe-compute-environments \
    [--compute-environments <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compute-environments` | No | list(string) | None | Compute environment names or ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "computeEnvironments": [
        {
            "computeEnvironmentName": "string",
            "computeEnvironmentArn": "string",
            "unmanagedvCpus": "integer",
            "ecsClusterArn": "string",
            "tags": {},
            "type": "MANAGED|UNMANAGED",
            "state": "ENABLED|DISABLED",
            "status": "CREATING|UPDATING|DELETING|DELETED|VALID|INVALID",
            "statusReason": "string",
            "computeResources": {
                "type": "EC2|SPOT|FARGATE|FARGATE_SPOT",
                "allocationStrategy": "string",
                "minvCpus": "integer",
                "maxvCpus": "integer",
                "desiredvCpus": "integer",
                "instanceTypes": ["string"],
                "subnets": ["string"],
                "securityGroupIds": ["string"],
                "instanceRole": "string",
                "tags": {},
                "ec2Configuration": [],
                "launchTemplate": {}
            },
            "serviceRole": "string",
            "updatePolicy": {},
            "eksConfiguration": {
                "eksClusterArn": "string",
                "kubernetesNamespace": "string"
            },
            "containerOrchestrationType": "ECS|EKS",
            "context": "string"
        }
    ],
    "nextToken": "string"
}
```
