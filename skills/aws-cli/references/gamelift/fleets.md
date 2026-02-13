# Fleets

### 2.1 `create-fleet`

Creates a new EC2 or Anywhere fleet to host game servers.

**Synopsis:**
```bash
aws gamelift create-fleet \
    --name <value> \
    [--description <value>] \
    [--build-id <value>] \
    [--script-id <value>] \
    [--ec2-instance-type <value>] \
    [--ec2-inbound-permissions <value>] \
    [--fleet-type <value>] \
    [--compute-type <value>] \
    [--new-game-session-protection-policy <value>] \
    [--runtime-configuration <value>] \
    [--resource-creation-limit-policy <value>] \
    [--metric-groups <value>] \
    [--peer-vpc-aws-account-id <value>] \
    [--peer-vpc-id <value>] \
    [--instance-role-arn <value>] \
    [--instance-role-credentials-provider <value>] \
    [--certificate-configuration <value>] \
    [--locations <value>] \
    [--tags <value>] \
    [--anywhere-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Descriptive label (1-1024 chars) |
| `--description` | No | string | None | Description (1-1024 chars) |
| `--build-id` | No | string | None | Build ID or ARN for custom game server |
| `--script-id` | No | string | None | Script ID or ARN for Realtime Servers |
| `--ec2-instance-type` | No | string | None | EC2 instance type (e.g., `c5.large`, `m5.large`) |
| `--ec2-inbound-permissions` | No | list | None | Inbound traffic rules (max 50). Shorthand: `FromPort=int,ToPort=int,IpRange=string,Protocol=TCP\|UDP` |
| `--fleet-type` | No | string | `ON_DEMAND` | Instance purchasing: `ON_DEMAND` or `SPOT` |
| `--compute-type` | No | string | `EC2` | Compute type: `EC2` or `ANYWHERE` |
| `--new-game-session-protection-policy` | No | string | `NoProtection` | Game session protection: `NoProtection` or `FullProtection` |
| `--runtime-configuration` | No | structure | None | Server process configuration (JSON) |
| `--resource-creation-limit-policy` | No | structure | None | Game session creation limits. Shorthand: `NewGameSessionsPerCreator=int,PolicyPeriodInMinutes=int` |
| `--metric-groups` | No | list(string) | None | CloudWatch metric group names (max 1) |
| `--peer-vpc-aws-account-id` | No | string | None | VPC peer account ID |
| `--peer-vpc-id` | No | string | None | VPC ID to peer with |
| `--instance-role-arn` | No | string | None | IAM role ARN for fleet instances |
| `--instance-role-credentials-provider` | No | string | None | `SHARED_CREDENTIAL_FILE` (requires SDK 5.x) |
| `--certificate-configuration` | No | structure | None | TLS config. Shorthand: `CertificateType=DISABLED\|GENERATED` |
| `--locations` | No | list | None | Remote locations. Shorthand: `Location=string ...` |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |
| `--anywhere-configuration` | No | structure | None | Anywhere fleet settings. Shorthand: `Cost=string` |

**Runtime Configuration Structure:**
```json
{
    "ServerProcesses": [
        {
            "LaunchPath": "string",
            "Parameters": "string",
            "ConcurrentExecutions": "integer"
        }
    ],
    "MaxConcurrentGameSessionActivations": "integer",
    "GameSessionActivationTimeoutSeconds": "integer"
}
```

**Output Schema:**
```json
{
    "FleetAttributes": {
        "FleetId": "string",
        "FleetArn": "string",
        "FleetType": "ON_DEMAND|SPOT",
        "InstanceType": "string",
        "Description": "string",
        "Name": "string",
        "CreationTime": "timestamp",
        "TerminationTime": "timestamp",
        "Status": "NEW|DOWNLOADING|VALIDATING|BUILDING|ACTIVATING|ACTIVE|DELETING|ERROR|TERMINATED|NOT_FOUND",
        "BuildId": "string",
        "BuildArn": "string",
        "ScriptId": "string",
        "ScriptArn": "string",
        "NewGameSessionProtectionPolicy": "NoProtection|FullProtection",
        "OperatingSystem": "string",
        "ResourceCreationLimitPolicy": {
            "NewGameSessionsPerCreator": "integer",
            "PolicyPeriodInMinutes": "integer"
        },
        "MetricGroups": ["string"],
        "StoppedActions": ["AUTO_SCALING"],
        "InstanceRoleArn": "string",
        "CertificateConfiguration": {
            "CertificateType": "DISABLED|GENERATED"
        },
        "ComputeType": "EC2|ANYWHERE",
        "AnywhereConfiguration": {
            "Cost": "string"
        },
        "InstanceRoleCredentialsProvider": "SHARED_CREDENTIAL_FILE"
    },
    "LocationStates": [
        {
            "Location": "string",
            "Status": "string"
        }
    ]
}
```

---

### 2.2 `delete-fleet`

Deletes a fleet. The fleet must have zero instances (scale down first).

**Synopsis:**
```bash
aws gamelift delete-fleet \
    --fleet-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN to delete |

**Output Schema:**
```json
None
```

---

### 2.3 `describe-fleet-attributes`

Retrieves fleet properties for one or more fleets. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-fleet-attributes \
    [--fleet-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-ids` | No | list(string) | None | Fleet IDs or ARNs (omit for all fleets) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FleetAttributes": [
        {
            "FleetId": "string",
            "FleetArn": "string",
            "FleetType": "ON_DEMAND|SPOT",
            "InstanceType": "string",
            "Name": "string",
            "Description": "string",
            "Status": "string",
            "BuildId": "string",
            "ScriptId": "string",
            "OperatingSystem": "string",
            "ComputeType": "EC2|ANYWHERE",
            "CreationTime": "timestamp",
            "TerminationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `describe-fleet-capacity`

Retrieves current capacity settings for one or more fleets. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-fleet-capacity \
    [--fleet-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-ids` | No | list(string) | None | Fleet IDs or ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FleetCapacity": [
        {
            "FleetId": "string",
            "FleetArn": "string",
            "InstanceType": "string",
            "InstanceCounts": {
                "DESIRED": "integer",
                "MINIMUM": "integer",
                "MAXIMUM": "integer",
                "PENDING": "integer",
                "ACTIVE": "integer",
                "IDLE": "integer",
                "TERMINATING": "integer"
            },
            "Location": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `describe-fleet-utilization`

Retrieves utilization statistics for one or more fleets. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-fleet-utilization \
    [--fleet-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-ids` | No | list(string) | None | Fleet IDs or ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FleetUtilization": [
        {
            "FleetId": "string",
            "FleetArn": "string",
            "ActiveServerProcessCount": "integer",
            "ActiveGameSessionCount": "integer",
            "CurrentPlayerSessionCount": "integer",
            "MaximumPlayerSessionCount": "integer",
            "Location": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `describe-fleet-events`

Retrieves entries from a fleet's event log. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-fleet-events \
    --fleet-id <value> \
    [--start-time <value>] \
    [--end-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--start-time` | No | timestamp | None | Earliest date to retrieve events |
| `--end-time` | No | timestamp | None | Latest date to retrieve events |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Events": [
        {
            "EventId": "string",
            "ResourceId": "string",
            "EventCode": "string",
            "Message": "string",
            "EventTime": "timestamp",
            "PreSignedLogUrl": "string",
            "Count": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `describe-fleet-port-settings`

Retrieves inbound connection permissions (port settings) for a fleet.

**Synopsis:**
```bash
aws gamelift describe-fleet-port-settings \
    --fleet-id <value> \
    [--location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--location` | No | string | None | Remote location to retrieve port settings for |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string",
    "InboundPermissions": [
        {
            "FromPort": "integer",
            "ToPort": "integer",
            "IpRange": "string",
            "Protocol": "TCP|UDP"
        }
    ],
    "UpdateStatus": "PENDING_UPDATE",
    "Location": "string"
}
```

---

### 2.8 `describe-fleet-location-attributes`

Retrieves information about fleet locations including status and type. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-fleet-location-attributes \
    --fleet-id <value> \
    [--locations <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--locations` | No | list(string) | None | Locations to retrieve (omit for all) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string",
    "LocationAttributes": [
        {
            "LocationState": {
                "Location": "string",
                "Status": "string"
            },
            "StoppedActions": ["AUTO_SCALING"],
            "UpdateStatus": "PENDING_UPDATE"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.9 `describe-fleet-location-capacity`

Retrieves capacity settings for a specific fleet location.

**Synopsis:**
```bash
aws gamelift describe-fleet-location-capacity \
    --fleet-id <value> \
    --location <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--location` | **Yes** | string | -- | Fleet location to retrieve capacity for |

**Output Schema:**
```json
{
    "FleetCapacity": {
        "FleetId": "string",
        "FleetArn": "string",
        "InstanceType": "string",
        "InstanceCounts": {
            "DESIRED": "integer",
            "MINIMUM": "integer",
            "MAXIMUM": "integer",
            "PENDING": "integer",
            "ACTIVE": "integer",
            "IDLE": "integer",
            "TERMINATING": "integer"
        },
        "Location": "string"
    }
}
```

---

### 2.10 `describe-fleet-location-utilization`

Retrieves utilization statistics for a specific fleet location.

**Synopsis:**
```bash
aws gamelift describe-fleet-location-utilization \
    --fleet-id <value> \
    --location <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--location` | **Yes** | string | -- | Fleet location |

**Output Schema:**
```json
{
    "FleetUtilization": {
        "FleetId": "string",
        "FleetArn": "string",
        "ActiveServerProcessCount": "integer",
        "ActiveGameSessionCount": "integer",
        "CurrentPlayerSessionCount": "integer",
        "MaximumPlayerSessionCount": "integer",
        "Location": "string"
    }
}
```

---

### 2.11 `list-fleets`

Retrieves all fleet IDs in the account. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-fleets \
    [--build-id <value>] \
    [--script-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--build-id` | No | string | None | Filter by build ID |
| `--script-id` | No | string | None | Filter by script ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FleetIds": ["string"],
    "NextToken": "string"
}
```

---

### 2.12 `update-fleet-attributes`

Updates fleet properties including name, description, and game session protection.

**Synopsis:**
```bash
aws gamelift update-fleet-attributes \
    --fleet-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--new-game-session-protection-policy <value>] \
    [--resource-creation-limit-policy <value>] \
    [--metric-groups <value>] \
    [--anywhere-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--name` | No | string | None | New name (1-1024 chars) |
| `--description` | No | string | None | New description |
| `--new-game-session-protection-policy` | No | string | None | `NoProtection` or `FullProtection` |
| `--resource-creation-limit-policy` | No | structure | None | Game session creation limits |
| `--metric-groups` | No | list(string) | None | CloudWatch metric group names |
| `--anywhere-configuration` | No | structure | None | Anywhere fleet cost settings |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string"
}
```

---

### 2.13 `update-fleet-capacity`

Updates capacity settings for a fleet location.

**Synopsis:**
```bash
aws gamelift update-fleet-capacity \
    --fleet-id <value> \
    [--desired-instances <value>] \
    [--min-size <value>] \
    [--max-size <value>] \
    [--location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--desired-instances` | No | integer | None | Number of instances to maintain |
| `--min-size` | No | integer | None | Minimum instance count (min: 0) |
| `--max-size` | No | integer | None | Maximum instance count (min: 0) |
| `--location` | No | string | None | Remote location to update |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string",
    "Location": "string"
}
```

---

### 2.14 `update-fleet-port-settings`

Updates port settings for a fleet. Adds or removes inbound permission rules.

**Synopsis:**
```bash
aws gamelift update-fleet-port-settings \
    --fleet-id <value> \
    [--inbound-permission-authorizations <value>] \
    [--inbound-permission-revocations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--inbound-permission-authorizations` | No | list | None | Rules to add. Shorthand: `FromPort=int,ToPort=int,IpRange=string,Protocol=TCP\|UDP` |
| `--inbound-permission-revocations` | No | list | None | Rules to remove (same structure) |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string"
}
```

---

### 2.15 `create-fleet-locations`

Adds remote locations to an existing multi-location fleet.

**Synopsis:**
```bash
aws gamelift create-fleet-locations \
    --fleet-id <value> \
    --locations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--locations` | **Yes** | list | -- | Locations to add. Shorthand: `Location=string ...` |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string",
    "LocationStates": [
        {
            "Location": "string",
            "Status": "string"
        }
    ]
}
```

---

### 2.16 `delete-fleet-locations`

Removes remote locations from a multi-location fleet.

**Synopsis:**
```bash
aws gamelift delete-fleet-locations \
    --fleet-id <value> \
    --locations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--locations` | **Yes** | list(string) | -- | Locations to remove |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string",
    "LocationStates": [
        {
            "Location": "string",
            "Status": "string"
        }
    ]
}
```

---

### 2.17 `describe-fleet-deployment`

Retrieves details of a fleet deployment.

**Synopsis:**
```bash
aws gamelift describe-fleet-deployment \
    --fleet-id <value> \
    [--deployment-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--deployment-id` | No | string | None | Deployment ID (omit for latest) |

**Output Schema:**
```json
{
    "FleetDeployment": {
        "DeploymentId": "string",
        "FleetId": "string",
        "GameServerBinaryArn": "string",
        "RollbackGameServerBinaryArn": "string",
        "PerInstanceBinaryArn": "string",
        "RollbackPerInstanceBinaryArn": "string",
        "DeploymentStatus": "IN_PROGRESS|IMPAIRED|COMPLETE|ROLLBACK_IN_PROGRESS|ROLLBACK_COMPLETE|CANCELLED|PENDING",
        "DeploymentConfiguration": {
            "ProtectionStrategy": "WITH_PROTECTION|IGNORE_PROTECTION",
            "MinimumHealthyPercentage": "integer",
            "ImpairmentStrategy": "MAINTAIN|ROLLBACK"
        },
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    },
    "LocationalDeployments": {
        "string": {
            "DeploymentStatus": "string"
        }
    }
}
```

---

### 2.18 `list-fleet-deployments`

Lists all deployments for a fleet. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-fleet-deployments \
    --fleet-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FleetDeployments": [
        {
            "DeploymentId": "string",
            "FleetId": "string",
            "DeploymentStatus": "string",
            "CreationTime": "timestamp",
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.19 `describe-ec2-instance-limits`

Retrieves EC2 instance limits for GameLift in the current region.

**Synopsis:**
```bash
aws gamelift describe-ec2-instance-limits \
    [--ec2-instance-type <value>] \
    [--location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ec2-instance-type` | No | string | None | Specific instance type to query |
| `--location` | No | string | None | Location to query limits for |

**Output Schema:**
```json
{
    "EC2InstanceLimits": [
        {
            "EC2InstanceType": "string",
            "CurrentInstances": "integer",
            "InstanceLimit": "integer",
            "Location": "string"
        }
    ]
}
```

---

### 2.20 `describe-instances`

Retrieves information about instances in a fleet. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-instances \
    --fleet-id <value> \
    [--instance-id <value>] \
    [--location <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--instance-id` | No | string | None | Specific instance ID |
| `--location` | No | string | None | Fleet location |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Instances": [
        {
            "FleetId": "string",
            "FleetArn": "string",
            "InstanceId": "string",
            "IpAddress": "string",
            "DnsName": "string",
            "OperatingSystem": "string",
            "Type": "string",
            "Status": "PENDING|ACTIVE|TERMINATING",
            "CreationTime": "timestamp",
            "Location": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.21 `get-instance-access`

Requests remote access credentials for a fleet instance (SSH key for Linux, RDP password for Windows).

**Synopsis:**
```bash
aws gamelift get-instance-access \
    --fleet-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--instance-id` | **Yes** | string | -- | Instance ID |

**Output Schema:**
```json
{
    "InstanceAccess": {
        "FleetId": "string",
        "InstanceId": "string",
        "IpAddress": "string",
        "OperatingSystem": "string",
        "Credentials": {
            "UserName": "string",
            "Secret": "string"
        }
    }
}
```

---

### 2.22 `describe-runtime-configuration`

Retrieves the runtime configuration for a fleet.

**Synopsis:**
```bash
aws gamelift describe-runtime-configuration \
    --fleet-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |

**Output Schema:**
```json
{
    "RuntimeConfiguration": {
        "ServerProcesses": [
            {
                "LaunchPath": "string",
                "Parameters": "string",
                "ConcurrentExecutions": "integer"
            }
        ],
        "MaxConcurrentGameSessionActivations": "integer",
        "GameSessionActivationTimeoutSeconds": "integer"
    }
}
```

---

### 2.23 `update-runtime-configuration`

Updates the runtime configuration for a fleet.

**Synopsis:**
```bash
aws gamelift update-runtime-configuration \
    --fleet-id <value> \
    --runtime-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--runtime-configuration` | **Yes** | structure | -- | New runtime configuration (JSON) |

**Output Schema:**
```json
{
    "RuntimeConfiguration": {
        "ServerProcesses": [
            {
                "LaunchPath": "string",
                "Parameters": "string",
                "ConcurrentExecutions": "integer"
            }
        ],
        "MaxConcurrentGameSessionActivations": "integer",
        "GameSessionActivationTimeoutSeconds": "integer"
    }
}
```
