# Container Instances

### 5.1 `register-container-instance`

> **Note:** This is an internal API used by the ECS agent. Not typically called directly.

Registers an EC2 instance into the specified cluster. The instance must be running the ECS container agent.

**Synopsis:**
```bash
aws ecs register-container-instance \
    [--cluster <value>] \
    [--instance-identity-document <value>] \
    [--instance-identity-document-signature <value>] \
    [--total-resources <value>] \
    [--version-info <value>] \
    [--container-instance-arn <value>] \
    [--attributes <value>] \
    [--platform-devices <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--instance-identity-document` | No | string | None | EC2 instance identity document |
| `--instance-identity-document-signature` | No | string | None | Signature of the identity document |
| `--total-resources` | No | list | None | Resources available on the instance |
| `--version-info` | No | structure | None | Agent version info |
| `--attributes` | No | list | None | Custom attributes to apply |
| `--tags` | No | list | None | Metadata tags (max 50) |

**Output Schema:**
```json
{
    "containerInstance": {
        "containerInstanceArn": "string",
        "ec2InstanceId": "string",
        "version": "long",
        "versionInfo": {
            "agentVersion": "string",
            "agentHash": "string",
            "dockerVersion": "string"
        },
        "remainingResources": [],
        "registeredResources": [],
        "status": "ACTIVE",
        "agentConnected": true,
        "runningTasksCount": "integer",
        "pendingTasksCount": "integer",
        "attributes": [],
        "registeredAt": "timestamp",
        "tags": []
    }
}
```

---

### 5.2 `deregister-container-instance`

Deregisters an Amazon ECS container instance from the specified cluster. The instance is removed from the cluster but the underlying EC2 instance is not terminated.

**Synopsis:**
```bash
aws ecs deregister-container-instance \
    --container-instance <value> \
    [--cluster <value>] \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-instance` | **Yes** | string | -- | Container instance ID or full ARN |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--force` / `--no-force` | No | boolean | false | Force deregistration even if tasks are running |

**Output Schema:**
```json
{
    "containerInstance": {
        "containerInstanceArn": "string",
        "ec2InstanceId": "string",
        "status": "INACTIVE",
        "runningTasksCount": "integer",
        "pendingTasksCount": "integer",
        "agentConnected": true|false,
        "registeredResources": [],
        "remainingResources": [],
        "attributes": []
    }
}
```

---

### 5.3 `describe-container-instances`

Describes Amazon ECS container instances. Returns detailed information about each container instance.

**Synopsis:**
```bash
aws ecs describe-container-instances \
    --container-instances <value> \
    [--cluster <value>] \
    [--include <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-instances` | **Yes** | list(string) | -- | Up to 100 container instance IDs or ARNs |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--include` | No | list(string) | None | `TAGS`, `CONTAINER_INSTANCE_HEALTH` |

**Output Schema:**
```json
{
    "containerInstances": [
        {
            "containerInstanceArn": "string",
            "ec2InstanceId": "string",
            "capacityProviderName": "string",
            "version": "long",
            "versionInfo": {
                "agentVersion": "string",
                "agentHash": "string",
                "dockerVersion": "string"
            },
            "remainingResources": [
                {
                    "name": "string",
                    "type": "INTEGER|DOUBLE|LONG|STRINGSET",
                    "doubleValue": "double",
                    "longValue": "long",
                    "integerValue": "integer",
                    "stringSetValue": ["string"]
                }
            ],
            "registeredResources": [],
            "status": "REGISTERING|REGISTRATION_FAILED|ACTIVE|INACTIVE|DEREGISTERING|DRAINING",
            "statusReason": "string",
            "agentConnected": true|false,
            "runningTasksCount": "integer",
            "pendingTasksCount": "integer",
            "agentUpdateStatus": "PENDING|STAGING|STAGED|UPDATING|UPDATED|FAILED",
            "attributes": [
                {
                    "name": "string",
                    "value": "string",
                    "targetType": "container-instance",
                    "targetId": "string"
                }
            ],
            "registeredAt": "timestamp",
            "attachments": [],
            "tags": [],
            "healthStatus": {
                "overallStatus": "OK|IMPAIRED|INSUFFICIENT_DATA|INITIALIZING",
                "details": [
                    {
                        "type": "CONTAINER_RUNTIME",
                        "status": "OK|IMPAIRED|INSUFFICIENT_DATA|INITIALIZING",
                        "lastUpdated": "timestamp",
                        "lastStatusChange": "timestamp"
                    }
                ]
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

### 5.4 `list-container-instances`

Returns a list of container instances in a specified cluster. **Paginated operation.**

**Synopsis:**
```bash
aws ecs list-container-instances \
    [--cluster <value>] \
    [--filter <value>] \
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
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--filter` | No | string | None | Filter expression (cluster query language) |
| `--status` | No | string | `ACTIVE` | `ACTIVE`, `DRAINING`, `REGISTERING`, `DEREGISTERING`, `REGISTRATION_FAILED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "containerInstanceArns": ["string"],
    "nextToken": "string"
}
```

---

### 5.5 `update-container-instances-state`

Modifies the status of an Amazon ECS container instance. Used primarily to drain container instances before maintenance or termination.

**Synopsis:**
```bash
aws ecs update-container-instances-state \
    --container-instances <value> \
    --status <value> \
    [--cluster <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-instances` | **Yes** | list(string) | -- | Container instance IDs or ARNs |
| `--status` | **Yes** | string | -- | `ACTIVE` or `DRAINING` |
| `--cluster` | No | string | `default` | Cluster short name or ARN |

**Output Schema:**
```json
{
    "containerInstances": [
        {
            "containerInstanceArn": "string",
            "ec2InstanceId": "string",
            "status": "ACTIVE|DRAINING",
            "runningTasksCount": "integer",
            "pendingTasksCount": "integer",
            "agentConnected": true|false
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

### 5.6 `update-container-agent`

Updates the Amazon ECS container agent on a specified container instance.

**Synopsis:**
```bash
aws ecs update-container-agent \
    --container-instance <value> \
    [--cluster <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-instance` | **Yes** | string | -- | Container instance ID or full ARN |
| `--cluster` | No | string | `default` | Cluster short name or ARN |

**Output Schema:**
```json
{
    "containerInstance": {
        "containerInstanceArn": "string",
        "ec2InstanceId": "string",
        "agentUpdateStatus": "PENDING|STAGING|STAGED|UPDATING|UPDATED|FAILED",
        "versionInfo": {
            "agentVersion": "string",
            "agentHash": "string",
            "dockerVersion": "string"
        }
    }
}
```
