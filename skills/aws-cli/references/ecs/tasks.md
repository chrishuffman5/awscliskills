# Tasks

### 3.1 `run-task`

Starts a new task using the specified task definition. Places tasks using the cluster's default capacity provider strategy or the specified launch type.

**Synopsis:**
```bash
aws ecs run-task \
    --task-definition <value> \
    [--cluster <value>] \
    [--count <value>] \
    [--launch-type <value>] \
    [--capacity-provider-strategy <value>] \
    [--platform-version <value>] \
    [--network-configuration <value>] \
    [--overrides <value>] \
    [--placement-constraints <value>] \
    [--placement-strategy <value>] \
    [--group <value>] \
    [--started-by <value>] \
    [--tags <value>] \
    [--enable-ecs-managed-tags | --no-enable-ecs-managed-tags] \
    [--propagate-tags <value>] \
    [--enable-execute-command | --disable-execute-command] \
    [--volume-configurations <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--task-definition` | string | Task definition `family:revision` or full ARN |

**Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--cluster` | string | `default` | Cluster short name or ARN |
| `--count` | integer | 1 | Number of task instances to run (max 10 per call) |
| `--launch-type` | string | None | `EC2`, `FARGATE`, `EXTERNAL`, `MANAGED_INSTANCES` |
| `--capacity-provider-strategy` | list | None | Capacity provider strategy |
| `--platform-version` | string | `LATEST` | Fargate platform version |
| `--network-configuration` | structure | None | VPC configuration (required for `awsvpc` mode) |
| `--overrides` | structure | None | Container overrides (command, env, cpu, memory) |
| `--placement-constraints` | list | None | Placement constraints (max 10) |
| `--placement-strategy` | list | None | Placement strategies (max 5) |
| `--group` | string | task family | Task group name |
| `--started-by` | string | None | Tag to identify who started the task (max 128 chars) |
| `--tags` | list | None | Metadata tags (max 50) |
| `--enable-ecs-managed-tags` | boolean | false | Enable ECS managed tags |
| `--propagate-tags` | string | `NONE` | `TASK_DEFINITION` or `NONE` |
| `--enable-execute-command` | boolean | false | Enable ECS Exec |
| `--volume-configurations` | list | None | EBS volume configurations |
| `--client-token` | string | None | Idempotency token (max 64 chars) |

**Overrides Structure:**
```json
{
    "containerOverrides": [
        {
            "name": "string",
            "command": ["string"],
            "environment": [
                {
                    "name": "string",
                    "value": "string"
                }
            ],
            "cpu": "integer",
            "memory": "integer",
            "memoryReservation": "integer"
        }
    ],
    "cpu": "string",
    "memory": "string",
    "taskRoleArn": "string",
    "executionRoleArn": "string",
    "ephemeralStorage": {
        "sizeInGiB": "integer"
    }
}
```

**Output Schema:**
```json
{
    "tasks": [
        {
            "taskArn": "string",
            "taskDefinitionArn": "string",
            "clusterArn": "string",
            "containerInstanceArn": "string",
            "lastStatus": "string",
            "desiredStatus": "string",
            "cpu": "string",
            "memory": "string",
            "containers": [
                {
                    "containerArn": "string",
                    "taskArn": "string",
                    "name": "string",
                    "image": "string",
                    "lastStatus": "string",
                    "exitCode": "integer",
                    "reason": "string",
                    "networkBindings": [
                        {
                            "bindIP": "string",
                            "containerPort": "integer",
                            "hostPort": "integer",
                            "protocol": "tcp|udp"
                        }
                    ],
                    "networkInterfaces": [
                        {
                            "attachmentId": "string",
                            "privateIpv4Address": "string",
                            "ipv6Address": "string"
                        }
                    ],
                    "healthStatus": "HEALTHY|UNHEALTHY|UNKNOWN"
                }
            ],
            "startedBy": "string",
            "group": "string",
            "launchType": "EC2|FARGATE|EXTERNAL|MANAGED_INSTANCES",
            "capacityProviderName": "string",
            "platformVersion": "string",
            "connectivity": "CONNECTED|DISCONNECTED",
            "connectivityAt": "timestamp",
            "createdAt": "timestamp",
            "startedAt": "timestamp",
            "stoppedAt": "timestamp",
            "stoppedReason": "string",
            "stopCode": "TaskFailedToStart|EssentialContainerExited|UserInitiated|ServiceSchedulerInitiated|SpotInterruption|TerminationNotice",
            "tags": [],
            "overrides": {},
            "availabilityZone": "string",
            "enableExecuteCommand": true|false,
            "healthStatus": "HEALTHY|UNHEALTHY|UNKNOWN",
            "ephemeralStorage": {
                "sizeInGiB": "integer"
            },
            "version": "long"
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

### 3.2 `start-task`

Starts a new task from the specified task definition on the specified container instance(s). Unlike `run-task`, `start-task` places tasks on specific container instances.

**Synopsis:**
```bash
aws ecs start-task \
    --task-definition <value> \
    --container-instances <value> \
    [--cluster <value>] \
    [--overrides <value>] \
    [--group <value>] \
    [--started-by <value>] \
    [--tags <value>] \
    [--enable-ecs-managed-tags | --no-enable-ecs-managed-tags] \
    [--propagate-tags <value>] \
    [--enable-execute-command | --disable-execute-command] \
    [--volume-configurations <value>] \
    [--network-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--task-definition` | string | Task definition `family:revision` or full ARN |
| `--container-instances` | list(string) | Container instance IDs or ARNs to place tasks on |

**Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--cluster` | string | `default` | Cluster short name or ARN |
| `--overrides` | structure | None | Container overrides |
| `--group` | string | task family | Task group name |
| `--started-by` | string | None | Tag identifying who started the task |
| `--tags` | list | None | Metadata tags (max 50) |
| `--enable-execute-command` | boolean | false | Enable ECS Exec |
| `--network-configuration` | structure | None | VPC configuration |
| `--volume-configurations` | list | None | EBS volume configurations |

**Output Schema:**
```json
{
    "tasks": [
        {
            "taskArn": "string",
            "taskDefinitionArn": "string",
            "clusterArn": "string",
            "containerInstanceArn": "string",
            "lastStatus": "string",
            "desiredStatus": "string",
            "containers": [],
            "startedBy": "string",
            "group": "string"
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

### 3.3 `stop-task`

Stops a running task. When `stop-task` is called, ECS sends a `SIGTERM` to the task, then waits 30 seconds (configurable via `stopTimeout` in task definition) before sending `SIGKILL`.

**Synopsis:**
```bash
aws ecs stop-task \
    --task <value> \
    [--cluster <value>] \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task` | **Yes** | string | -- | Task ID or full ARN |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--reason` | No | string | None | Reason for stopping (visible in `describe-tasks`) |

**Output Schema:**
```json
{
    "task": {
        "taskArn": "string",
        "taskDefinitionArn": "string",
        "clusterArn": "string",
        "lastStatus": "string",
        "desiredStatus": "STOPPED",
        "stoppedReason": "string",
        "containers": [],
        "stoppedAt": "timestamp"
    }
}
```

---

### 3.4 `describe-tasks`

Describes a specified task or tasks.

**Synopsis:**
```bash
aws ecs describe-tasks \
    --tasks <value> \
    [--cluster <value>] \
    [--include <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tasks` | **Yes** | list(string) | -- | Up to 100 task IDs or ARNs |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--include` | No | list(string) | None | Additional info: `TAGS` |

**Output Schema:**
```json
{
    "tasks": [
        {
            "taskArn": "string",
            "taskDefinitionArn": "string",
            "clusterArn": "string",
            "containerInstanceArn": "string",
            "lastStatus": "string",
            "desiredStatus": "string",
            "cpu": "string",
            "memory": "string",
            "containers": [
                {
                    "containerArn": "string",
                    "taskArn": "string",
                    "name": "string",
                    "image": "string",
                    "imageDigest": "string",
                    "runtimeId": "string",
                    "lastStatus": "string",
                    "exitCode": "integer",
                    "reason": "string",
                    "networkBindings": [],
                    "networkInterfaces": [],
                    "healthStatus": "HEALTHY|UNHEALTHY|UNKNOWN",
                    "managedAgents": [
                        {
                            "lastStartedAt": "timestamp",
                            "name": "ExecuteCommandAgent",
                            "reason": "string",
                            "lastStatus": "string"
                        }
                    ]
                }
            ],
            "startedBy": "string",
            "group": "string",
            "launchType": "EC2|FARGATE|EXTERNAL|MANAGED_INSTANCES",
            "capacityProviderName": "string",
            "platformVersion": "string",
            "connectivity": "CONNECTED|DISCONNECTED",
            "createdAt": "timestamp",
            "startedAt": "timestamp",
            "stoppedAt": "timestamp",
            "stoppedReason": "string",
            "stopCode": "string",
            "tags": [],
            "overrides": {},
            "availabilityZone": "string",
            "enableExecuteCommand": true|false,
            "healthStatus": "HEALTHY|UNHEALTHY|UNKNOWN",
            "version": "long",
            "attachments": [],
            "attributes": [],
            "pullStartedAt": "timestamp",
            "pullStoppedAt": "timestamp",
            "executionStoppedAt": "timestamp",
            "ephemeralStorage": {
                "sizeInGiB": "integer"
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

### 3.5 `list-tasks`

Returns a list of tasks. Can be filtered by cluster, container instance, family, service, or desired status. **Paginated operation.**

**Synopsis:**
```bash
aws ecs list-tasks \
    [--cluster <value>] \
    [--container-instance <value>] \
    [--family <value>] \
    [--service-name <value>] \
    [--desired-status <value>] \
    [--launch-type <value>] \
    [--started-by <value>] \
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
| `--container-instance` | No | string | None | Container instance ID or ARN |
| `--family` | No | string | None | Task definition family name |
| `--service-name` | No | string | None | Service name to filter by |
| `--desired-status` | No | string | `RUNNING` | `RUNNING` or `STOPPED` |
| `--launch-type` | No | string | None | `EC2`, `FARGATE`, `EXTERNAL` |
| `--started-by` | No | string | None | `startedBy` value to filter by |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "taskArns": ["string"],
    "nextToken": "string"
}
```
