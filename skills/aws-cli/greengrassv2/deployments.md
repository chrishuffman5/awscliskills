# Deployments

### 3.1 `create-deployment`

Creates a deployment to a core device or thing group. Replaces previous deployments for the same target.

**Synopsis:**
```bash
aws greengrassv2 create-deployment \
    --target-arn <value> \
    [--deployment-name <value>] \
    [--components <value>] \
    [--iot-job-configuration <value>] \
    [--deployment-policies <value>] \
    [--parent-target-arn <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | **Yes** | string | -- | ARN of the IoT thing or thing group |
| `--deployment-name` | No | string | None | Deployment name (1-256 chars) |
| `--components` | No | map | None | Components to deploy with versions and config |
| `--iot-job-configuration` | No | structure | None | IoT job rollout/abort/timeout config |
| `--deployment-policies` | No | structure | None | Failure handling and update policies |
| `--parent-target-arn` | No | string | None | Parent deployment target (subdeployments) |
| `--tags` | No | map | None | Tags (max 200) |
| `--client-token` | No | string | Auto | Idempotency token (1-64 chars) |

**Components map:**
```json
{
    "com.example.HelloWorld": {
        "componentVersion": "1.0.0",
        "configurationUpdate": {
            "merge": "{\"key\":\"value\"}",
            "reset": ["/path/to/reset"]
        },
        "runWith": {
            "posixUser": "ggc_user:ggc_group",
            "systemResourceLimits": {
                "memory": 102400,
                "cpus": 2.0
            },
            "windowsUser": "ggc_user"
        }
    }
}
```

**Deployment Policies:**
```json
{
    "failureHandlingPolicy": "ROLLBACK|DO_NOTHING",
    "componentUpdatePolicy": {
        "timeoutInSeconds": 60,
        "action": "NOTIFY_COMPONENTS|SKIP_NOTIFY_COMPONENTS"
    },
    "configurationValidationPolicy": {
        "timeoutInSeconds": 60
    }
}
```

**IoT Job Configuration:**
```json
{
    "jobExecutionsRolloutConfig": {
        "maximumPerMinute": 10,
        "exponentialRate": {
            "baseRatePerMinute": 5,
            "incrementFactor": 2.0,
            "rateIncreaseCriteria": {
                "numberOfNotifiedThings": 10,
                "numberOfSucceededThings": 5
            }
        }
    },
    "abortConfig": {
        "criteriaList": [
            {
                "failureType": "FAILED|REJECTED|TIMED_OUT|ALL",
                "action": "CANCEL",
                "thresholdPercentage": 30.0,
                "minNumberOfExecutedThings": 5
            }
        ]
    },
    "timeoutConfig": {
        "inProgressTimeoutInMinutes": 60
    }
}
```

**Output Schema:**
```json
{
    "deploymentId": "string",
    "iotJobId": "string",
    "iotJobArn": "string"
}
```

---

### 3.2 `get-deployment`

Retrieves details about a deployment.

**Synopsis:**
```bash
aws greengrassv2 get-deployment \
    --deployment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-id` | **Yes** | string | -- | Deployment ID |

**Output Schema:**
```json
{
    "targetArn": "string",
    "revisionId": "string",
    "deploymentId": "string",
    "deploymentName": "string",
    "deploymentStatus": "ACTIVE|COMPLETED|CANCELED|FAILED|INACTIVE",
    "iotJobId": "string",
    "iotJobArn": "string",
    "components": {
        "string": {
            "componentVersion": "string",
            "configurationUpdate": {
                "merge": "string",
                "reset": ["string"]
            },
            "runWith": {
                "posixUser": "string",
                "systemResourceLimits": {"memory": "long", "cpus": "double"},
                "windowsUser": "string"
            }
        }
    },
    "deploymentPolicies": {
        "failureHandlingPolicy": "ROLLBACK|DO_NOTHING",
        "componentUpdatePolicy": {
            "timeoutInSeconds": "integer",
            "action": "NOTIFY_COMPONENTS|SKIP_NOTIFY_COMPONENTS"
        },
        "configurationValidationPolicy": {
            "timeoutInSeconds": "integer"
        }
    },
    "iotJobConfiguration": {},
    "creationTimestamp": "timestamp",
    "isLatestForTarget": "boolean",
    "parentTargetArn": "string",
    "tags": {"string": "string"}
}
```

---

### 3.3 `list-deployments`

Lists deployments. **Paginated operation.**

**Synopsis:**
```bash
aws greengrassv2 list-deployments \
    [--target-arn <value>] \
    [--history-filter <value>] \
    [--parent-target-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | No | string | None | Filter by target thing or thing group ARN |
| `--history-filter` | No | string | None | `ALL` or `LATEST_ONLY` |
| `--parent-target-arn` | No | string | None | Filter by parent deployment target |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "deployments": [
        {
            "targetArn": "string",
            "revisionId": "string",
            "deploymentId": "string",
            "deploymentName": "string",
            "creationTimestamp": "timestamp",
            "deploymentStatus": "ACTIVE|COMPLETED|CANCELED|FAILED|INACTIVE",
            "isLatestForTarget": "boolean",
            "parentTargetArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `cancel-deployment`

Cancels a deployment. Only active deployments can be canceled.

**Synopsis:**
```bash
aws greengrassv2 cancel-deployment \
    --deployment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-id` | **Yes** | string | -- | Deployment ID |

**Output Schema:**
```json
{
    "message": "string"
}
```

---

### 3.5 `delete-deployment`

Deletes a deployment. Only inactive deployments can be deleted.

**Synopsis:**
```bash
aws greengrassv2 delete-deployment \
    --deployment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-id` | **Yes** | string | -- | Deployment ID |

**Output:** None

---

### 3.6 `list-effective-deployments`

Lists deployments that apply to a core device. **Paginated operation.**

**Synopsis:**
```bash
aws greengrassv2 list-effective-deployments \
    --core-device-thing-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-device-thing-name` | **Yes** | string | -- | Core device name (1-128 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "effectiveDeployments": [
        {
            "deploymentId": "string",
            "deploymentName": "string",
            "iotJobId": "string",
            "iotJobArn": "string",
            "description": "string",
            "targetArn": "string",
            "coreDeviceExecutionStatus": "IN_PROGRESS|QUEUED|FAILED|COMPLETED|TIMED_OUT|CANCELED|REJECTED|SUCCEEDED",
            "reason": "string",
            "creationTimestamp": "timestamp",
            "modifiedTimestamp": "timestamp",
            "statusDetails": {
                "errorStack": ["string"],
                "errorTypes": ["string"]
            }
        }
    ],
    "nextToken": "string"
}
```
