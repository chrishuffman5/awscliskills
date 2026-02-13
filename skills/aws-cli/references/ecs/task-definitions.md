# Task Definitions

### 4.1 `register-task-definition`

Registers a new task definition from the supplied `family` and `containerDefinitions`.

**Synopsis:**
```bash
aws ecs register-task-definition \
    --family <value> \
    --container-definitions <value> \
    [--task-role-arn <value>] \
    [--execution-role-arn <value>] \
    [--network-mode <value>] \
    [--volumes <value>] \
    [--placement-constraints <value>] \
    [--requires-compatibilities <value>] \
    [--cpu <value>] \
    [--memory <value>] \
    [--tags <value>] \
    [--pid-mode <value>] \
    [--ipc-mode <value>] \
    [--proxy-configuration <value>] \
    [--inference-accelerators <value>] \
    [--ephemeral-storage <value>] \
    [--runtime-platform <value>] \
    [--enable-fault-injection | --no-enable-fault-injection] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--family` | string | Task definition family name (up to 255 chars) |
| `--container-definitions` | list | JSON array of container definitions |

**Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--task-role-arn` | string | None | IAM role ARN for containers to call AWS APIs |
| `--execution-role-arn` | string | None | IAM role ARN for the ECS agent (pull images, send logs) |
| `--network-mode` | string | `bridge` | `bridge`, `host`, `awsvpc`, `none` |
| `--volumes` | list | None | Data volume definitions |
| `--placement-constraints` | list | None | Placement constraints |
| `--requires-compatibilities` | list | None | `EC2`, `FARGATE`, `EXTERNAL` |
| `--cpu` | string | None | Task-level CPU units (e.g., `256`, `512`, `1024`, `2048`, `4096`) |
| `--memory` | string | None | Task-level memory in MiB (e.g., `512`, `1024`, `2048`) |
| `--tags` | list | None | Metadata tags (max 50) |
| `--pid-mode` | string | None | PID namespace: `host` or `task` |
| `--ipc-mode` | string | None | IPC namespace: `host`, `task`, `none` |
| `--proxy-configuration` | structure | None | App Mesh proxy configuration |
| `--inference-accelerators` | list | None | Elastic Inference accelerators |
| `--ephemeral-storage` | structure | None | Ephemeral storage: `sizeInGiB=integer` (21-200 GiB for Fargate) |
| `--runtime-platform` | structure | None | OS/architecture. `cpuArchitecture`: `X86_64\|ARM64`; `operatingSystemFamily`: `LINUX\|WINDOWS_SERVER_*` |
| `--enable-fault-injection` | boolean | false | Enable fault injection testing |

**Container Definition Structure (Key Fields):**
```json
{
    "name": "string",
    "image": "string",
    "cpu": "integer",
    "memory": "integer",
    "memoryReservation": "integer",
    "essential": true|false,
    "portMappings": [
        {
            "containerPort": "integer",
            "hostPort": "integer",
            "protocol": "tcp|udp",
            "name": "string",
            "appProtocol": "http|http2|grpc"
        }
    ],
    "environment": [
        {
            "name": "string",
            "value": "string"
        }
    ],
    "environmentFiles": [
        {
            "value": "string",
            "type": "s3"
        }
    ],
    "secrets": [
        {
            "name": "string",
            "valueFrom": "string"
        }
    ],
    "mountPoints": [
        {
            "sourceVolume": "string",
            "containerPath": "string",
            "readOnly": true|false
        }
    ],
    "volumesFrom": [
        {
            "sourceContainer": "string",
            "readOnly": true|false
        }
    ],
    "logConfiguration": {
        "logDriver": "json-file|syslog|journald|gelf|fluentd|awslogs|splunk|awsfirelens",
        "options": {
            "string": "string"
        },
        "secretOptions": [
            {
                "name": "string",
                "valueFrom": "string"
            }
        ]
    },
    "healthCheck": {
        "command": ["CMD-SHELL", "curl -f http://localhost/ || exit 1"],
        "interval": "integer",
        "timeout": "integer",
        "retries": "integer",
        "startPeriod": "integer"
    },
    "command": ["string"],
    "entryPoint": ["string"],
    "workingDirectory": "string",
    "user": "string",
    "privileged": true|false,
    "readonlyRootFilesystem": true|false,
    "links": ["string"],
    "dockerLabels": {
        "string": "string"
    },
    "ulimits": [
        {
            "name": "string",
            "softLimit": "integer",
            "hardLimit": "integer"
        }
    ],
    "linuxParameters": {
        "capabilities": {
            "add": ["string"],
            "drop": ["string"]
        },
        "devices": [],
        "initProcessEnabled": true|false,
        "sharedMemorySize": "integer",
        "tmpfs": [],
        "maxSwap": "integer",
        "swappiness": "integer"
    },
    "dependsOn": [
        {
            "containerName": "string",
            "condition": "START|COMPLETE|SUCCESS|HEALTHY"
        }
    ],
    "startTimeout": "integer",
    "stopTimeout": "integer",
    "systemControls": [
        {
            "namespace": "string",
            "value": "string"
        }
    ],
    "resourceRequirements": [
        {
            "value": "string",
            "type": "GPU|InferenceAccelerator"
        }
    ],
    "firelensConfiguration": {
        "type": "fluentd|fluentbit",
        "options": {
            "string": "string"
        }
    }
}
```

**Volume Definition Structure:**
```json
{
    "name": "string",
    "host": {
        "sourcePath": "string"
    },
    "dockerVolumeConfiguration": {
        "scope": "task|shared",
        "autoprovision": true|false,
        "driver": "string",
        "driverOpts": {"string": "string"},
        "labels": {"string": "string"}
    },
    "efsVolumeConfiguration": {
        "fileSystemId": "string",
        "rootDirectory": "string",
        "transitEncryption": "ENABLED|DISABLED",
        "transitEncryptionPort": "integer",
        "authorizationConfig": {
            "accessPointId": "string",
            "iam": "ENABLED|DISABLED"
        }
    }
}
```

**Output Schema:**
```json
{
    "taskDefinition": {
        "taskDefinitionArn": "string",
        "containerDefinitions": [],
        "family": "string",
        "taskRoleArn": "string",
        "executionRoleArn": "string",
        "networkMode": "bridge|host|awsvpc|none",
        "revision": "integer",
        "volumes": [],
        "status": "ACTIVE|INACTIVE|DELETE_IN_PROGRESS",
        "requiresAttributes": [
            {
                "name": "string",
                "value": "string",
                "targetType": "container-instance",
                "targetId": "string"
            }
        ],
        "placementConstraints": [],
        "compatibilities": ["EC2", "FARGATE", "EXTERNAL"],
        "requiresCompatibilities": [],
        "cpu": "string",
        "memory": "string",
        "pidMode": "host|task",
        "ipcMode": "host|task|none",
        "proxyConfiguration": {},
        "registeredAt": "timestamp",
        "registeredBy": "string",
        "ephemeralStorage": {
            "sizeInGiB": "integer"
        },
        "runtimePlatform": {
            "cpuArchitecture": "X86_64|ARM64",
            "operatingSystemFamily": "string"
        },
        "enableFaultInjection": true|false
    },
    "tags": []
}
```

---

### 4.2 `deregister-task-definition`

Deregisters the specified task definition by family and revision. Deregistered task definitions remain in `INACTIVE` state and can still be described but cannot be used for new tasks.

**Synopsis:**
```bash
aws ecs deregister-task-definition \
    --task-definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-definition` | **Yes** | string | -- | Task definition `family:revision` or full ARN |

**Output Schema:**
```json
{
    "taskDefinition": {
        "taskDefinitionArn": "string",
        "family": "string",
        "revision": "integer",
        "status": "INACTIVE",
        "containerDefinitions": [],
        "networkMode": "string",
        "cpu": "string",
        "memory": "string"
    }
}
```

---

### 4.3 `describe-task-definition`

Describes a task definition. You can specify a family and revision or the full ARN.

**Synopsis:**
```bash
aws ecs describe-task-definition \
    --task-definition <value> \
    [--include <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-definition` | **Yes** | string | -- | Task definition `family:revision` or full ARN |
| `--include` | No | list(string) | None | Additional info: `TAGS` |

**Output Schema:**
```json
{
    "taskDefinition": {
        "taskDefinitionArn": "string",
        "containerDefinitions": [],
        "family": "string",
        "taskRoleArn": "string",
        "executionRoleArn": "string",
        "networkMode": "bridge|host|awsvpc|none",
        "revision": "integer",
        "volumes": [],
        "status": "ACTIVE|INACTIVE|DELETE_IN_PROGRESS",
        "requiresAttributes": [],
        "placementConstraints": [],
        "compatibilities": [],
        "requiresCompatibilities": [],
        "cpu": "string",
        "memory": "string",
        "registeredAt": "timestamp",
        "registeredBy": "string",
        "runtimePlatform": {},
        "ephemeralStorage": {}
    },
    "tags": []
}
```

---

### 4.4 `list-task-definitions`

Returns a list of task definitions registered in your account. Can be filtered by family. **Paginated operation.**

**Synopsis:**
```bash
aws ecs list-task-definitions \
    [--family-prefix <value>] \
    [--status <value>] \
    [--sort <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--family-prefix` | No | string | None | Filter by family name |
| `--status` | No | string | `ACTIVE` | `ACTIVE`, `INACTIVE`, `DELETE_IN_PROGRESS` |
| `--sort` | No | string | `ASC` | `ASC` or `DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "taskDefinitionArns": ["string"],
    "nextToken": "string"
}
```

---

### 4.5 `list-task-definition-families`

Returns a list of task definition families registered in your account. **Paginated operation.**

**Synopsis:**
```bash
aws ecs list-task-definition-families \
    [--family-prefix <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--family-prefix` | No | string | None | Filter by family name prefix |
| `--status` | No | string | `ACTIVE` | `ACTIVE`, `INACTIVE`, `ALL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "families": ["string"],
    "nextToken": "string"
}
```

---

### 4.6 `delete-task-definitions`

Deletes one or more task definitions. Must be in `INACTIVE` state (deregistered) before deletion.

**Synopsis:**
```bash
aws ecs delete-task-definitions \
    --task-definitions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-definitions` | **Yes** | list(string) | -- | Up to 10 task definition `family:revision` strings or ARNs |

**Output Schema:**
```json
{
    "taskDefinitions": [
        {
            "taskDefinitionArn": "string",
            "family": "string",
            "revision": "integer",
            "status": "DELETE_IN_PROGRESS"
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
