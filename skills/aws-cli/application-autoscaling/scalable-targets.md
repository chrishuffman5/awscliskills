# Scalable Targets

### 1.1 `register-scalable-target`

Registers or updates a scalable target with Application Auto Scaling.

**Synopsis:**
```bash
aws application-autoscaling register-scalable-target \
    --service-namespace <value> \
    --resource-id <value> \
    --scalable-dimension <value> \
    [--min-capacity <value>] \
    [--max-capacity <value>] \
    [--role-arn <value>] \
    [--suspended-state <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-namespace` | **Yes** | string | -- | Service namespace: `ecs`, `dynamodb`, `rds`, `lambda`, `ec2`, `elasticmapreduce`, `appstream`, `sagemaker`, `custom-resource`, `comprehend`, `cassandra`, `kafka`, `elasticache`, `neptune`, `workspaces` |
| `--resource-id` | **Yes** | string | -- | Resource identifier (format varies by service) |
| `--scalable-dimension` | **Yes** | string | -- | Scalable dimension (e.g., `ecs:service:DesiredCount`) |
| `--min-capacity` | No | integer | 0 | Minimum capacity (required for new registrations) |
| `--max-capacity` | No | integer | None | Maximum capacity (required for new registrations) |
| `--role-arn` | No | string | Service-linked role | IAM role ARN (only for services without SLR) |
| `--suspended-state` | No | structure | None | Suspend/resume scaling activities |
| `--tags` | No | map | None | Tags for the scalable target |

**SuspendedState structure:**
```json
{
    "DynamicScalingInSuspended": true,
    "DynamicScalingOutSuspended": true,
    "ScheduledScalingSuspended": true
}
```

**Output Schema:**
```json
{
    "ScalableTargetARN": "string"
}
```

---

### 1.2 `deregister-scalable-target`

Deregisters a scalable target. Also deletes all associated scaling policies and scheduled actions.

**Synopsis:**
```bash
aws application-autoscaling deregister-scalable-target \
    --service-namespace <value> \
    --resource-id <value> \
    --scalable-dimension <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-namespace` | **Yes** | string | -- | Service namespace |
| `--resource-id` | **Yes** | string | -- | Resource identifier |
| `--scalable-dimension` | **Yes** | string | -- | Scalable dimension |

**Output:** None

---

### 1.3 `describe-scalable-targets`

Describes registered scalable targets. **Paginated operation.**

**Synopsis:**
```bash
aws application-autoscaling describe-scalable-targets \
    --service-namespace <value> \
    [--resource-ids <value>] \
    [--scalable-dimension <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-namespace` | **Yes** | string | -- | Service namespace |
| `--resource-ids` | No | list | None | Resource IDs to filter (max 50) |
| `--scalable-dimension` | No | string | None | Filter by scalable dimension |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "ScalableTargets": [
        {
            "ServiceNamespace": "string",
            "ResourceId": "string",
            "ScalableDimension": "string",
            "MinCapacity": "integer",
            "MaxCapacity": "integer",
            "PredictedCapacity": "integer",
            "RoleARN": "string",
            "CreationTime": "timestamp",
            "SuspendedState": {
                "DynamicScalingInSuspended": "boolean",
                "DynamicScalingOutSuspended": "boolean",
                "ScheduledScalingSuspended": "boolean"
            },
            "ScalableTargetARN": "string"
        }
    ],
    "NextToken": "string"
}
```
