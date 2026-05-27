# Capacity Providers

### 6.1 `create-capacity-provider`

Creates a new capacity provider. Capacity providers are associated with clusters and used in capacity provider strategies.

**Synopsis:**
```bash
aws ecs create-capacity-provider \
    --name <value> \
    [--auto-scaling-group-provider <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--name` | string | Capacity provider name (up to 255 chars). Cannot start with `aws`, `ecs`, or `fargate` |

**Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--auto-scaling-group-provider` | structure | None | Auto Scaling group configuration |
| `--tags` | list | None | Metadata tags (max 50) |

**Auto Scaling Group Provider Structure:**
```json
{
    "autoScalingGroupArn": "string",
    "managedScaling": {
        "status": "ENABLED|DISABLED",
        "targetCapacity": "integer (1-100)",
        "minimumScalingStepSize": "integer (1-10000)",
        "maximumScalingStepSize": "integer (1-10000)",
        "instanceWarmupPeriod": "integer (0-10000)"
    },
    "managedTerminationProtection": "ENABLED|DISABLED",
    "managedDraining": "ENABLED|DISABLED"
}
```

**Output Schema:**
```json
{
    "capacityProvider": {
        "capacityProviderArn": "string",
        "name": "string",
        "status": "ACTIVE|INACTIVE",
        "autoScalingGroupProvider": {
            "autoScalingGroupArn": "string",
            "managedScaling": {
                "status": "ENABLED|DISABLED",
                "targetCapacity": "integer",
                "minimumScalingStepSize": "integer",
                "maximumScalingStepSize": "integer",
                "instanceWarmupPeriod": "integer"
            },
            "managedTerminationProtection": "ENABLED|DISABLED",
            "managedDraining": "ENABLED|DISABLED"
        },
        "updateStatus": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|DELETE_IN_PROGRESS|DELETE_COMPLETE|DELETE_FAILED|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_FAILED",
        "updateStatusReason": "string",
        "tags": []
    }
}
```

---

### 6.2 `delete-capacity-provider`

Deletes the specified capacity provider. Must be disassociated from all clusters first.

**Synopsis:**
```bash
aws ecs delete-capacity-provider \
    --capacity-provider <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--capacity-provider` | **Yes** | string | -- | Short name or full ARN of the capacity provider |

**Output Schema:**
```json
{
    "capacityProvider": {
        "capacityProviderArn": "string",
        "name": "string",
        "status": "INACTIVE",
        "updateStatus": "DELETE_IN_PROGRESS"
    }
}
```

---

### 6.3 `describe-capacity-providers`

Describes one or more capacity providers.

**Synopsis:**
```bash
aws ecs describe-capacity-providers \
    [--capacity-providers <value>] \
    [--include <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--capacity-providers` | No | list(string) | all | Short names or ARNs of capacity providers |
| `--include` | No | list(string) | None | Additional info: `TAGS` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "capacityProviders": [
        {
            "capacityProviderArn": "string",
            "name": "string",
            "status": "ACTIVE|INACTIVE",
            "autoScalingGroupProvider": {
                "autoScalingGroupArn": "string",
                "managedScaling": {
                    "status": "ENABLED|DISABLED",
                    "targetCapacity": "integer",
                    "minimumScalingStepSize": "integer",
                    "maximumScalingStepSize": "integer",
                    "instanceWarmupPeriod": "integer"
                },
                "managedTerminationProtection": "ENABLED|DISABLED",
                "managedDraining": "ENABLED|DISABLED"
            },
            "updateStatus": "string",
            "updateStatusReason": "string",
            "tags": []
        }
    ],
    "failures": [
        {
            "arn": "string",
            "reason": "string",
            "detail": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.4 `update-capacity-provider`

Modifies the parameters for a capacity provider.

**Synopsis:**
```bash
aws ecs update-capacity-provider \
    --name <value> \
    --auto-scaling-group-provider <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Capacity provider name |
| `--auto-scaling-group-provider` | **Yes** | structure | -- | Updated Auto Scaling group provider config (only `managedScaling`, `managedTerminationProtection`, `managedDraining` can be updated) |

**Output Schema:**
```json
{
    "capacityProvider": {
        "capacityProviderArn": "string",
        "name": "string",
        "status": "ACTIVE",
        "autoScalingGroupProvider": {
            "autoScalingGroupArn": "string",
            "managedScaling": {},
            "managedTerminationProtection": "ENABLED|DISABLED",
            "managedDraining": "ENABLED|DISABLED"
        },
        "updateStatus": "UPDATE_IN_PROGRESS"
    }
}
```
