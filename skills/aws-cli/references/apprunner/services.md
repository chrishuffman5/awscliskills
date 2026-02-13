# Services

### 1.1 `create-service`

Creates an App Runner service.

**Synopsis:**
```bash
aws apprunner create-service \
    --service-name <value> \
    --source-configuration <value> \
    [--instance-configuration <value>] \
    [--tags <value>] \
    [--encryption-configuration <value>] \
    [--health-check-configuration <value>] \
    [--auto-scaling-configuration-arn <value>] \
    [--network-configuration <value>] \
    [--observability-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name for the service |
| `--source-configuration` | **Yes** | structure | -- | Source configuration (image or code repository) |
| `--instance-configuration` | No | structure | None | Instance config. Shorthand: `Cpu=string,Memory=string,InstanceRoleArn=string` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--encryption-configuration` | No | structure | None | KMS encryption. Shorthand: `KmsKey=string` |
| `--health-check-configuration` | No | structure | None | Health check config |
| `--auto-scaling-configuration-arn` | No | string | None | Auto scaling configuration ARN |
| `--network-configuration` | No | structure | None | Network config (VPC connector, ingress) |
| `--observability-configuration` | No | structure | None | Observability config |

**Output Schema:**
```json
{
    "Service": {
        "ServiceName": "string",
        "ServiceId": "string",
        "ServiceArn": "string",
        "ServiceUrl": "string",
        "CreatedAt": "timestamp",
        "UpdatedAt": "timestamp",
        "DeletedAt": "timestamp",
        "Status": "CREATE_FAILED|RUNNING|DELETED|DELETE_FAILED|PAUSED|OPERATION_IN_PROGRESS",
        "SourceConfiguration": {
            "CodeRepository": {},
            "ImageRepository": {},
            "AutoDeploymentsEnabled": true|false,
            "AuthenticationConfiguration": {}
        },
        "InstanceConfiguration": {
            "Cpu": "string",
            "Memory": "string",
            "InstanceRoleArn": "string"
        },
        "EncryptionConfiguration": {
            "KmsKey": "string"
        },
        "HealthCheckConfiguration": {
            "Protocol": "TCP|HTTP",
            "Path": "string",
            "Interval": "integer",
            "Timeout": "integer",
            "HealthyThreshold": "integer",
            "UnhealthyThreshold": "integer"
        },
        "AutoScalingConfigurationSummary": {
            "AutoScalingConfigurationArn": "string",
            "AutoScalingConfigurationName": "string",
            "AutoScalingConfigurationRevision": "integer"
        },
        "NetworkConfiguration": {
            "EgressConfiguration": {
                "EgressType": "DEFAULT|VPC",
                "VpcConnectorArn": "string"
            },
            "IngressConfiguration": {
                "IsPubliclyAccessible": true|false
            },
            "IpAddressType": "IPV4|DUAL_STACK"
        },
        "ObservabilityConfiguration": {
            "ObservabilityEnabled": true|false,
            "ObservabilityConfigurationArn": "string"
        }
    },
    "OperationId": "string"
}
```

---

### 1.2 `delete-service`

Deletes an App Runner service.

**Synopsis:**
```bash
aws apprunner delete-service \
    --service-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the service to delete |

**Output Schema:**
```json
{
    "Service": {
        "ServiceName": "string",
        "ServiceArn": "string",
        "Status": "OPERATION_IN_PROGRESS"
    },
    "OperationId": "string"
}
```

---

### 1.3 `describe-service`

Returns a full description of an App Runner service.

**Synopsis:**
```bash
aws apprunner describe-service \
    --service-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the service |

**Output Schema:**
```json
{
    "Service": {
        "ServiceName": "string",
        "ServiceId": "string",
        "ServiceArn": "string",
        "ServiceUrl": "string",
        "Status": "CREATE_FAILED|RUNNING|DELETED|DELETE_FAILED|PAUSED|OPERATION_IN_PROGRESS",
        "SourceConfiguration": {},
        "InstanceConfiguration": {},
        "HealthCheckConfiguration": {},
        "AutoScalingConfigurationSummary": {},
        "NetworkConfiguration": {},
        "ObservabilityConfiguration": {},
        "CreatedAt": "timestamp",
        "UpdatedAt": "timestamp"
    }
}
```

---

### 1.4 `list-services`

Lists App Runner services. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner list-services \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ServiceSummaryList": [
        {
            "ServiceName": "string",
            "ServiceId": "string",
            "ServiceArn": "string",
            "ServiceUrl": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "Status": "CREATE_FAILED|RUNNING|DELETED|DELETE_FAILED|PAUSED|OPERATION_IN_PROGRESS"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-service`

Updates the configuration of an App Runner service.

**Synopsis:**
```bash
aws apprunner update-service \
    --service-arn <value> \
    [--source-configuration <value>] \
    [--instance-configuration <value>] \
    [--auto-scaling-configuration-arn <value>] \
    [--health-check-configuration <value>] \
    [--network-configuration <value>] \
    [--observability-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the service to update |
| `--source-configuration` | No | structure | None | Updated source configuration |
| `--instance-configuration` | No | structure | None | Updated instance config |
| `--auto-scaling-configuration-arn` | No | string | None | Auto scaling configuration ARN |
| `--health-check-configuration` | No | structure | None | Updated health check config |
| `--network-configuration` | No | structure | None | Updated network config |
| `--observability-configuration` | No | structure | None | Updated observability config |

**Output Schema:**
```json
{
    "Service": {
        "ServiceName": "string",
        "ServiceArn": "string",
        "Status": "OPERATION_IN_PROGRESS"
    },
    "OperationId": "string"
}
```

---

### 1.6 `pause-service`

Pauses a running App Runner service. Paused services do not incur compute charges.

**Synopsis:**
```bash
aws apprunner pause-service \
    --service-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the service to pause |

**Output Schema:**
```json
{
    "Service": {
        "ServiceName": "string",
        "ServiceArn": "string",
        "Status": "OPERATION_IN_PROGRESS"
    },
    "OperationId": "string"
}
```

---

### 1.7 `resume-service`

Resumes a paused App Runner service.

**Synopsis:**
```bash
aws apprunner resume-service \
    --service-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the service to resume |

**Output Schema:**
```json
{
    "Service": {
        "ServiceName": "string",
        "ServiceArn": "string",
        "Status": "OPERATION_IN_PROGRESS"
    },
    "OperationId": "string"
}
```

---

### 1.8 `start-deployment`

Triggers a manual deployment for the App Runner service.

**Synopsis:**
```bash
aws apprunner start-deployment \
    --service-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the service |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 1.9 `list-operations`

Lists operations for a service. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner list-operations \
    --service-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the service |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OperationSummaryList": [
        {
            "Id": "string",
            "Type": "START_DEPLOYMENT|CREATE_SERVICE|PAUSE_SERVICE|RESUME_SERVICE|DELETE_SERVICE|UPDATE_SERVICE",
            "Status": "PENDING|IN_PROGRESS|FAILED|SUCCEEDED|ROLLBACK_IN_PROGRESS|ROLLBACK_FAILED|ROLLBACK_SUCCEEDED",
            "TargetArn": "string",
            "StartedAt": "timestamp",
            "EndedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
