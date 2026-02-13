# Task Sets

Task sets are used with services that use `CODE_DEPLOY` or `EXTERNAL` deployment controllers.

### 7.1 `create-task-set`

Create a task set in the specified cluster and service.

**Synopsis:**
```bash
aws ecs create-task-set \
    --service <value> \
    --cluster <value> \
    --task-definition <value> \
    [--external-id <value>] \
    [--network-configuration <value>] \
    [--load-balancers <value>] \
    [--service-registries <value>] \
    [--launch-type <value>] \
    [--capacity-provider-strategy <value>] \
    [--platform-version <value>] \
    [--scale <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--service` | string | Service name or ARN |
| `--cluster` | string | Cluster short name or ARN |
| `--task-definition` | string | Task definition `family:revision` or ARN |

**Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--external-id` | string | None | External identifier for the task set |
| `--network-configuration` | structure | None | VPC configuration (required for `awsvpc` mode) |
| `--load-balancers` | list | None | Load balancer configuration |
| `--service-registries` | list | None | Service discovery registries |
| `--launch-type` | string | None | `EC2`, `FARGATE`, `EXTERNAL` |
| `--capacity-provider-strategy` | list | None | Capacity provider strategy |
| `--platform-version` | string | `LATEST` | Fargate platform version |
| `--scale` | structure | `{value: 100, unit: PERCENT}` | Percentage of desired tasks: `value=double,unit=PERCENT` |
| `--client-token` | string | None | Idempotency token (max 36 chars) |
| `--tags` | list | None | Metadata tags (max 50) |

**Output Schema:**
```json
{
    "taskSet": {
        "id": "string",
        "taskSetArn": "string",
        "serviceArn": "string",
        "clusterArn": "string",
        "startedBy": "string",
        "externalId": "string",
        "status": "PRIMARY|ACTIVE|DRAINING",
        "taskDefinition": "string",
        "computedDesiredCount": "integer",
        "pendingCount": "integer",
        "runningCount": "integer",
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "launchType": "EC2|FARGATE|EXTERNAL",
        "capacityProviderStrategy": [],
        "platformVersion": "string",
        "networkConfiguration": {},
        "loadBalancers": [],
        "serviceRegistries": [],
        "scale": {
            "value": "double",
            "unit": "PERCENT"
        },
        "stabilityStatus": "STEADY_STATE|STABILIZING",
        "stabilityStatusAt": "timestamp",
        "tags": []
    }
}
```

---

### 7.2 `delete-task-set`

Deletes a specified task set within a service.

**Synopsis:**
```bash
aws ecs delete-task-set \
    --cluster <value> \
    --service <value> \
    --task-set <value> \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Cluster short name or ARN |
| `--service` | **Yes** | string | -- | Service name or ARN |
| `--task-set` | **Yes** | string | -- | Task set ID or full ARN |
| `--force` / `--no-force` | No | boolean | false | Force delete even if not scaled to zero |

**Output Schema:**
```json
{
    "taskSet": {
        "id": "string",
        "taskSetArn": "string",
        "status": "DRAINING",
        "taskDefinition": "string",
        "computedDesiredCount": "integer",
        "runningCount": "integer"
    }
}
```

---

### 7.3 `describe-task-sets`

Describes the task sets in the specified cluster and service.

**Synopsis:**
```bash
aws ecs describe-task-sets \
    --cluster <value> \
    --service <value> \
    [--task-sets <value>] \
    [--include <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Cluster short name or ARN |
| `--service` | **Yes** | string | -- | Service name or ARN |
| `--task-sets` | No | list(string) | all | Task set IDs or ARNs |
| `--include` | No | list(string) | None | Additional info: `TAGS` |

**Output Schema:**
```json
{
    "taskSets": [
        {
            "id": "string",
            "taskSetArn": "string",
            "serviceArn": "string",
            "clusterArn": "string",
            "status": "PRIMARY|ACTIVE|DRAINING",
            "taskDefinition": "string",
            "computedDesiredCount": "integer",
            "pendingCount": "integer",
            "runningCount": "integer",
            "launchType": "string",
            "networkConfiguration": {},
            "loadBalancers": [],
            "scale": {
                "value": "double",
                "unit": "PERCENT"
            },
            "stabilityStatus": "STEADY_STATE|STABILIZING",
            "tags": []
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

### 7.4 `update-task-set`

Modifies the scale of a task set. Only the `--scale` parameter can be updated.

**Synopsis:**
```bash
aws ecs update-task-set \
    --cluster <value> \
    --service <value> \
    --task-set <value> \
    --scale <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Cluster short name or ARN |
| `--service` | **Yes** | string | -- | Service name or ARN |
| `--task-set` | **Yes** | string | -- | Task set ID or full ARN |
| `--scale` | **Yes** | structure | -- | Scale percentage: `value=double,unit=PERCENT` (0-100) |

**Output Schema:**
```json
{
    "taskSet": {
        "id": "string",
        "taskSetArn": "string",
        "status": "string",
        "taskDefinition": "string",
        "computedDesiredCount": "integer",
        "scale": {
            "value": "double",
            "unit": "PERCENT"
        },
        "stabilityStatus": "STEADY_STATE|STABILIZING"
    }
}
```
