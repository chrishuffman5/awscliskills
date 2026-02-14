# Brokers

### 1.1 `create-broker`

Creates a new message broker (ActiveMQ or RabbitMQ).

**Synopsis:**
```bash
aws mq create-broker \
    --broker-name <value> \
    --deployment-mode <value> \
    --engine-type <value> \
    --host-instance-type <value> \
    --publicly-accessible | --no-publicly-accessible \
    [--authentication-strategy <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--configuration <value>] \
    [--creator-request-id <value>] \
    [--encryption-options <value>] \
    [--engine-version <value>] \
    [--ldap-server-metadata <value>] \
    [--logs <value>] \
    [--maintenance-window-start-time <value>] \
    [--security-groups <value>] \
    [--storage-type <value>] \
    [--subnet-ids <value>] \
    [--tags <value>] \
    [--users <value>] \
    [--data-replication-mode <value>] \
    [--data-replication-primary-broker-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-name` | **Yes** | string | -- | Broker name (1-50 chars, alphanumeric, dashes, underscores) |
| `--deployment-mode` | **Yes** | string | -- | `SINGLE_INSTANCE`, `ACTIVE_STANDBY_MULTI_AZ`, `CLUSTER_MULTI_AZ` |
| `--engine-type` | **Yes** | string | -- | `ACTIVEMQ` or `RABBITMQ` |
| `--host-instance-type` | **Yes** | string | -- | Instance type (e.g., `mq.m5.large`) |
| `--publicly-accessible` | **Yes** | boolean | -- | Allow connections from outside VPC |
| `--authentication-strategy` | No | string | `SIMPLE` | `SIMPLE`, `LDAP`, `CONFIG_MANAGED` |
| `--auto-minor-version-upgrade` | No | boolean | true | Enable auto patch upgrades |
| `--configuration` | No | structure | None | Configuration ID and revision |
| `--creator-request-id` | No | string | None | Idempotency token (recommend UUID) |
| `--encryption-options` | No | structure | None | Encryption settings |
| `--engine-version` | No | string | Latest | Engine version |
| `--ldap-server-metadata` | No | structure | None | LDAP configuration (ActiveMQ only) |
| `--logs` | No | structure | None | CloudWatch logging configuration |
| `--maintenance-window-start-time` | No | structure | None | Weekly maintenance window |
| `--security-groups` | No | list | None | Security group IDs |
| `--storage-type` | No | string | None | `EBS` or `EFS` |
| `--subnet-ids` | No | list | None | VPC subnet IDs |
| `--tags` | No | map | None | Resource tags |
| `--users` | No | list | None | Broker users |
| `--data-replication-mode` | No | string | `NONE` | `NONE` or `CRDR` |
| `--data-replication-primary-broker-arn` | No | string | None | Primary broker ARN for CRDR |

**Configuration:**
```json
{
    "Id": "string",
    "Revision": integer
}
```

**EncryptionOptions:**
```json
{
    "KmsKeyId": "string",
    "UseAwsOwnedKey": true|false
}
```

**Logs:**
```json
{
    "Audit": true|false,
    "General": true|false
}
```

**MaintenanceWindowStartTime:**
```json
{
    "DayOfWeek": "MONDAY|TUESDAY|WEDNESDAY|THURSDAY|FRIDAY|SATURDAY|SUNDAY",
    "TimeOfDay": "string",
    "TimeZone": "string"
}
```

**Users (list element):**
```json
{
    "ConsoleAccess": true|false,
    "Groups": ["string"],
    "Password": "string",
    "Username": "string",
    "ReplicationUser": true|false
}
```

**Output Schema:**
```json
{
    "BrokerArn": "string",
    "BrokerId": "string"
}
```

---

### 1.2 `describe-broker`

Describes a broker including state, endpoints, and configuration.

**Synopsis:**
```bash
aws mq describe-broker \
    --broker-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID |

**Output Schema:**
```json
{
    "ActionsRequired": [
        {"ActionRequiredCode": "string", "ActionRequiredInfo": "string"}
    ],
    "AuthenticationStrategy": "SIMPLE|LDAP|CONFIG_MANAGED",
    "AutoMinorVersionUpgrade": boolean,
    "BrokerArn": "string",
    "BrokerId": "string",
    "BrokerInstances": [
        {
            "ConsoleURL": "string",
            "Endpoints": ["string"],
            "IpAddress": "string"
        }
    ],
    "BrokerName": "string",
    "BrokerState": "CREATION_IN_PROGRESS|CREATION_FAILED|DELETION_IN_PROGRESS|RUNNING|REBOOT_IN_PROGRESS|CRITICAL_ACTION_REQUIRED|REPLICA",
    "Configurations": {
        "Current": {"Id": "string", "Revision": integer},
        "History": [{"Id": "string", "Revision": integer}],
        "Pending": {"Id": "string", "Revision": integer}
    },
    "Created": "timestamp",
    "DeploymentMode": "SINGLE_INSTANCE|ACTIVE_STANDBY_MULTI_AZ|CLUSTER_MULTI_AZ",
    "EncryptionOptions": {
        "KmsKeyId": "string",
        "UseAwsOwnedKey": boolean
    },
    "EngineType": "ACTIVEMQ|RABBITMQ",
    "EngineVersion": "string",
    "HostInstanceType": "string",
    "LdapServerMetadata": {
        "Hosts": ["string"],
        "RoleBase": "string",
        "RoleName": "string",
        "RoleSearchMatching": "string",
        "RoleSearchSubtree": boolean,
        "ServiceAccountUsername": "string",
        "UserBase": "string",
        "UserRoleName": "string",
        "UserSearchMatching": "string",
        "UserSearchSubtree": boolean
    },
    "Logs": {
        "Audit": boolean,
        "AuditLogGroup": "string",
        "General": boolean,
        "GeneralLogGroup": "string",
        "Pending": {"Audit": boolean, "General": boolean}
    },
    "MaintenanceWindowStartTime": {
        "DayOfWeek": "string",
        "TimeOfDay": "string",
        "TimeZone": "string"
    },
    "PendingAuthenticationStrategy": "string",
    "PendingEngineVersion": "string",
    "PendingHostInstanceType": "string",
    "PendingLdapServerMetadata": {},
    "PendingSecurityGroups": ["string"],
    "PubliclyAccessible": boolean,
    "SecurityGroups": ["string"],
    "StorageType": "EBS|EFS",
    "SubnetIds": ["string"],
    "Tags": {"string": "string"},
    "Users": [
        {"PendingChange": "CREATE|UPDATE|DELETE", "Username": "string"}
    ],
    "DataReplicationMetadata": {
        "DataReplicationCounterpart": {"BrokerId": "string", "Region": "string"},
        "DataReplicationRole": "string"
    },
    "DataReplicationMode": "NONE|CRDR",
    "PendingDataReplicationMetadata": {},
    "PendingDataReplicationMode": "NONE|CRDR"
}
```

---

### 1.3 `list-brokers`

Lists all brokers. **Paginated operation.**

**Synopsis:**
```bash
aws mq list-brokers \
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
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "BrokerSummaries": [
        {
            "BrokerArn": "string",
            "BrokerId": "string",
            "BrokerName": "string",
            "BrokerState": "CREATION_IN_PROGRESS|CREATION_FAILED|DELETION_IN_PROGRESS|RUNNING|REBOOT_IN_PROGRESS|CRITICAL_ACTION_REQUIRED|REPLICA",
            "Created": "timestamp",
            "DeploymentMode": "SINGLE_INSTANCE|ACTIVE_STANDBY_MULTI_AZ|CLUSTER_MULTI_AZ",
            "EngineType": "ACTIVEMQ|RABBITMQ",
            "HostInstanceType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-broker`

Updates broker settings. Some changes require a reboot to take effect.

**Synopsis:**
```bash
aws mq update-broker \
    --broker-id <value> \
    [--authentication-strategy <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--configuration <value>] \
    [--engine-version <value>] \
    [--host-instance-type <value>] \
    [--ldap-server-metadata <value>] \
    [--logs <value>] \
    [--maintenance-window-start-time <value>] \
    [--security-groups <value>] \
    [--data-replication-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID |
| `--authentication-strategy` | No | string | None | `SIMPLE`, `LDAP`, `CONFIG_MANAGED` |
| `--auto-minor-version-upgrade` | No | boolean | None | Enable auto patch upgrades |
| `--configuration` | No | structure | None | Configuration ID and revision |
| `--engine-version` | No | string | None | Engine version to upgrade to |
| `--host-instance-type` | No | string | None | Instance type to change to |
| `--ldap-server-metadata` | No | structure | None | Updated LDAP configuration |
| `--logs` | No | structure | None | Updated logging configuration |
| `--maintenance-window-start-time` | No | structure | None | Updated maintenance window |
| `--security-groups` | No | list | None | Updated security groups |
| `--data-replication-mode` | No | string | None | `NONE` or `CRDR` |

**Output Schema:**
```json
{
    "AuthenticationStrategy": "SIMPLE|LDAP|CONFIG_MANAGED",
    "AutoMinorVersionUpgrade": boolean,
    "BrokerId": "string",
    "Configuration": {"Id": "string", "Revision": integer},
    "EngineVersion": "string",
    "HostInstanceType": "string",
    "LdapServerMetadata": {},
    "Logs": {"Audit": boolean, "General": boolean},
    "MaintenanceWindowStartTime": {
        "DayOfWeek": "string",
        "TimeOfDay": "string",
        "TimeZone": "string"
    },
    "SecurityGroups": ["string"],
    "DataReplicationMetadata": {},
    "DataReplicationMode": "NONE|CRDR",
    "PendingDataReplicationMetadata": {},
    "PendingDataReplicationMode": "NONE|CRDR"
}
```

---

### 1.5 `delete-broker`

Deletes a message broker.

**Synopsis:**
```bash
aws mq delete-broker \
    --broker-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID to delete |

**Output Schema:**
```json
{
    "BrokerId": "string"
}
```

---

### 1.6 `reboot-broker`

Reboots a message broker. Required to apply user changes and some configuration changes.

**Synopsis:**
```bash
aws mq reboot-broker \
    --broker-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID to reboot |

**Output:** None

---

### 1.7 `promote`

Promotes a data replication replica broker to become the primary broker.

**Synopsis:**
```bash
aws mq promote \
    --broker-id <value> \
    --mode <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID to promote |
| `--mode` | **Yes** | string | -- | Promotion mode: `SWITCHOVER` or `FAILOVER` |

**Output Schema:**
```json
{
    "BrokerId": "string"
}
```

---

### 1.8 `describe-broker-engine-types`

Lists available broker engine types and versions.

**Synopsis:**
```bash
aws mq describe-broker-engine-types \
    [--engine-type <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine-type` | No | string | None | Filter: `ACTIVEMQ` or `RABBITMQ` |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "BrokerEngineTypes": [
        {
            "EngineType": "ACTIVEMQ|RABBITMQ",
            "EngineVersions": [
                {"Name": "string"}
            ]
        }
    ],
    "MaxResults": integer,
    "NextToken": "string"
}
```

---

### 1.9 `describe-broker-instance-options`

Lists available broker instance options (instance types, engines, deployment modes).

**Synopsis:**
```bash
aws mq describe-broker-instance-options \
    [--engine-type <value>] \
    [--host-instance-type <value>] \
    [--storage-type <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine-type` | No | string | None | Filter by engine type |
| `--host-instance-type` | No | string | None | Filter by instance type |
| `--storage-type` | No | string | None | Filter by storage type |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "BrokerInstanceOptions": [
        {
            "AvailabilityZones": [{"Name": "string"}],
            "EngineType": "ACTIVEMQ|RABBITMQ",
            "HostInstanceType": "string",
            "StorageType": "EBS|EFS",
            "SupportedDeploymentModes": ["SINGLE_INSTANCE|ACTIVE_STANDBY_MULTI_AZ|CLUSTER_MULTI_AZ"],
            "SupportedEngineVersions": ["string"]
        }
    ],
    "MaxResults": integer,
    "NextToken": "string"
}
```
