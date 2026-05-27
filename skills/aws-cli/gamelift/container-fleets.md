# Container Fleets

### 3.1 `create-container-fleet`

Creates a new container-based fleet to host game servers using container group definitions.

**Synopsis:**
```bash
aws gamelift create-container-fleet \
    --fleet-role-arn <value> \
    [--description <value>] \
    [--game-server-container-group-definition-name <value>] \
    [--per-instance-container-group-definition-name <value>] \
    [--instance-connection-port-range <value>] \
    [--instance-inbound-permissions <value>] \
    [--game-server-container-groups-per-instance <value>] \
    [--instance-type <value>] \
    [--billing-type <value>] \
    [--locations <value>] \
    [--metric-groups <value>] \
    [--new-game-session-protection-policy <value>] \
    [--game-session-creation-limit-policy <value>] \
    [--log-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-role-arn` | **Yes** | string | -- | IAM role ARN with GameLiftContainerFleetPolicy (1-256 chars) |
| `--description` | No | string | None | Description (1-1024 chars) |
| `--game-server-container-group-definition-name` | No | string | None | Container group definition name or ARN for game servers |
| `--per-instance-container-group-definition-name` | No | string | None | Container group definition for per-instance processes |
| `--instance-connection-port-range` | No | structure | Calculated | Port range. Shorthand: `FromPort=int,ToPort=int` |
| `--instance-inbound-permissions` | No | list | Calculated | Inbound rules (max 50). Shorthand: `FromPort=int,ToPort=int,IpRange=string,Protocol=TCP\|UDP` |
| `--game-server-container-groups-per-instance` | No | integer | Calculated | Number of game server container groups per instance (1-5000) |
| `--instance-type` | No | string | Auto-selected | EC2 instance type (cannot be updated after creation) |
| `--billing-type` | No | string | `ON_DEMAND` | `ON_DEMAND` or `SPOT` (cannot be updated after creation) |
| `--locations` | No | list | Home region | Locations for deployment (1-100). Shorthand: `Location=string` |
| `--metric-groups` | No | list(string) | None | CloudWatch metric group names (max 1) |
| `--new-game-session-protection-policy` | No | string | `NoProtection` | `NoProtection` or `FullProtection` |
| `--game-session-creation-limit-policy` | No | structure | None | Shorthand: `NewGameSessionsPerCreator=int,PolicyPeriodInMinutes=int` |
| `--log-configuration` | No | structure | `CLOUDWATCH` | Log config. Shorthand: `LogDestination=NONE\|CLOUDWATCH\|S3,S3BucketName=string,LogGroupArn=string` |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "ContainerFleet": {
        "FleetId": "string",
        "FleetArn": "string",
        "FleetRoleArn": "string",
        "GameServerContainerGroupDefinitionName": "string",
        "GameServerContainerGroupDefinitionArn": "string",
        "PerInstanceContainerGroupDefinitionName": "string",
        "PerInstanceContainerGroupDefinitionArn": "string",
        "InstanceConnectionPortRange": {
            "FromPort": "integer",
            "ToPort": "integer"
        },
        "InstanceInboundPermissions": [
            {
                "FromPort": "integer",
                "ToPort": "integer",
                "IpRange": "string",
                "Protocol": "TCP|UDP"
            }
        ],
        "GameServerContainerGroupsPerInstance": "integer",
        "MaximumGameServerContainerGroupsPerInstance": "integer",
        "InstanceType": "string",
        "BillingType": "ON_DEMAND|SPOT",
        "Description": "string",
        "CreationTime": "timestamp",
        "MetricGroups": ["string"],
        "NewGameSessionProtectionPolicy": "NoProtection|FullProtection",
        "GameSessionCreationLimitPolicy": {
            "NewGameSessionsPerCreator": "integer",
            "PolicyPeriodInMinutes": "integer"
        },
        "Status": "PENDING|CREATING|CREATED|ACTIVATING|ACTIVE|UPDATING|DELETING",
        "DeploymentDetails": {
            "LatestDeploymentId": "string"
        },
        "LogConfiguration": {
            "LogDestination": "NONE|CLOUDWATCH|S3",
            "S3BucketName": "string",
            "LogGroupArn": "string"
        },
        "LocationAttributes": [
            {
                "Location": "string",
                "Status": "string"
            }
        ]
    }
}
```

---

### 3.2 `delete-container-fleet`

Deletes a container fleet and releases its resources.

**Synopsis:**
```bash
aws gamelift delete-container-fleet \
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

### 3.3 `describe-container-fleet`

Retrieves properties of a container fleet.

**Synopsis:**
```bash
aws gamelift describe-container-fleet \
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
    "ContainerFleet": {
        "FleetId": "string",
        "FleetArn": "string",
        "FleetRoleArn": "string",
        "GameServerContainerGroupDefinitionName": "string",
        "GameServerContainerGroupDefinitionArn": "string",
        "PerInstanceContainerGroupDefinitionName": "string",
        "PerInstanceContainerGroupDefinitionArn": "string",
        "InstanceConnectionPortRange": {},
        "InstanceInboundPermissions": [],
        "GameServerContainerGroupsPerInstance": "integer",
        "MaximumGameServerContainerGroupsPerInstance": "integer",
        "InstanceType": "string",
        "BillingType": "ON_DEMAND|SPOT",
        "Description": "string",
        "CreationTime": "timestamp",
        "Status": "string",
        "DeploymentDetails": {},
        "LogConfiguration": {},
        "LocationAttributes": []
    }
}
```

---

### 3.4 `list-container-fleets`

Lists all container fleets in the account. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-container-fleets \
    [--container-group-definition-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-group-definition-name` | No | string | None | Filter by container group definition name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ContainerFleets": [
        {
            "FleetId": "string",
            "FleetArn": "string",
            "Status": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-container-fleet`

Updates properties of an existing container fleet.

**Synopsis:**
```bash
aws gamelift update-container-fleet \
    --fleet-id <value> \
    [--game-server-container-group-definition-name <value>] \
    [--per-instance-container-group-definition-name <value>] \
    [--game-server-container-groups-per-instance <value>] \
    [--instance-connection-port-range <value>] \
    [--instance-inbound-permission-authorizations <value>] \
    [--instance-inbound-permission-revocations <value>] \
    [--deployment-configuration <value>] \
    [--description <value>] \
    [--metric-groups <value>] \
    [--new-game-session-protection-policy <value>] \
    [--game-session-creation-limit-policy <value>] \
    [--log-configuration <value>] \
    [--remove-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--game-server-container-group-definition-name` | No | string | None | New container group definition |
| `--per-instance-container-group-definition-name` | No | string | None | New per-instance definition |
| `--game-server-container-groups-per-instance` | No | integer | None | Container groups per instance |
| `--instance-connection-port-range` | No | structure | None | New port range |
| `--instance-inbound-permission-authorizations` | No | list | None | Inbound rules to add |
| `--instance-inbound-permission-revocations` | No | list | None | Inbound rules to remove |
| `--deployment-configuration` | No | structure | None | Deployment settings. Shorthand: `ProtectionStrategy=WITH_PROTECTION\|IGNORE_PROTECTION,MinimumHealthyPercentage=int,ImpairmentStrategy=MAINTAIN\|ROLLBACK` |
| `--description` | No | string | None | New description |
| `--metric-groups` | No | list(string) | None | CloudWatch metric groups |
| `--new-game-session-protection-policy` | No | string | None | `NoProtection` or `FullProtection` |
| `--game-session-creation-limit-policy` | No | structure | None | Game session creation limits |
| `--log-configuration` | No | structure | None | Log configuration |
| `--remove-attributes` | No | list(string) | None | Attributes to remove: `PER_INSTANCE_CONTAINER_GROUP_DEFINITION` |

**Output Schema:**
```json
{
    "ContainerFleet": {
        "FleetId": "string",
        "FleetArn": "string",
        "Status": "string",
        "DeploymentDetails": {
            "LatestDeploymentId": "string"
        }
    }
}
```

---

### 3.6 `create-container-group-definition`

Creates a container group definition that describes containers for game server hosting.

**Synopsis:**
```bash
aws gamelift create-container-group-definition \
    --name <value> \
    --total-memory-limit-mebibytes <value> \
    --total-vcpu-limit <value> \
    --operating-system <value> \
    [--container-group-type <value>] \
    [--game-server-container-definition <value>] \
    [--support-container-definitions <value>] \
    [--version-description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique identifier (1-128 chars, pattern: `^[a-zA-Z0-9\-]+$`) |
| `--total-memory-limit-mebibytes` | **Yes** | integer | -- | Max memory in MiB (4-1024000) |
| `--total-vcpu-limit` | **Yes** | double | -- | Max vCPU units (0.125-10) |
| `--operating-system` | **Yes** | string | -- | `AMAZON_LINUX_2023` |
| `--container-group-type` | No | string | `GAME_SERVER` | `GAME_SERVER` or `PER_INSTANCE` |
| `--game-server-container-definition` | No | structure | None | Game server container definition (JSON) |
| `--support-container-definitions` | No | list | None | Support containers (max 10, JSON) |
| `--version-description` | No | string | None | Description for this version (1-1024 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Game Server Container Definition Structure:**
```json
{
    "ContainerName": "string",
    "ImageUri": "string",
    "PortConfiguration": {
        "ContainerPortRanges": [
            {
                "FromPort": "integer",
                "ToPort": "integer",
                "Protocol": "TCP|UDP"
            }
        ]
    },
    "ServerSdkVersion": "string",
    "EnvironmentOverride": [
        {"Name": "string", "Value": "string"}
    ],
    "MountPoints": [
        {"InstancePath": "string", "ContainerPath": "string", "AccessLevel": "READ_ONLY|READ_AND_WRITE"}
    ],
    "DependsOn": [
        {"ContainerName": "string", "Condition": "START|COMPLETE|SUCCESS|HEALTHY"}
    ]
}
```

**Output Schema:**
```json
{
    "ContainerGroupDefinition": {
        "ContainerGroupDefinitionArn": "string",
        "CreationTime": "timestamp",
        "OperatingSystem": "AMAZON_LINUX_2023",
        "Name": "string",
        "ContainerGroupType": "GAME_SERVER|PER_INSTANCE",
        "TotalMemoryLimitMebibytes": "integer",
        "TotalVcpuLimit": "double",
        "GameServerContainerDefinition": {
            "ContainerName": "string",
            "ImageUri": "string",
            "ResolvedImageDigest": "string",
            "PortConfiguration": {},
            "ServerSdkVersion": "string"
        },
        "SupportContainerDefinitions": [],
        "VersionNumber": "integer",
        "VersionDescription": "string",
        "Status": "READY|COPYING|FAILED",
        "StatusReason": "string"
    }
}
```

---

### 3.7 `delete-container-group-definition`

Deletes a container group definition. Deletes all versions or a specific version.

**Synopsis:**
```bash
aws gamelift delete-container-group-definition \
    --name <value> \
    [--version-count-to-retain <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name or ARN of the container group definition |
| `--version-count-to-retain` | No | integer | None | Number of most recent versions to keep (min: 1) |

**Output Schema:**
```json
None
```

---

### 3.8 `describe-container-group-definition`

Retrieves a container group definition.

**Synopsis:**
```bash
aws gamelift describe-container-group-definition \
    --name <value> \
    [--version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name or ARN |
| `--version-number` | No | integer | None | Specific version (omit for latest) |

**Output Schema:**
```json
{
    "ContainerGroupDefinition": {
        "ContainerGroupDefinitionArn": "string",
        "CreationTime": "timestamp",
        "OperatingSystem": "string",
        "Name": "string",
        "ContainerGroupType": "GAME_SERVER|PER_INSTANCE",
        "TotalMemoryLimitMebibytes": "integer",
        "TotalVcpuLimit": "double",
        "GameServerContainerDefinition": {},
        "SupportContainerDefinitions": [],
        "VersionNumber": "integer",
        "VersionDescription": "string",
        "Status": "READY|COPYING|FAILED",
        "StatusReason": "string"
    }
}
```

---

### 3.9 `list-container-group-definitions`

Lists all container group definitions in the account. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-container-group-definitions \
    [--container-group-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-group-type` | No | string | None | Filter by type: `GAME_SERVER` or `PER_INSTANCE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ContainerGroupDefinitions": [
        {
            "ContainerGroupDefinitionArn": "string",
            "Name": "string",
            "ContainerGroupType": "string",
            "Status": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.10 `list-container-group-definition-versions`

Lists all versions of a container group definition. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-container-group-definition-versions \
    --name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name or ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ContainerGroupDefinitions": [
        {
            "ContainerGroupDefinitionArn": "string",
            "Name": "string",
            "VersionNumber": "integer",
            "VersionDescription": "string",
            "Status": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.11 `update-container-group-definition`

Creates a new version of a container group definition with updated properties.

**Synopsis:**
```bash
aws gamelift update-container-group-definition \
    --name <value> \
    [--game-server-container-definition <value>] \
    [--support-container-definitions <value>] \
    [--total-memory-limit-mebibytes <value>] \
    [--total-vcpu-limit <value>] \
    [--version-description <value>] \
    [--source-version-number <value>] \
    [--operating-system <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name or ARN |
| `--game-server-container-definition` | No | structure | None | Updated game server container definition |
| `--support-container-definitions` | No | list | None | Updated support containers |
| `--total-memory-limit-mebibytes` | No | integer | None | New memory limit |
| `--total-vcpu-limit` | No | double | None | New vCPU limit |
| `--version-description` | No | string | None | Description for new version |
| `--source-version-number` | No | integer | None | Version to use as base (default: latest) |
| `--operating-system` | No | string | None | `AMAZON_LINUX_2023` |

**Output Schema:**
```json
{
    "ContainerGroupDefinition": {
        "ContainerGroupDefinitionArn": "string",
        "Name": "string",
        "VersionNumber": "integer",
        "VersionDescription": "string",
        "Status": "READY|COPYING|FAILED",
        "CreationTime": "timestamp"
    }
}
```
