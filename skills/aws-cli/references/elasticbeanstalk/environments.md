# Environments

### 3.1 `create-environment`

Launches an environment for the specified application using the specified configuration.

**Synopsis:**
```bash
aws elasticbeanstalk create-environment \
    --application-name <value> \
    [--environment-name <value>] \
    [--group-name <value>] \
    [--description <value>] \
    [--cname-prefix <value>] \
    [--tier <value>] \
    [--tags <value>] \
    [--version-label <value>] \
    [--template-name <value>] \
    [--solution-stack-name <value>] \
    [--platform-arn <value>] \
    [--option-settings <value>] \
    [--options-to-remove <value>] \
    [--operations-role <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--environment-name` | No | string | -- | Name of the environment (4-40 chars) |
| `--group-name` | No | string | -- | Name of the group for compose environments |
| `--description` | No | string | -- | Description of the environment |
| `--cname-prefix` | No | string | auto-generated | CNAME prefix for the environment URL |
| `--tier` | No | structure | WebServer | Environment tier. Shorthand: `Name=string,Type=string,Version=string` |
| `--tags` | No | list | None | Tags |
| `--version-label` | No | string | -- | Application version to deploy |
| `--template-name` | No | string | -- | Configuration template to use |
| `--solution-stack-name` | No | string | -- | Solution stack name (platform) |
| `--platform-arn` | No | string | -- | Platform ARN |
| `--option-settings` | No | list | None | Configuration options. Shorthand: `ResourceName=string,Namespace=string,OptionName=string,Value=string ...` |
| `--options-to-remove` | No | list | None | Options to remove. Shorthand: `ResourceName=string,Namespace=string,OptionName=string ...` |
| `--operations-role` | No | string | -- | IAM role for environment operations |

**Tier Values:**
| Name | Type | Description |
|------|------|-------------|
| `WebServer` | `Standard` | Web server environment with load balancer |
| `Worker` | `SQS/HTTP` | Worker environment processing SQS messages |

**Output Schema:**
```json
{
    "EnvironmentName": "string",
    "EnvironmentId": "string",
    "ApplicationName": "string",
    "VersionLabel": "string",
    "SolutionStackName": "string",
    "PlatformArn": "string",
    "TemplateName": "string",
    "Description": "string",
    "EndpointURL": "string",
    "CNAME": "string",
    "DateCreated": "timestamp",
    "DateUpdated": "timestamp",
    "Status": "Launching|Updating|Ready|Terminating|Terminated",
    "AbortableOperationInProgress": "boolean",
    "Health": "Green|Yellow|Red|Grey",
    "HealthStatus": "NoData|Unknown|Pending|Ok|Info|Warning|Degraded|Severe|Suspended",
    "Resources": {
        "LoadBalancer": {
            "LoadBalancerName": "string",
            "Domain": "string",
            "Listeners": [
                {
                    "Protocol": "string",
                    "Port": "integer"
                }
            ]
        }
    },
    "Tier": {
        "Name": "string",
        "Type": "string",
        "Version": "string"
    },
    "EnvironmentLinks": [],
    "EnvironmentArn": "string",
    "OperationsRole": "string"
}
```

---

### 3.2 `describe-environments`

Returns descriptions for existing environments. **Paginated operation.**

**Synopsis:**
```bash
aws elasticbeanstalk describe-environments \
    [--application-name <value>] \
    [--version-label <value>] \
    [--environment-ids <value>] \
    [--environment-names <value>] \
    [--include-deleted | --no-include-deleted] \
    [--included-deleted-back-to <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | -- | Filter by application name |
| `--version-label` | No | string | -- | Filter by version label |
| `--environment-ids` | No | list(string) | None | Filter by environment IDs |
| `--environment-names` | No | list(string) | None | Filter by environment names |
| `--include-deleted` | No | boolean | false | Include terminated environments |
| `--included-deleted-back-to` | No | timestamp | -- | Include terminated environments since this date |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Environments": [
        {
            "EnvironmentName": "string",
            "EnvironmentId": "string",
            "ApplicationName": "string",
            "VersionLabel": "string",
            "SolutionStackName": "string",
            "PlatformArn": "string",
            "Description": "string",
            "EndpointURL": "string",
            "CNAME": "string",
            "DateCreated": "timestamp",
            "DateUpdated": "timestamp",
            "Status": "string",
            "Health": "string",
            "HealthStatus": "string",
            "Tier": {},
            "EnvironmentArn": "string",
            "OperationsRole": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.3 `update-environment`

Updates the environment to run a specified version or change configuration option settings.

**Synopsis:**
```bash
aws elasticbeanstalk update-environment \
    [--application-name <value>] \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--group-name <value>] \
    [--description <value>] \
    [--tier <value>] \
    [--version-label <value>] \
    [--template-name <value>] \
    [--solution-stack-name <value>] \
    [--platform-arn <value>] \
    [--option-settings <value>] \
    [--options-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | No | string | -- | ID of the environment to update |
| `--environment-name` | No | string | -- | Name of the environment to update |
| `--application-name` | No | string | -- | Application name (required if no environment-id) |
| `--group-name` | No | string | -- | Group name for compose environments |
| `--description` | No | string | -- | Updated description |
| `--tier` | No | structure | -- | Updated tier |
| `--version-label` | No | string | -- | Application version to deploy |
| `--template-name` | No | string | -- | Configuration template to apply |
| `--solution-stack-name` | No | string | -- | Update solution stack |
| `--platform-arn` | No | string | -- | Update platform |
| `--option-settings` | No | list | None | Configuration options to set |
| `--options-to-remove` | No | list | None | Configuration options to remove |

**Output Schema:**
Same as `create-environment`.

---

### 3.4 `terminate-environment`

Terminates the specified environment.

**Synopsis:**
```bash
aws elasticbeanstalk terminate-environment \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--terminate-resources | --no-terminate-resources] \
    [--force-terminate | --no-force-terminate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | No | string | -- | ID of the environment |
| `--environment-name` | No | string | -- | Name of the environment |
| `--terminate-resources` | No | boolean | true | Terminate underlying resources |
| `--force-terminate` | No | boolean | false | Force terminate even if in updating state |

**Output Schema:**
Same as `create-environment`.

---

### 3.5 `rebuild-environment`

Deletes and recreates all of the AWS resources for the specified environment (ASG, instances, load balancer, etc.).

**Synopsis:**
```bash
aws elasticbeanstalk rebuild-environment \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | No | string | -- | ID of the environment |
| `--environment-name` | No | string | -- | Name of the environment |

**Output Schema:**
```json
{}
```

---

### 3.6 `restart-app-server`

Causes the environment to restart the application container server running on each Amazon EC2 instance.

**Synopsis:**
```bash
aws elasticbeanstalk restart-app-server \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | No | string | -- | ID of the environment |
| `--environment-name` | No | string | -- | Name of the environment |

**Output Schema:**
```json
{}
```

---

### 3.7 `describe-environment-health`

Returns information about the overall health of the specified environment. Requires enhanced health reporting.

**Synopsis:**
```bash
aws elasticbeanstalk describe-environment-health \
    [--environment-name <value>] \
    [--environment-id <value>] \
    [--attribute-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | No | string | -- | Environment name |
| `--environment-id` | No | string | -- | Environment ID |
| `--attribute-names` | No | list(string) | None | Attributes to return: `Status`, `Color`, `Causes`, `ApplicationMetrics`, `InstancesHealth`, `All`, `RefreshedAt` |

**Output Schema:**
```json
{
    "EnvironmentName": "string",
    "HealthStatus": "string",
    "Status": "Green|Yellow|Red|Grey",
    "Color": "string",
    "Causes": ["string"],
    "ApplicationMetrics": {
        "Duration": "integer",
        "RequestCount": "integer",
        "StatusCodes": {
            "Status2xx": "integer",
            "Status3xx": "integer",
            "Status4xx": "integer",
            "Status5xx": "integer"
        },
        "Latency": {
            "P999": "double",
            "P99": "double",
            "P95": "double",
            "P90": "double",
            "P85": "double",
            "P75": "double",
            "P50": "double",
            "P10": "double"
        }
    },
    "InstancesHealth": {
        "NoData": "integer",
        "Unknown": "integer",
        "Pending": "integer",
        "Ok": "integer",
        "Info": "integer",
        "Warning": "integer",
        "Degraded": "integer",
        "Severe": "integer"
    },
    "RefreshedAt": "timestamp"
}
```

---

### 3.8 `describe-instances-health`

Returns health information for instances in the specified environment.

**Synopsis:**
```bash
aws elasticbeanstalk describe-instances-health \
    [--environment-name <value>] \
    [--environment-id <value>] \
    [--attribute-names <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | No | string | -- | Environment name |
| `--environment-id` | No | string | -- | Environment ID |
| `--attribute-names` | No | list(string) | None | Attributes: `HealthStatus`, `Color`, `Causes`, `ApplicationMetrics`, `RefreshedAt`, `LaunchedAt`, `System`, `Deployment`, `AvailabilityZone`, `InstanceType`, `All` |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "InstanceHealthList": [
        {
            "InstanceId": "string",
            "HealthStatus": "string",
            "Color": "string",
            "Causes": ["string"],
            "LaunchedAt": "timestamp",
            "ApplicationMetrics": {},
            "System": {
                "CPUUtilization": {
                    "User": "double",
                    "Nice": "double",
                    "System": "double",
                    "Idle": "double",
                    "IOWait": "double",
                    "IRQ": "double",
                    "SoftIRQ": "double",
                    "Privileged": "double"
                },
                "LoadAverage": ["double"]
            },
            "Deployment": {
                "VersionLabel": "string",
                "DeploymentId": "integer",
                "Status": "string",
                "DeploymentTime": "timestamp"
            },
            "AvailabilityZone": "string",
            "InstanceType": "string"
        }
    ],
    "RefreshedAt": "timestamp",
    "NextToken": "string"
}
```

---

### 3.9 `compose-environments`

Creates and updates environments for a group of applications.

**Synopsis:**
```bash
aws elasticbeanstalk compose-environments \
    [--application-name <value>] \
    [--group-name <value>] \
    [--version-labels <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | -- | Application name |
| `--group-name` | No | string | -- | Group name |
| `--version-labels` | No | list(string) | None | Version labels to deploy |

**Output Schema:**
```json
{
    "Environments": [
        {
            "EnvironmentName": "string",
            "EnvironmentId": "string",
            "ApplicationName": "string",
            "Status": "string",
            "Health": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.10 `swap-environment-cnames`

Swaps the CNAMEs of two environments. Useful for blue/green deployments.

**Synopsis:**
```bash
aws elasticbeanstalk swap-environment-cnames \
    [--source-environment-id <value>] \
    [--source-environment-name <value>] \
    [--destination-environment-id <value>] \
    [--destination-environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-environment-id` | No | string | -- | Source environment ID |
| `--source-environment-name` | No | string | -- | Source environment name |
| `--destination-environment-id` | No | string | -- | Destination environment ID |
| `--destination-environment-name` | No | string | -- | Destination environment name |

**Output Schema:**
```json
{}
```

---

### 3.11 `abort-environment-update`

Cancels in-progress environment configuration update or application version deployment.

**Synopsis:**
```bash
aws elasticbeanstalk abort-environment-update \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | No | string | -- | Environment ID |
| `--environment-name` | No | string | -- | Environment name |

**Output Schema:**
```json
{}
```

---

### 3.12 `describe-environment-resources`

Returns AWS resources for the specified environment.

**Synopsis:**
```bash
aws elasticbeanstalk describe-environment-resources \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | No | string | -- | Environment ID |
| `--environment-name` | No | string | -- | Environment name |

**Output Schema:**
```json
{
    "EnvironmentResources": {
        "EnvironmentName": "string",
        "AutoScalingGroups": [{"Name": "string"}],
        "Instances": [{"Id": "string"}],
        "LaunchConfigurations": [{"Name": "string"}],
        "LaunchTemplates": [{"Id": "string"}],
        "LoadBalancers": [{"Name": "string"}],
        "Triggers": [{"Name": "string"}],
        "Queues": [{"Name": "string", "URL": "string"}]
    }
}
```

---

### 3.13 `list-available-solution-stacks`

Returns a list of the available solution stacks (platforms).

**Synopsis:**
```bash
aws elasticbeanstalk list-available-solution-stacks \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

This command takes no service-specific parameters.

**Output Schema:**
```json
{
    "SolutionStacks": ["string"],
    "SolutionStackDetails": [
        {
            "SolutionStackName": "string",
            "PermittedFileTypes": ["string"]
        }
    ]
}
```
