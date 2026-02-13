# Service Deployments

### 9.1 `list-service-deployments`

Returns a list of deployments that changed the service. **Paginated operation.**

**Synopsis:**
```bash
aws ecs list-service-deployments \
    --service <value> \
    [--cluster <value>] \
    [--status <value>] \
    [--created-at <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service` | **Yes** | string | -- | Service name or ARN |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--status` | No | list(string) | None | Filter: `PENDING`, `SUCCESSFUL`, `STOPPED`, `STOP_REQUESTED`, `IN_PROGRESS`, `ROLLBACK_IN_PROGRESS`, `ROLLBACK_SUCCESSFUL`, `ROLLBACK_FAILED` |
| `--created-at` | No | structure | None | Time filter: `before=timestamp,after=timestamp` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "serviceDeployments": [
        {
            "serviceDeploymentArn": "string",
            "serviceArn": "string",
            "clusterArn": "string",
            "createdAt": "timestamp",
            "startedAt": "timestamp",
            "finishedAt": "timestamp",
            "stoppedAt": "timestamp",
            "updatedAt": "timestamp",
            "sourceServiceRevisions": [
                {
                    "arn": "string",
                    "requestedTaskCount": "integer",
                    "runningTaskCount": "integer",
                    "pendingTaskCount": "integer"
                }
            ],
            "targetServiceRevision": {
                "arn": "string",
                "requestedTaskCount": "integer",
                "runningTaskCount": "integer",
                "pendingTaskCount": "integer"
            },
            "status": "string",
            "statusReason": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.2 `describe-service-deployments`

Describes one or more service deployments.

**Synopsis:**
```bash
aws ecs describe-service-deployments \
    --service-deployment-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-deployment-arns` | **Yes** | list(string) | -- | Service deployment ARNs |

**Output Schema:**
```json
{
    "serviceDeployments": [
        {
            "serviceDeploymentArn": "string",
            "serviceArn": "string",
            "clusterArn": "string",
            "createdAt": "timestamp",
            "startedAt": "timestamp",
            "finishedAt": "timestamp",
            "status": "string",
            "statusReason": "string",
            "deploymentConfiguration": {},
            "rollback": {
                "reason": "string",
                "startedAt": "timestamp",
                "serviceRevisionArn": "string"
            },
            "targetServiceRevision": {},
            "sourceServiceRevisions": [],
            "alarms": {},
            "deploymentCircuitBreaker": {}
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

### 9.3 `describe-service-revisions`

Describes one or more service revisions.

**Synopsis:**
```bash
aws ecs describe-service-revisions \
    --service-revision-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-revision-arns` | **Yes** | list(string) | -- | Service revision ARNs |

**Output Schema:**
```json
{
    "serviceRevisions": [
        {
            "serviceRevisionArn": "string",
            "serviceArn": "string",
            "clusterArn": "string",
            "taskDefinition": "string",
            "capacityProviderStrategy": [],
            "launchType": "string",
            "platformVersion": "string",
            "platformFamily": "string",
            "loadBalancers": [],
            "serviceRegistries": [],
            "networkConfiguration": {},
            "containerImages": [
                {
                    "containerName": "string",
                    "imageDigest": "string",
                    "image": "string"
                }
            ],
            "serviceConnectConfiguration": {},
            "volumeConfigurations": [],
            "createdAt": "timestamp",
            "guardDutyEnabled": true|false,
            "fargateEphemeralStorage": {}
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
