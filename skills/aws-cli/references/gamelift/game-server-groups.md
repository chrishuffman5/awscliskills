# Game Server Groups

### 7.1 `create-game-server-group`

Creates a FleetIQ game server group for use with EC2 Auto Scaling.

**Synopsis:**
```bash
aws gamelift create-game-server-group \
    --game-server-group-name <value> \
    --role-arn <value> \
    --min-size <value> \
    --max-size <value> \
    --launch-template <value> \
    --instance-definitions <value> \
    [--auto-scaling-policy <value>] \
    [--balancing-strategy <value>] \
    [--game-server-protection-policy <value>] \
    [--vpc-subnets <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Unique name (1-128 chars, pattern: `[a-zA-Z0-9-\.]+`) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for Auto Scaling access (1-256 chars) |
| `--min-size` | **Yes** | integer | -- | Minimum instances in ASG (min: 0) |
| `--max-size` | **Yes** | integer | -- | Maximum instances in ASG (min: 1) |
| `--launch-template` | **Yes** | structure | -- | EC2 launch template. Shorthand: `LaunchTemplateId=string,LaunchTemplateName=string,Version=string` |
| `--instance-definitions` | **Yes** | list | -- | Instance types (min 2, max 20). Shorthand: `InstanceType=string,WeightedCapacity=string` |
| `--auto-scaling-policy` | No | structure | None | Scaling policy. Shorthand: `EstimatedInstanceWarmup=int,TargetTrackingConfiguration={TargetValue=double}` |
| `--balancing-strategy` | No | string | `SPOT_PREFERRED` | `SPOT_ONLY`, `SPOT_PREFERRED`, or `ON_DEMAND_ONLY` |
| `--game-server-protection-policy` | No | string | `NO_PROTECTION` | `NO_PROTECTION` or `FULL_PROTECTION` |
| `--vpc-subnets` | No | list(string) | None | VPC subnet IDs (max 20) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "GameServerGroup": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "RoleArn": "string",
        "InstanceDefinitions": [
            {
                "InstanceType": "string",
                "WeightedCapacity": "string"
            }
        ],
        "BalancingStrategy": "SPOT_ONLY|SPOT_PREFERRED|ON_DEMAND_ONLY",
        "GameServerProtectionPolicy": "NO_PROTECTION|FULL_PROTECTION",
        "AutoScalingGroupArn": "string",
        "Status": "NEW|ACTIVATING|ACTIVE|DELETE_SCHEDULED|DELETING|DELETED|ERROR",
        "StatusReason": "string",
        "SuspendedActions": ["string"],
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 7.2 `delete-game-server-group`

Deletes a game server group and its associated Auto Scaling group.

**Synopsis:**
```bash
aws gamelift delete-game-server-group \
    --game-server-group-name <value> \
    [--delete-option <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--delete-option` | No | string | None | `SAFE_DELETE` (only if no game servers), `FORCE_DELETE` (terminates all), or `RETAIN` (keep ASG) |

**Output Schema:**
```json
{
    "GameServerGroup": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "Status": "DELETE_SCHEDULED|DELETING|DELETED"
    }
}
```

---

### 7.3 `describe-game-server-group`

Retrieves properties of a game server group.

**Synopsis:**
```bash
aws gamelift describe-game-server-group \
    --game-server-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |

**Output Schema:**
```json
{
    "GameServerGroup": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "RoleArn": "string",
        "InstanceDefinitions": [],
        "BalancingStrategy": "string",
        "GameServerProtectionPolicy": "string",
        "AutoScalingGroupArn": "string",
        "Status": "string",
        "StatusReason": "string",
        "SuspendedActions": [],
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 7.4 `list-game-server-groups`

Lists all game server groups in the account. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-game-server-groups \
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
    "GameServerGroups": [
        {
            "GameServerGroupName": "string",
            "GameServerGroupArn": "string",
            "Status": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `update-game-server-group`

Updates properties of a game server group.

**Synopsis:**
```bash
aws gamelift update-game-server-group \
    --game-server-group-name <value> \
    [--role-arn <value>] \
    [--instance-definitions <value>] \
    [--game-server-protection-policy <value>] \
    [--balancing-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--role-arn` | No | string | None | New IAM role ARN |
| `--instance-definitions` | No | list | None | New instance definitions (2-20) |
| `--game-server-protection-policy` | No | string | None | `NO_PROTECTION` or `FULL_PROTECTION` |
| `--balancing-strategy` | No | string | None | `SPOT_ONLY`, `SPOT_PREFERRED`, or `ON_DEMAND_ONLY` |

**Output Schema:**
```json
{
    "GameServerGroup": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "RoleArn": "string",
        "InstanceDefinitions": [],
        "BalancingStrategy": "string",
        "GameServerProtectionPolicy": "string",
        "Status": "string"
    }
}
```

---

### 7.6 `suspend-game-server-group`

Suspends auto-scaling activity for a game server group.

**Synopsis:**
```bash
aws gamelift suspend-game-server-group \
    --game-server-group-name <value> \
    --suspend-actions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--suspend-actions` | **Yes** | list(string) | -- | Actions to suspend: `REPLACE_INSTANCE_TYPES` |

**Output Schema:**
```json
{
    "GameServerGroup": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "SuspendedActions": ["REPLACE_INSTANCE_TYPES"],
        "Status": "string"
    }
}
```

---

### 7.7 `resume-game-server-group`

Resumes previously suspended auto-scaling activity.

**Synopsis:**
```bash
aws gamelift resume-game-server-group \
    --game-server-group-name <value> \
    --resume-actions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--resume-actions` | **Yes** | list(string) | -- | Actions to resume: `REPLACE_INSTANCE_TYPES` |

**Output Schema:**
```json
{
    "GameServerGroup": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "SuspendedActions": [],
        "Status": "string"
    }
}
```

---

### 7.8 `register-game-server`

Registers a game server with a game server group.

**Synopsis:**
```bash
aws gamelift register-game-server \
    --game-server-group-name <value> \
    --game-server-id <value> \
    --instance-id <value> \
    [--connection-info <value>] \
    [--game-server-data <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--game-server-id` | **Yes** | string | -- | Custom identifier (3-128 chars) |
| `--instance-id` | **Yes** | string | -- | EC2 instance ID |
| `--connection-info` | No | string | None | Connection info for clients (1-512 chars) |
| `--game-server-data` | No | string | None | Custom data (1-1024 chars) |

**Output Schema:**
```json
{
    "GameServer": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "GameServerId": "string",
        "InstanceId": "string",
        "ConnectionInfo": "string",
        "GameServerData": "string",
        "ClaimStatus": "CLAIMED",
        "UtilizationStatus": "AVAILABLE|UTILIZED",
        "RegistrationTime": "timestamp",
        "LastClaimTime": "timestamp",
        "LastHealthCheckTime": "timestamp"
    }
}
```

---

### 7.9 `deregister-game-server`

Removes a game server from a game server group.

**Synopsis:**
```bash
aws gamelift deregister-game-server \
    --game-server-group-name <value> \
    --game-server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--game-server-id` | **Yes** | string | -- | Game server ID |

**Output Schema:**
```json
None
```

---

### 7.10 `describe-game-server`

Retrieves properties of a registered game server.

**Synopsis:**
```bash
aws gamelift describe-game-server \
    --game-server-group-name <value> \
    --game-server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--game-server-id` | **Yes** | string | -- | Game server ID |

**Output Schema:**
```json
{
    "GameServer": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "GameServerId": "string",
        "InstanceId": "string",
        "ConnectionInfo": "string",
        "GameServerData": "string",
        "ClaimStatus": "CLAIMED",
        "UtilizationStatus": "AVAILABLE|UTILIZED",
        "RegistrationTime": "timestamp",
        "LastClaimTime": "timestamp",
        "LastHealthCheckTime": "timestamp"
    }
}
```

---

### 7.11 `list-game-servers`

Lists all game servers in a game server group. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-game-servers \
    --game-server-group-name <value> \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--sort-order` | No | string | None | `ASC` or `DESC` by registration time |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GameServers": [
        {
            "GameServerGroupName": "string",
            "GameServerId": "string",
            "InstanceId": "string",
            "ConnectionInfo": "string",
            "UtilizationStatus": "string",
            "ClaimStatus": "string",
            "RegistrationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.12 `update-game-server`

Updates game server properties (health check, utilization, data).

**Synopsis:**
```bash
aws gamelift update-game-server \
    --game-server-group-name <value> \
    --game-server-id <value> \
    [--game-server-data <value>] \
    [--utilization-status <value>] \
    [--health-check <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--game-server-id` | **Yes** | string | -- | Game server ID |
| `--game-server-data` | No | string | None | New custom data |
| `--utilization-status` | No | string | None | `AVAILABLE` or `UTILIZED` |
| `--health-check` | No | string | None | `HEALTHY` (reports server as healthy) |

**Output Schema:**
```json
{
    "GameServer": {
        "GameServerGroupName": "string",
        "GameServerId": "string",
        "InstanceId": "string",
        "UtilizationStatus": "string",
        "LastHealthCheckTime": "timestamp"
    }
}
```

---

### 7.13 `describe-game-server-instances`

Tracks game server instances in a game server group. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-game-server-instances \
    --game-server-group-name <value> \
    [--instance-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--instance-ids` | No | list(string) | None | Specific instance IDs (max 20) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GameServerInstances": [
        {
            "GameServerGroupName": "string",
            "GameServerGroupArn": "string",
            "InstanceId": "string",
            "InstanceStatus": "ACTIVE|DRAINING|SPOT_TERMINATING"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.14 `claim-game-server`

Locates an available game server and temporarily reserves it for a game session.

**Synopsis:**
```bash
aws gamelift claim-game-server \
    --game-server-group-name <value> \
    [--game-server-id <value>] \
    [--game-server-data <value>] \
    [--filter-option <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-server-group-name` | **Yes** | string | -- | Group name or ARN |
| `--game-server-id` | No | string | None | Specific game server to claim |
| `--game-server-data` | No | string | None | Data to associate with the claim |
| `--filter-option` | No | structure | None | Filter criteria. Shorthand: `InstanceStatuses=ACTIVE\|DRAINING` |

**Output Schema:**
```json
{
    "GameServer": {
        "GameServerGroupName": "string",
        "GameServerGroupArn": "string",
        "GameServerId": "string",
        "InstanceId": "string",
        "ConnectionInfo": "string",
        "GameServerData": "string",
        "ClaimStatus": "CLAIMED",
        "UtilizationStatus": "string",
        "RegistrationTime": "timestamp",
        "LastClaimTime": "timestamp"
    }
}
```
