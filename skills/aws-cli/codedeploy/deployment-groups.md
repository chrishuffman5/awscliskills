# Deployment Groups

### 2.1 `create-deployment-group`

Creates a deployment group to which application revisions are deployed.

**Synopsis:**
```bash
aws deploy create-deployment-group \
    --application-name <value> \
    --deployment-group-name <value> \
    --service-role-arn <value> \
    [--deployment-config-name <value>] \
    [--ec2-tag-filters <value>] \
    [--on-premises-instance-tag-filters <value>] \
    [--auto-scaling-groups <value>] \
    [--trigger-configurations <value>] \
    [--alarm-configuration <value>] \
    [--auto-rollback-configuration <value>] \
    [--outdated-instances-strategy <value>] \
    [--deployment-style <value>] \
    [--blue-green-deployment-configuration <value>] \
    [--load-balancer-info <value>] \
    [--ec2-tag-set <value>] \
    [--on-premises-tag-set <value>] \
    [--ecs-services <value>] \
    [--tags <value>] \
    [--termination-hook-enabled | --no-termination-hook-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--deployment-group-name` | **Yes** | string | -- | Deployment group name |
| `--service-role-arn` | **Yes** | string | -- | IAM service role ARN for CodeDeploy |
| `--deployment-config-name` | No | string | `CodeDeployDefault.OneAtATime` | Deployment configuration name |
| `--ec2-tag-filters` | No | list | None | EC2 tag filters. Shorthand: `Key=string,Value=string,Type=KEY_ONLY\|VALUE_ONLY\|KEY_AND_VALUE ...` |
| `--on-premises-instance-tag-filters` | No | list | None | On-premises instance tag filters |
| `--auto-scaling-groups` | No | list(string) | None | Auto Scaling group names |
| `--trigger-configurations` | No | list | None | SNS trigger configurations |
| `--alarm-configuration` | No | structure | None | CloudWatch alarm configuration |
| `--auto-rollback-configuration` | No | structure | None | Auto-rollback configuration |
| `--outdated-instances-strategy` | No | string | `UPDATE` | Strategy for outdated instances: `UPDATE`, `IGNORE` |
| `--deployment-style` | No | structure | None | Deployment style. Shorthand: `deploymentType=IN_PLACE\|BLUE_GREEN,deploymentOption=WITH_TRAFFIC_CONTROL\|WITHOUT_TRAFFIC_CONTROL` |
| `--blue-green-deployment-configuration` | No | structure | None | Blue/green deployment configuration |
| `--load-balancer-info` | No | structure | None | Load balancer information |
| `--ec2-tag-set` | No | structure | None | EC2 tag set (groups of tag filters with AND/OR logic) |
| `--on-premises-tag-set` | No | structure | None | On-premises tag set |
| `--ecs-services` | No | list | None | ECS service information. Shorthand: `serviceName=string,clusterName=string ...` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--termination-hook-enabled` | No | boolean | false | Enable termination hook for ASG lifecycle events |

**Auto-Rollback Configuration:**
```json
{
    "enabled": true|false,
    "events": ["DEPLOYMENT_FAILURE", "DEPLOYMENT_STOP_ON_ALARM", "DEPLOYMENT_STOP_ON_REQUEST"]
}
```

**Alarm Configuration:**
```json
{
    "enabled": true|false,
    "ignorePollAlarmFailure": true|false,
    "alarms": [
        {
            "name": "string"
        }
    ]
}
```

**Blue/Green Deployment Configuration:**
```json
{
    "terminateBlueInstancesOnDeploymentSuccess": {
        "action": "TERMINATE|KEEP_ALIVE",
        "terminationWaitTimeInMinutes": "integer"
    },
    "deploymentReadyOption": {
        "actionOnTimeout": "CONTINUE_DEPLOYMENT|STOP_DEPLOYMENT",
        "waitTimeInMinutes": "integer"
    },
    "greenFleetProvisioningOption": {
        "action": "DISCOVER_EXISTING|COPY_AUTO_SCALING_GROUP"
    }
}
```

**Load Balancer Info Structure:**
```json
{
    "elbInfoList": [
        {
            "name": "string"
        }
    ],
    "targetGroupInfoList": [
        {
            "name": "string"
        }
    ],
    "targetGroupPairInfoList": [
        {
            "targetGroups": [
                {
                    "name": "string"
                }
            ],
            "prodTrafficRoute": {
                "listenerArns": ["string"]
            },
            "testTrafficRoute": {
                "listenerArns": ["string"]
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "deploymentGroupId": "string"
}
```

---

### 2.2 `delete-deployment-group`

Deletes a deployment group.

**Synopsis:**
```bash
aws deploy delete-deployment-group \
    --application-name <value> \
    --deployment-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--deployment-group-name` | **Yes** | string | -- | Deployment group name |

**Output Schema:**
```json
{
    "hooksNotCleanedUp": [
        {
            "name": "string",
            "hook": "string"
        }
    ]
}
```

---

### 2.3 `get-deployment-group`

Gets information about a deployment group.

**Synopsis:**
```bash
aws deploy get-deployment-group \
    --application-name <value> \
    --deployment-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--deployment-group-name` | **Yes** | string | -- | Deployment group name |

**Output Schema:**
```json
{
    "deploymentGroupInfo": {
        "applicationName": "string",
        "deploymentGroupId": "string",
        "deploymentGroupName": "string",
        "deploymentConfigName": "string",
        "ec2TagFilters": [
            {
                "Key": "string",
                "Value": "string",
                "Type": "KEY_ONLY|VALUE_ONLY|KEY_AND_VALUE"
            }
        ],
        "onPremisesInstanceTagFilters": [],
        "autoScalingGroups": [
            {
                "name": "string",
                "hook": "string",
                "terminationHook": "string"
            }
        ],
        "serviceRoleArn": "string",
        "targetRevision": {
            "revisionType": "S3|GitHub|String|AppSpecContent",
            "s3Location": { },
            "gitHubLocation": { },
            "string": { },
            "appSpecContent": { }
        },
        "triggerConfigurations": [],
        "alarmConfiguration": { },
        "autoRollbackConfiguration": { },
        "deploymentStyle": {
            "deploymentType": "IN_PLACE|BLUE_GREEN",
            "deploymentOption": "WITH_TRAFFIC_CONTROL|WITHOUT_TRAFFIC_CONTROL"
        },
        "outdatedInstancesStrategy": "UPDATE|IGNORE",
        "blueGreenDeploymentConfiguration": { },
        "loadBalancerInfo": { },
        "lastSuccessfulDeployment": {
            "deploymentId": "string",
            "status": "string",
            "endTime": "timestamp",
            "createTime": "timestamp"
        },
        "lastAttemptedDeployment": {
            "deploymentId": "string",
            "status": "string",
            "endTime": "timestamp",
            "createTime": "timestamp"
        },
        "ec2TagSet": {
            "ec2TagSetList": [[]]
        },
        "onPremisesTagSet": { },
        "computePlatform": "Server|Lambda|ECS",
        "ecsServices": [
            {
                "serviceName": "string",
                "clusterName": "string"
            }
        ],
        "terminationHookEnabled": true|false
    }
}
```

---

### 2.4 `list-deployment-groups`

Lists the deployment groups for an application. **Paginated operation.**

**Synopsis:**
```bash
aws deploy list-deployment-groups \
    --application-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "applicationName": "string",
    "deploymentGroups": ["string"],
    "nextToken": "string"
}
```

---

### 2.5 `update-deployment-group`

Changes information about a deployment group. Takes the same parameters as `create-deployment-group`, using `--current-deployment-group-name` to identify the existing group and optionally `--new-deployment-group-name` to rename it.

**Synopsis:**
```bash
aws deploy update-deployment-group \
    --application-name <value> \
    --current-deployment-group-name <value> \
    [--new-deployment-group-name <value>] \
    [--deployment-config-name <value>] \
    [--ec2-tag-filters <value>] \
    [--on-premises-instance-tag-filters <value>] \
    [--auto-scaling-groups <value>] \
    [--service-role-arn <value>] \
    [--trigger-configurations <value>] \
    [--alarm-configuration <value>] \
    [--auto-rollback-configuration <value>] \
    [--outdated-instances-strategy <value>] \
    [--deployment-style <value>] \
    [--blue-green-deployment-configuration <value>] \
    [--load-balancer-info <value>] \
    [--ec2-tag-set <value>] \
    [--on-premises-tag-set <value>] \
    [--ecs-services <value>] \
    [--termination-hook-enabled | --no-termination-hook-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--current-deployment-group-name` | **Yes** | string | -- | Current deployment group name |
| `--new-deployment-group-name` | No | string | None | New deployment group name |
| All other parameters | No | -- | -- | Same as `create-deployment-group`; only specified values are updated |

**Output Schema:**
```json
{
    "hooksNotCleanedUp": [
        {
            "name": "string",
            "hook": "string"
        }
    ]
}
```

---

### 2.6 `batch-get-deployment-groups`

Gets information about one or more deployment groups.

**Synopsis:**
```bash
aws deploy batch-get-deployment-groups \
    --application-name <value> \
    --deployment-group-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--deployment-group-names` | **Yes** | list(string) | -- | Deployment group names |

**Output Schema:**
```json
{
    "deploymentGroupsInfo": [
        {
            "applicationName": "string",
            "deploymentGroupId": "string",
            "deploymentGroupName": "string",
            "deploymentConfigName": "string",
            "ec2TagFilters": [],
            "autoScalingGroups": [],
            "serviceRoleArn": "string",
            "deploymentStyle": { },
            "computePlatform": "Server|Lambda|ECS",
            "ecsServices": []
        }
    ],
    "errorMessage": "string"
}
```
