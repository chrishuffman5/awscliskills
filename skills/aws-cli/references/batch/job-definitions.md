# Job Definitions

### 2.1 `register-job-definition`

Registers a new job definition.

**Synopsis:**
```bash
aws batch register-job-definition \
    --job-definition-name <value> \
    --type <value> \
    [--parameters <value>] \
    [--scheduling-priority <value>] \
    [--container-properties <value>] \
    [--node-properties <value>] \
    [--retry-strategy <value>] \
    [--propagate-tags | --no-propagate-tags] \
    [--timeout <value>] \
    [--tags <value>] \
    [--platform-capabilities <value>] \
    [--eks-properties <value>] \
    [--ecs-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-definition-name` | **Yes** | string | -- | Name for the job definition |
| `--type` | **Yes** | string | -- | Type: `container`, `multinode` |
| `--parameters` | No | map | None | Default parameter substitution values |
| `--scheduling-priority` | No | integer | None | Scheduling priority (0-9999) |
| `--container-properties` | No | structure | None | Container properties (image, vcpus, memory, command, etc.) |
| `--node-properties` | No | structure | None | Multi-node parallel job properties |
| `--retry-strategy` | No | structure | None | Retry strategy. Shorthand: `attempts=integer` |
| `--propagate-tags` | No | boolean | false | Propagate tags to ECS task |
| `--timeout` | No | structure | None | Timeout. Shorthand: `attemptDurationSeconds=integer` |
| `--tags` | No | map | None | Tags |
| `--platform-capabilities` | No | list(string) | None | Platform capabilities: `EC2`, `FARGATE` |
| `--eks-properties` | No | structure | None | EKS properties for EKS-based jobs |
| `--ecs-properties` | No | structure | None | ECS properties for multi-container jobs |

**Container Properties Structure:**
```json
{
    "image": "string",
    "vcpus": "integer",
    "memory": "integer",
    "command": ["string"],
    "jobRoleArn": "string",
    "executionRoleArn": "string",
    "volumes": [
        {
            "host": {"sourcePath": "string"},
            "name": "string",
            "efsVolumeConfiguration": {}
        }
    ],
    "environment": [
        {"name": "string", "value": "string"}
    ],
    "mountPoints": [
        {"containerPath": "string", "readOnly": true|false, "sourceVolume": "string"}
    ],
    "privileged": true|false,
    "ulimits": [],
    "user": "string",
    "resourceRequirements": [
        {"value": "string", "type": "GPU|VCPU|MEMORY"}
    ],
    "logConfiguration": {
        "logDriver": "json-file|syslog|journald|gelf|fluentd|awslogs|splunk",
        "options": {},
        "secretOptions": []
    },
    "secrets": [],
    "networkConfiguration": {
        "assignPublicIp": "ENABLED|DISABLED"
    },
    "fargatePlatformConfiguration": {
        "platformVersion": "string"
    },
    "ephemeralStorage": {
        "sizeInGiB": "integer"
    },
    "runtimePlatform": {
        "operatingSystemFamily": "string",
        "cpuArchitecture": "string"
    }
}
```

**Output Schema:**
```json
{
    "jobDefinitionName": "string",
    "jobDefinitionArn": "string",
    "revision": "integer"
}
```

---

### 2.2 `deregister-job-definition`

Deregisters a job definition. The definition transitions to INACTIVE status.

**Synopsis:**
```bash
aws batch deregister-job-definition \
    --job-definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-definition` | **Yes** | string | -- | Job definition name:revision or ARN |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-job-definitions`

Describes job definitions. **Paginated operation.**

**Synopsis:**
```bash
aws batch describe-job-definitions \
    [--job-definitions <value>] \
    [--job-definition-name <value>] \
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
| `--job-definitions` | No | list(string) | None | Job definition names or ARNs (up to 100) |
| `--job-definition-name` | No | string | None | Job definition name (returns all revisions) |
| `--status` | No | string | None | Filter by status: `ACTIVE`, `INACTIVE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "jobDefinitions": [
        {
            "jobDefinitionName": "string",
            "jobDefinitionArn": "string",
            "revision": "integer",
            "status": "ACTIVE|INACTIVE",
            "type": "container|multinode",
            "schedulingPriority": "integer",
            "parameters": {},
            "retryStrategy": {
                "attempts": "integer",
                "evaluateOnExit": []
            },
            "containerProperties": {
                "image": "string",
                "vcpus": "integer",
                "memory": "integer",
                "command": ["string"],
                "jobRoleArn": "string",
                "executionRoleArn": "string",
                "environment": [],
                "resourceRequirements": [],
                "logConfiguration": {}
            },
            "nodeProperties": {},
            "timeout": {
                "attemptDurationSeconds": "integer"
            },
            "tags": {},
            "propagateTags": true|false,
            "platformCapabilities": ["EC2|FARGATE"],
            "eksProperties": {},
            "ecsProperties": {},
            "containerOrchestrationType": "ECS|EKS"
        }
    ],
    "nextToken": "string"
}
```
