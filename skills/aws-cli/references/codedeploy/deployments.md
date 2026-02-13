# Deployments

### 3.1 `create-deployment`

Deploys an application revision through the specified deployment group.

**Synopsis:**
```bash
aws deploy create-deployment \
    --application-name <value> \
    [--deployment-group-name <value>] \
    [--revision <value>] \
    [--deployment-config-name <value>] \
    [--description <value>] \
    [--ignore-application-stop-failures | --no-ignore-application-stop-failures] \
    [--target-instances <value>] \
    [--auto-rollback-configuration <value>] \
    [--update-outdated-instances-only | --no-update-outdated-instances-only] \
    [--file-exists-behavior <value>] \
    [--override-alarm-configuration <value>] \
    [--s3-location <value>] \
    [--github-location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--deployment-group-name` | No | string | None | Deployment group name |
| `--revision` | No | structure | None | Application revision location |
| `--deployment-config-name` | No | string | None | Deployment configuration name |
| `--description` | No | string | None | Deployment description |
| `--ignore-application-stop-failures` | No | boolean | false | Ignore ApplicationStop failures |
| `--target-instances` | No | structure | None | Target instances for the deployment |
| `--auto-rollback-configuration` | No | structure | None | Auto-rollback configuration |
| `--update-outdated-instances-only` | No | boolean | false | Only update outdated instances |
| `--file-exists-behavior` | No | string | `DISALLOW` | Behavior for existing files: `DISALLOW`, `OVERWRITE`, `RETAIN` |
| `--override-alarm-configuration` | No | structure | None | Override alarm configuration |
| `--s3-location` | No | structure | None | S3 revision location. Shorthand: `bucket=string,key=string,bundleType=tar\|tgz\|zip\|YAML\|JSON,version=string,eTag=string` |
| `--github-location` | No | structure | None | GitHub revision location. Shorthand: `repository=string,commitId=string` |

**Revision Structure:**
```json
{
    "revisionType": "S3|GitHub|String|AppSpecContent",
    "s3Location": {
        "bucket": "string",
        "key": "string",
        "bundleType": "tar|tgz|zip|YAML|JSON",
        "version": "string",
        "eTag": "string"
    },
    "gitHubLocation": {
        "repository": "string",
        "commitId": "string"
    },
    "string": {
        "content": "string",
        "sha256": "string"
    },
    "appSpecContent": {
        "content": "string",
        "sha256": "string"
    }
}
```

**Target Instances Structure:**
```json
{
    "tagFilters": [
        {
            "Key": "string",
            "Value": "string",
            "Type": "KEY_ONLY|VALUE_ONLY|KEY_AND_VALUE"
        }
    ],
    "autoScalingGroups": ["string"],
    "ec2TagSet": {
        "ec2TagSetList": [[]]
    }
}
```

**Output Schema:**
```json
{
    "deploymentId": "string"
}
```

---

### 3.2 `get-deployment`

Gets information about a deployment.

**Synopsis:**
```bash
aws deploy get-deployment \
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
    "deploymentInfo": {
        "applicationName": "string",
        "deploymentGroupName": "string",
        "deploymentConfigName": "string",
        "deploymentId": "string",
        "previousRevision": { },
        "revision": {
            "revisionType": "S3|GitHub|String|AppSpecContent",
            "s3Location": { },
            "gitHubLocation": { },
            "string": { },
            "appSpecContent": { }
        },
        "status": "Created|Queued|InProgress|Baking|Succeeded|Failed|Stopped|Ready",
        "errorInformation": {
            "code": "AGENT_ISSUE|ALARM_ACTIVE|APPLICATION_MISSING|AUTOSCALING_VALIDATION_ERROR|AUTO_SCALING_CONFIGURATION|AUTO_SCALING_IAM_ROLE_PERMISSIONS|CLOUDFORMATION_STACK_FAILURE|CODEDEPLOY_RESOURCE_CANNOT_BE_FOUND|CUSTOMER_APPLICATION_UNHEALTHY|DEPLOYMENT_GROUP_MISSING|ECS_UPDATE_ERROR|ELASTIC_LOAD_BALANCING_INVALID|ELB_INVALID_INSTANCE|HEALTH_CONSTRAINTS|HEALTH_CONSTRAINTS_INVALID|HOOK_EXECUTION_FAILURE|IAM_ROLE_MISSING|IAM_ROLE_PERMISSIONS|INTERNAL_ERROR|INVALID_ECS_SERVICE|INVALID_LAMBDA_CONFIGURATION|INVALID_LAMBDA_FUNCTION|INVALID_REVISION|MANUAL_STOP|MISSING_BLUE_GREEN_DEPLOYMENT_CONFIGURATION|MISSING_ELB_INFORMATION|MISSING_GITHUB_TOKEN|NO_EC2_SUBSCRIPTION|NO_INSTANCES|OVER_MAX_INSTANCES|RESOURCE_LIMIT_EXCEEDED|REVISION_MISSING|THROTTLED|TIMEOUT",
            "message": "string"
        },
        "createTime": "timestamp",
        "startTime": "timestamp",
        "completeTime": "timestamp",
        "deploymentOverview": {
            "Pending": "long",
            "InProgress": "long",
            "Succeeded": "long",
            "Failed": "long",
            "Skipped": "long",
            "Ready": "long"
        },
        "description": "string",
        "creator": "user|autoscaling|codeDeployRollback|CodeDeploy|CodeDeployAutoUpdate",
        "ignoreApplicationStopFailures": true|false,
        "autoRollbackConfiguration": { },
        "updateOutdatedInstancesOnly": true|false,
        "rollbackInfo": {
            "rollbackDeploymentId": "string",
            "rollbackTriggeringDeploymentId": "string",
            "rollbackMessage": "string"
        },
        "deploymentStyle": {
            "deploymentType": "IN_PLACE|BLUE_GREEN",
            "deploymentOption": "WITH_TRAFFIC_CONTROL|WITHOUT_TRAFFIC_CONTROL"
        },
        "targetInstances": { },
        "instanceTerminationWaitTimeStarted": true|false,
        "blueGreenDeploymentConfiguration": { },
        "loadBalancerInfo": { },
        "fileExistsBehavior": "DISALLOW|OVERWRITE|RETAIN",
        "deploymentStatusMessages": ["string"],
        "computePlatform": "Server|Lambda|ECS",
        "externalId": "string",
        "relatedDeployments": {
            "autoUpdateOutdatedInstancesRootDeploymentId": "string",
            "autoUpdateOutdatedInstancesDeploymentIds": ["string"]
        },
        "overrideAlarmConfiguration": { }
    }
}
```

---

### 3.3 `list-deployments`

Lists the deployments in a deployment group. **Paginated operation.**

**Synopsis:**
```bash
aws deploy list-deployments \
    [--application-name <value>] \
    [--deployment-group-name <value>] \
    [--external-id <value>] \
    [--include-only-statuses <value>] \
    [--create-time-range <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | None | Application name |
| `--deployment-group-name` | No | string | None | Deployment group name (requires `--application-name`) |
| `--external-id` | No | string | None | External ID for deployment group |
| `--include-only-statuses` | No | list(string) | None | Filter by status: `Created`, `Queued`, `InProgress`, `Baking`, `Succeeded`, `Failed`, `Stopped`, `Ready` |
| `--create-time-range` | No | structure | None | Time range filter. Shorthand: `start=timestamp,end=timestamp` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "deployments": ["string"],
    "nextToken": "string"
}
```

---

### 3.4 `stop-deployment`

Attempts to stop an in-progress deployment.

**Synopsis:**
```bash
aws deploy stop-deployment \
    --deployment-id <value> \
    [--auto-rollback-enabled | --no-auto-rollback-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-id` | **Yes** | string | -- | Deployment ID |
| `--auto-rollback-enabled` | No | boolean | false | Automatically roll back the deployment |

**Output Schema:**
```json
{
    "status": "Pending|Succeeded",
    "statusMessage": "string"
}
```

---

### 3.5 `batch-get-deployments`

Gets information about one or more deployments.

**Synopsis:**
```bash
aws deploy batch-get-deployments \
    --deployment-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-ids` | **Yes** | list(string) | -- | Deployment IDs (max 25) |

**Output Schema:**
```json
{
    "deploymentsInfo": [
        {
            "applicationName": "string",
            "deploymentGroupName": "string",
            "deploymentConfigName": "string",
            "deploymentId": "string",
            "revision": { },
            "status": "Created|Queued|InProgress|Baking|Succeeded|Failed|Stopped|Ready",
            "createTime": "timestamp",
            "startTime": "timestamp",
            "completeTime": "timestamp",
            "deploymentOverview": { },
            "computePlatform": "Server|Lambda|ECS"
        }
    ]
}
```

---

### 3.6 `continue-deployment`

For blue/green deployments, starts the process of rerouting traffic from instances in the original environment to instances in the replacement environment without waiting for a specified wait time to elapse.

**Synopsis:**
```bash
aws deploy continue-deployment \
    [--deployment-id <value>] \
    [--deployment-wait-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-id` | No | string | None | Deployment ID |
| `--deployment-wait-type` | No | string | None | Wait type: `READY_WAIT`, `TERMINATION_WAIT` |

**Output Schema:**
```json
{}
```
