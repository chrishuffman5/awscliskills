# Replication Instances

### 1.1 `create-replication-instance`

Creates a replication instance using the specified parameters.

**Synopsis:**
```bash
aws dms create-replication-instance \
    --replication-instance-identifier <value> \
    --replication-instance-class <value> \
    [--allocated-storage <value>] \
    [--vpc-security-group-ids <value>] \
    [--availability-zone <value>] \
    [--replication-subnet-group-identifier <value>] \
    [--preferred-maintenance-window <value>] \
    [--multi-az | --no-multi-az] \
    [--engine-version <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--dns-name-servers <value>] \
    [--resource-identifier <value>] \
    [--network-type <value>] \
    [--kerberos-authentication-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-instance-identifier` | **Yes** | string | -- | Instance identifier (1-63 alphanumeric chars/hyphens, starts with letter) |
| `--replication-instance-class` | **Yes** | string | -- | Compute and memory capacity (e.g., `dms.r5.large`, `dms.c5.xlarge`) |
| `--allocated-storage` | No | integer | -- | Storage in GB |
| `--vpc-security-group-ids` | No | list(string) | -- | VPC security groups to associate |
| `--availability-zone` | No | string | Random AZ | AZ for the instance (cannot use with `--multi-az`) |
| `--replication-subnet-group-identifier` | No | string | -- | Subnet group to associate |
| `--preferred-maintenance-window` | No | string | 30-min window | UTC maintenance window: `ddd:hh24:mi-ddd:hh24:mi` |
| `--multi-az` | No | boolean | false | Enable Multi-AZ deployment |
| `--engine-version` | No | string | Latest | DMS engine version |
| `--auto-minor-version-upgrade` | No | boolean | true | Auto-apply minor engine upgrades |
| `--tags` | No | list | -- | Tags: `key=string,value=string ...` |
| `--kms-key-id` | No | string | Account default | KMS key for encryption |
| `--publicly-accessible` | No | boolean | true | Assign public IP address |
| `--dns-name-servers` | No | string | -- | Custom DNS servers (comma-separated, up to 4) |
| `--resource-identifier` | No | string | Auto-generated | Friendly name for ARN (up to 31 chars) |
| `--network-type` | No | string | -- | IP protocol: `IPv4 only` or `Dual-stack` |
| `--kerberos-authentication-settings` | No | structure | -- | Kerberos settings (KeyCacheSecretId, KeyCacheSecretIamArn, Krb5FileContents) |

**Output Schema:**
```json
{
    "ReplicationInstance": {
        "ReplicationInstanceIdentifier": "string",
        "ReplicationInstanceClass": "string",
        "ReplicationInstanceStatus": "string",
        "AllocatedStorage": "integer",
        "InstanceCreateTime": "timestamp",
        "VpcSecurityGroups": [
            {
                "VpcSecurityGroupId": "string",
                "Status": "string"
            }
        ],
        "AvailabilityZone": "string",
        "ReplicationSubnetGroup": {
            "ReplicationSubnetGroupIdentifier": "string",
            "ReplicationSubnetGroupDescription": "string",
            "VpcId": "string",
            "SubnetGroupStatus": "string",
            "Subnets": [
                {
                    "SubnetIdentifier": "string",
                    "SubnetAvailabilityZone": { "Name": "string" },
                    "SubnetStatus": "string"
                }
            ]
        },
        "PreferredMaintenanceWindow": "string",
        "PendingModifiedValues": {
            "ReplicationInstanceClass": "string",
            "AllocatedStorage": "integer",
            "MultiAZ": "boolean",
            "EngineVersion": "string",
            "NetworkType": "string"
        },
        "MultiAZ": "boolean",
        "EngineVersion": "string",
        "AutoMinorVersionUpgrade": "boolean",
        "KmsKeyId": "string",
        "ReplicationInstanceArn": "string",
        "ReplicationInstancePublicIpAddresses": ["string"],
        "ReplicationInstancePrivateIpAddresses": ["string"],
        "PubliclyAccessible": "boolean",
        "SecondaryAvailabilityZone": "string",
        "FreeUntil": "timestamp",
        "DnsNameServers": "string",
        "NetworkType": "string"
    }
}
```

---

### 1.2 `delete-replication-instance`

Deletes the specified replication instance.

**Synopsis:**
```bash
aws dms delete-replication-instance \
    --replication-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance to delete |

**Output Schema:**
```json
{
    "ReplicationInstance": {
        "ReplicationInstanceIdentifier": "string",
        "ReplicationInstanceClass": "string",
        "ReplicationInstanceStatus": "string",
        "ReplicationInstanceArn": "string"
    }
}
```

---

### 1.3 `describe-replication-instances`

Returns information about replication instances. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-instances \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-instance-arn`, `replication-instance-id`, `replication-instance-class`, `engine-version` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "ReplicationInstances": [
        {
            "ReplicationInstanceIdentifier": "string",
            "ReplicationInstanceClass": "string",
            "ReplicationInstanceStatus": "string",
            "AllocatedStorage": "integer",
            "InstanceCreateTime": "timestamp",
            "VpcSecurityGroups": [],
            "AvailabilityZone": "string",
            "ReplicationSubnetGroup": {},
            "PreferredMaintenanceWindow": "string",
            "PendingModifiedValues": {},
            "MultiAZ": "boolean",
            "EngineVersion": "string",
            "AutoMinorVersionUpgrade": "boolean",
            "KmsKeyId": "string",
            "ReplicationInstanceArn": "string",
            "ReplicationInstancePublicIpAddresses": ["string"],
            "ReplicationInstancePrivateIpAddresses": ["string"],
            "PubliclyAccessible": "boolean",
            "SecondaryAvailabilityZone": "string",
            "NetworkType": "string"
        }
    ]
}
```

---

### 1.4 `modify-replication-instance`

Modifies the replication instance to apply new settings.

**Synopsis:**
```bash
aws dms modify-replication-instance \
    --replication-instance-arn <value> \
    [--allocated-storage <value>] \
    [--apply-immediately | --no-apply-immediately] \
    [--replication-instance-class <value>] \
    [--vpc-security-group-ids <value>] \
    [--preferred-maintenance-window <value>] \
    [--multi-az | --no-multi-az] \
    [--engine-version <value>] \
    [--allow-major-version-upgrade | --no-allow-major-version-upgrade] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--replication-instance-identifier <value>] \
    [--network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance |
| `--allocated-storage` | No | integer | -- | New storage amount in GB |
| `--apply-immediately` | No | boolean | false | Apply changes immediately vs. next maintenance window |
| `--replication-instance-class` | No | string | -- | New compute class |
| `--vpc-security-group-ids` | No | list(string) | -- | New VPC security groups |
| `--preferred-maintenance-window` | No | string | -- | New maintenance window |
| `--multi-az` | No | boolean | -- | Enable/disable Multi-AZ |
| `--engine-version` | No | string | -- | New engine version |
| `--allow-major-version-upgrade` | No | boolean | -- | Allow major version upgrades |
| `--auto-minor-version-upgrade` | No | boolean | -- | Auto-apply minor upgrades |
| `--replication-instance-identifier` | No | string | -- | New instance identifier |
| `--network-type` | No | string | -- | IP protocol type |

**Output Schema:** Same as `create-replication-instance`.

---

### 1.5 `reboot-replication-instance`

Reboots a replication instance. Rebooting results in a momentary outage until the instance becomes available again.

**Synopsis:**
```bash
aws dms reboot-replication-instance \
    --replication-instance-arn <value> \
    [--force-failover | --no-force-failover] \
    [--force-planned-failover | --no-force-planned-failover] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance |
| `--force-failover` | No | boolean | false | Force a failover (Multi-AZ only) |
| `--force-planned-failover` | No | boolean | false | Force a planned failover (Multi-AZ only) |

**Output Schema:** Same as `create-replication-instance`.

---

### 1.6 `describe-orderable-replication-instances`

Returns information about the replication instance types that can be created. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-orderable-replication-instances \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "OrderableReplicationInstances": [
        {
            "EngineVersion": "string",
            "ReplicationInstanceClass": "string",
            "StorageType": "string",
            "MinAllocatedStorage": "integer",
            "MaxAllocatedStorage": "integer",
            "DefaultAllocatedStorage": "integer",
            "IncludedAllocatedStorage": "integer",
            "AvailabilityZones": ["string"],
            "ReleaseStatus": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 1.7 `describe-replication-instance-task-logs`

Returns information about the task logs for the specified replication instance. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-instance-task-logs \
    --replication-instance-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ReplicationInstanceArn": "string",
    "ReplicationInstanceTaskLogs": [
        {
            "ReplicationTaskName": "string",
            "ReplicationTaskArn": "string",
            "ReplicationInstanceTaskLogSize": "long"
        }
    ],
    "Marker": "string"
}
```
