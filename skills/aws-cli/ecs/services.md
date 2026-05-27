# Services

### 2.1 `create-service`

Creates a new ECS service. Services maintain a specified number of running task instances.

**Synopsis:**
```bash
aws ecs create-service \
    --service-name <value> \
    [--cluster <value>] \
    [--task-definition <value>] \
    [--desired-count <value>] \
    [--launch-type <value>] \
    [--capacity-provider-strategy <value>] \
    [--platform-version <value>] \
    [--scheduling-strategy <value>] \
    [--deployment-controller <value>] \
    [--deployment-configuration <value>] \
    [--load-balancers <value>] \
    [--service-registries <value>] \
    [--network-configuration <value>] \
    [--placement-constraints <value>] \
    [--placement-strategy <value>] \
    [--health-check-grace-period-seconds <value>] \
    [--role <value>] \
    [--tags <value>] \
    [--enable-ecs-managed-tags | --no-enable-ecs-managed-tags] \
    [--propagate-tags <value>] \
    [--enable-execute-command | --disable-execute-command] \
    [--service-connect-configuration <value>] \
    [--volume-configurations <value>] \
    [--vpc-lattice-configurations <value>] \
    [--availability-zone-rebalancing <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--service-name` | string | Service name (up to 255 chars, unique within cluster) |

**Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--cluster` | string | `default` | Cluster short name or ARN |
| `--task-definition` | string | None | Task definition `family:revision` or full ARN |
| `--desired-count` | integer | None | Number of task instances (required for REPLICA scheduling) |
| `--launch-type` | string | None | `EC2`, `FARGATE`, `EXTERNAL`, `MANAGED_INSTANCES` |
| `--capacity-provider-strategy` | list | None | Capacity provider strategy (max 20 providers). Shorthand: `capacityProvider=string,weight=integer,base=integer ...` |
| `--platform-version` | string | `LATEST` | Fargate platform version |
| `--scheduling-strategy` | string | `REPLICA` | `REPLICA` or `DAEMON` |
| `--deployment-controller` | structure | `{type: ECS}` | `type`: `ECS`, `CODE_DEPLOY`, `EXTERNAL` |
| `--deployment-configuration` | structure | None | Deployment behavior (see structure below) |
| `--load-balancers` | list | None | Load balancer configuration |
| `--service-registries` | list | None | Cloud Map service discovery registries |
| `--network-configuration` | structure | None | VPC configuration (required for `awsvpc` network mode) |
| `--placement-constraints` | list | None | Placement constraints (max 10) |
| `--placement-strategy` | list | None | Placement strategies (max 5) |
| `--health-check-grace-period-seconds` | integer | 0 | Seconds to ignore health checks after task start |
| `--role` | string | None | IAM role ARN for load balancer calls |
| `--tags` | list | None | Metadata tags (max 50) |
| `--enable-ecs-managed-tags` | boolean | false | Enable ECS managed tags |
| `--propagate-tags` | string | `NONE` | `TASK_DEFINITION`, `SERVICE`, `NONE` |
| `--enable-execute-command` | boolean | false | Enable ECS Exec |
| `--service-connect-configuration` | structure | None | Service Connect configuration |
| `--volume-configurations` | list | None | EBS volume configurations |
| `--availability-zone-rebalancing` | string | None | `ENABLED` or `DISABLED` |
| `--client-token` | string | None | Idempotency token (unique, case-sensitive) |

**Deployment Configuration Structure:**
```json
{
    "deploymentCircuitBreaker": {
        "enable": true|false,
        "rollback": true|false
    },
    "maximumPercent": 200,
    "minimumHealthyPercent": 100,
    "alarms": {
        "alarmNames": ["string"],
        "rollback": true|false,
        "enable": true|false
    }
}
```

**Network Configuration Structure:**
```json
{
    "awsvpcConfiguration": {
        "subnets": ["string"],
        "securityGroups": ["string"],
        "assignPublicIp": "ENABLED|DISABLED"
    }
}
```

**Load Balancer Structure:**
```json
[
    {
        "targetGroupArn": "string",
        "loadBalancerName": "string",
        "containerName": "string",
        "containerPort": "integer"
    }
]
```

**Placement Constraint Structure:**
```json
[
    {
        "type": "distinctInstance|memberOf",
        "expression": "string"
    }
]
```

**Placement Strategy Structure:**
```json
[
    {
        "type": "random|spread|binpack",
        "field": "string"
    }
]
```

**Output Schema:**
```json
{
    "service": {
        "serviceArn": "string",
        "serviceName": "string",
        "clusterArn": "string",
        "loadBalancers": [],
        "serviceRegistries": [],
        "status": "ACTIVE|DRAINING|INACTIVE",
        "desiredCount": "integer",
        "runningCount": "integer",
        "pendingCount": "integer",
        "launchType": "EC2|FARGATE|EXTERNAL|MANAGED_INSTANCES",
        "capacityProviderStrategy": [],
        "platformVersion": "string",
        "platformFamily": "string",
        "taskDefinition": "string",
        "deploymentConfiguration": {
            "deploymentCircuitBreaker": {
                "enable": true|false,
                "rollback": true|false
            },
            "maximumPercent": "integer",
            "minimumHealthyPercent": "integer"
        },
        "taskSets": [],
        "deployments": [
            {
                "id": "string",
                "status": "PRIMARY|ACTIVE|INACTIVE",
                "taskDefinition": "string",
                "desiredCount": "integer",
                "pendingCount": "integer",
                "runningCount": "integer",
                "failedTasks": "integer",
                "createdAt": "timestamp",
                "updatedAt": "timestamp",
                "launchType": "string",
                "platformVersion": "string",
                "platformFamily": "string",
                "networkConfiguration": {},
                "rolloutState": "COMPLETED|FAILED|IN_PROGRESS",
                "rolloutStateReason": "string"
            }
        ],
        "roleArn": "string",
        "events": [
            {
                "id": "string",
                "createdAt": "timestamp",
                "message": "string"
            }
        ],
        "createdAt": "timestamp",
        "placementConstraints": [],
        "placementStrategy": [],
        "networkConfiguration": {},
        "healthCheckGracePeriodSeconds": "integer",
        "schedulingStrategy": "REPLICA|DAEMON",
        "deploymentController": {
            "type": "ECS|CODE_DEPLOY|EXTERNAL"
        },
        "tags": [],
        "createdBy": "string",
        "enableECSManagedTags": true|false,
        "propagateTags": "TASK_DEFINITION|SERVICE|NONE",
        "enableExecuteCommand": true|false,
        "availabilityZoneRebalancing": "ENABLED|DISABLED"
    }
}
```

---

### 2.2 `delete-service`

Deletes a specified service within a cluster. You can set `--force` to delete a service even if it has not been scaled down to zero tasks.

**Synopsis:**
```bash
aws ecs delete-service \
    --service <value> \
    [--cluster <value>] \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service` | **Yes** | string | -- | Service name or ARN |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--force` / `--no-force` | No | boolean | false | Force delete even if desired count is not zero |

**Output Schema:**
```json
{
    "service": {
        "serviceArn": "string",
        "serviceName": "string",
        "clusterArn": "string",
        "status": "ACTIVE|DRAINING|INACTIVE",
        "desiredCount": "integer",
        "runningCount": "integer",
        "pendingCount": "integer",
        "taskDefinition": "string",
        "deployments": [],
        "events": []
    }
}
```

---

### 2.3 `describe-services`

Describes the specified services running in a cluster.

**Synopsis:**
```bash
aws ecs describe-services \
    --services <value> \
    [--cluster <value>] \
    [--include <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--services` | **Yes** | list(string) | -- | Up to 10 service names or ARNs |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--include` | No | list(string) | None | Additional info: `TAGS` |

**Output Schema:**
```json
{
    "services": [
        {
            "serviceArn": "string",
            "serviceName": "string",
            "clusterArn": "string",
            "status": "ACTIVE|DRAINING|INACTIVE",
            "desiredCount": "integer",
            "runningCount": "integer",
            "pendingCount": "integer",
            "launchType": "EC2|FARGATE|EXTERNAL|MANAGED_INSTANCES",
            "taskDefinition": "string",
            "deploymentConfiguration": {
                "maximumPercent": "integer",
                "minimumHealthyPercent": "integer",
                "deploymentCircuitBreaker": {
                    "enable": true|false,
                    "rollback": true|false
                },
                "strategy": "ROLLING|BLUE_GREEN|LINEAR|CANARY"
            },
            "deployments": [
                {
                    "id": "string",
                    "status": "PRIMARY|ACTIVE|INACTIVE",
                    "taskDefinition": "string",
                    "desiredCount": "integer",
                    "pendingCount": "integer",
                    "runningCount": "integer",
                    "failedTasks": "integer",
                    "createdAt": "timestamp",
                    "updatedAt": "timestamp",
                    "launchType": "string",
                    "platformVersion": "string",
                    "rolloutState": "COMPLETED|FAILED|IN_PROGRESS",
                    "rolloutStateReason": "string"
                }
            ],
            "taskSets": [],
            "loadBalancers": [],
            "serviceRegistries": [],
            "events": [
                {
                    "id": "string",
                    "createdAt": "timestamp",
                    "message": "string"
                }
            ],
            "createdAt": "timestamp",
            "placementConstraints": [],
            "placementStrategy": [],
            "networkConfiguration": {},
            "healthCheckGracePeriodSeconds": "integer",
            "schedulingStrategy": "REPLICA|DAEMON",
            "deploymentController": {
                "type": "ECS|CODE_DEPLOY|EXTERNAL"
            },
            "tags": [],
            "enableECSManagedTags": true|false,
            "propagateTags": "string",
            "enableExecuteCommand": true|false
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

### 2.4 `list-services`

Lists the services that are running in a specified cluster. **Paginated operation.**

**Synopsis:**
```bash
aws ecs list-services \
    [--cluster <value>] \
    [--launch-type <value>] \
    [--scheduling-strategy <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--launch-type` | No | string | None | Filter by launch type: `EC2`, `FARGATE`, `EXTERNAL` |
| `--scheduling-strategy` | No | string | None | Filter by scheduling strategy: `REPLICA`, `DAEMON` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "serviceArns": ["string"],
    "nextToken": "string"
}
```

---

### 2.5 `update-service`

Updates the specified service. Triggers a new deployment when task definition, network configuration, or other deployment-triggering parameters change.

**Synopsis:**
```bash
aws ecs update-service \
    --service <value> \
    [--cluster <value>] \
    [--desired-count <value>] \
    [--task-definition <value>] \
    [--capacity-provider-strategy <value>] \
    [--deployment-configuration <value>] \
    [--network-configuration <value>] \
    [--placement-constraints <value>] \
    [--placement-strategy <value>] \
    [--platform-version <value>] \
    [--force-new-deployment | --no-force-new-deployment] \
    [--health-check-grace-period-seconds <value>] \
    [--enable-execute-command | --disable-execute-command] \
    [--enable-ecs-managed-tags | --no-enable-ecs-managed-tags] \
    [--load-balancers <value>] \
    [--propagate-tags <value>] \
    [--service-registries <value>] \
    [--service-connect-configuration <value>] \
    [--volume-configurations <value>] \
    [--vpc-lattice-configurations <value>] \
    [--availability-zone-rebalancing <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--service` | string | Service name or ARN |

**Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--cluster` | string | `default` | Cluster short name or ARN |
| `--desired-count` | integer | no change | Number of task instances |
| `--task-definition` | string | no change | Task definition `family:revision` or ARN. **Triggers deployment** |
| `--capacity-provider-strategy` | list | no change | Capacity provider strategy |
| `--deployment-configuration` | structure | no change | Deployment behavior |
| `--network-configuration` | structure | no change | VPC configuration. **Triggers deployment** |
| `--placement-constraints` | list | no change | Task placement constraints (max 10) |
| `--placement-strategy` | list | no change | Placement strategies (max 5) |
| `--platform-version` | string | no change | Fargate platform version. **Triggers deployment** |
| `--force-new-deployment` | boolean | false | Force deployment without config change |
| `--health-check-grace-period-seconds` | integer | no change | Health check grace period |
| `--enable-execute-command` | boolean | no change | Enable ECS Exec |
| `--load-balancers` | list | no change | Load balancer configuration. **Triggers deployment** |
| `--service-registries` | list | no change | Service discovery registries. **Triggers deployment** |
| `--service-connect-configuration` | structure | no change | Service Connect config. **Triggers deployment** |
| `--volume-configurations` | list | no change | EBS volume config. **Triggers deployment** |
| `--availability-zone-rebalancing` | string | no change | `ENABLED` or `DISABLED` |

**Output Schema:**
```json
{
    "service": {
        "serviceArn": "string",
        "serviceName": "string",
        "clusterArn": "string",
        "status": "ACTIVE|DRAINING|INACTIVE",
        "desiredCount": "integer",
        "runningCount": "integer",
        "taskDefinition": "string",
        "deployments": [
            {
                "id": "string",
                "status": "PRIMARY|ACTIVE|INACTIVE",
                "desiredCount": "integer",
                "runningCount": "integer",
                "taskDefinition": "string",
                "rolloutState": "COMPLETED|FAILED|IN_PROGRESS"
            }
        ]
    }
}
```

---

### 2.6 `update-service-primary-task-set`

Modifies which task set in a service is the primary task set. Used with `CODE_DEPLOY` or `EXTERNAL` deployment controllers.

**Synopsis:**
```bash
aws ecs update-service-primary-task-set \
    --cluster <value> \
    --service <value> \
    --primary-task-set <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Cluster short name or ARN |
| `--service` | **Yes** | string | -- | Service name or ARN |
| `--primary-task-set` | **Yes** | string | -- | Task set ID or full ARN |

**Output Schema:**
```json
{
    "taskSet": {
        "id": "string",
        "taskSetArn": "string",
        "serviceArn": "string",
        "clusterArn": "string",
        "status": "PRIMARY|ACTIVE|DRAINING",
        "taskDefinition": "string",
        "computedDesiredCount": "integer",
        "pendingCount": "integer",
        "runningCount": "integer",
        "scale": {
            "value": "double",
            "unit": "PERCENT"
        },
        "stabilityStatus": "STEADY_STATE|STABILIZING",
        "stabilityStatusAt": "timestamp"
    }
}
```
