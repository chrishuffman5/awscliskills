# Instances

### 2.1 `create-db-instance`

Creates a new instance in a DocumentDB cluster.

**Synopsis:**
```bash
aws docdb create-db-instance \
    --db-instance-identifier <value> \
    --db-instance-class <value> \
    --engine <value> \
    --db-cluster-identifier <value> \
    [--availability-zone <value>] \
    [--preferred-maintenance-window <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--tags <value>] \
    [--copy-tags-to-snapshot | --no-copy-tags-to-snapshot] \
    [--promotion-tier <value>] \
    [--enable-performance-insights | --no-enable-performance-insights] \
    [--performance-insights-kms-key-id <value>] \
    [--ca-certificate-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier (1-63 chars) |
| `--db-instance-class` | **Yes** | string | -- | Instance class (e.g., `db.r6g.large`, `db.r5.xlarge`) |
| `--engine` | **Yes** | string | -- | Database engine: `docdb` |
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster to add the instance to |
| `--availability-zone` | No | string | Auto | AZ for the instance |
| `--preferred-maintenance-window` | No | string | Auto | Weekly maintenance window |
| `--auto-minor-version-upgrade` | No | boolean | true | Enable auto minor version upgrade |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--copy-tags-to-snapshot` | No | boolean | false | Copy tags to snapshots |
| `--promotion-tier` | No | integer | 1 | Failover priority (0-15, lower = higher priority) |
| `--enable-performance-insights` | No | boolean | false | Enable Performance Insights |
| `--performance-insights-kms-key-id` | No | string | -- | KMS key for Performance Insights encryption |
| `--ca-certificate-identifier` | No | string | -- | CA certificate identifier |

**Output Schema:**
```json
{
    "DBInstance": {
        "DBInstanceIdentifier": "string",
        "DBInstanceClass": "string",
        "Engine": "docdb",
        "DBInstanceStatus": "string",
        "Endpoint": {
            "Address": "string",
            "Port": "integer",
            "HostedZoneId": "string"
        },
        "InstanceCreateTime": "timestamp",
        "PreferredMaintenanceWindow": "string",
        "BackupRetentionPeriod": "integer",
        "VpcSecurityGroups": [
            {
                "VpcSecurityGroupId": "string",
                "Status": "string"
            }
        ],
        "AvailabilityZone": "string",
        "DBSubnetGroup": {
            "DBSubnetGroupName": "string",
            "DBSubnetGroupDescription": "string",
            "VpcId": "string",
            "SubnetGroupStatus": "string",
            "Subnets": [
                {
                    "SubnetIdentifier": "string",
                    "SubnetAvailabilityZone": {
                        "Name": "string"
                    },
                    "SubnetStatus": "string"
                }
            ]
        },
        "EngineVersion": "string",
        "AutoMinorVersionUpgrade": true|false,
        "PubliclyAccessible": false,
        "StatusInfos": [
            {
                "StatusType": "string",
                "Normal": true|false,
                "Status": "string",
                "Message": "string"
            }
        ],
        "DBClusterIdentifier": "string",
        "StorageEncrypted": true|false,
        "KmsKeyId": "string",
        "DbiResourceId": "string",
        "CACertificateIdentifier": "string",
        "CopyTagsToSnapshot": true|false,
        "PromotionTier": "integer",
        "DBInstanceArn": "string",
        "EnabledCloudwatchLogsExports": ["string"],
        "CertificateDetails": {
            "CAIdentifier": "string",
            "ValidTill": "timestamp"
        }
    }
}
```

---

### 2.2 `delete-db-instance`

Deletes a previously provisioned instance.

**Synopsis:**
```bash
aws docdb delete-db-instance \
    --db-instance-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier to delete |

**Output Schema:** Same as `create-db-instance` output.

---

### 2.3 `describe-db-instances`

Returns information about provisioned DocumentDB instances. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-db-instances \
    [--db-instance-identifier <value>] \
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
| `--db-instance-identifier` | No | string | All | Instance identifier |
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DBInstances": [
        {
            "DBInstanceIdentifier": "string",
            "DBInstanceClass": "string",
            "Engine": "string",
            "DBInstanceStatus": "string",
            "Endpoint": {
                "Address": "string",
                "Port": "integer"
            },
            "DBClusterIdentifier": "string",
            "AvailabilityZone": "string",
            "PromotionTier": "integer",
            "DBInstanceArn": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 2.4 `modify-db-instance`

Modifies settings for an instance.

**Synopsis:**
```bash
aws docdb modify-db-instance \
    --db-instance-identifier <value> \
    [--db-instance-class <value>] \
    [--apply-immediately | --no-apply-immediately] \
    [--preferred-maintenance-window <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--new-db-instance-identifier <value>] \
    [--copy-tags-to-snapshot | --no-copy-tags-to-snapshot] \
    [--promotion-tier <value>] \
    [--enable-performance-insights | --no-enable-performance-insights] \
    [--performance-insights-kms-key-id <value>] \
    [--ca-certificate-identifier <value>] \
    [--certificate-rotation-restart | --no-certificate-rotation-restart] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier |
| `--db-instance-class` | No | string | -- | New instance class |
| `--apply-immediately` | No | boolean | false | Apply changes immediately |
| `--preferred-maintenance-window` | No | string | -- | New maintenance window |
| `--auto-minor-version-upgrade` | No | boolean | -- | Enable/disable auto minor version upgrade |
| `--new-db-instance-identifier` | No | string | -- | New instance identifier (rename) |
| `--copy-tags-to-snapshot` | No | boolean | -- | Copy tags to snapshots |
| `--promotion-tier` | No | integer | -- | Failover priority (0-15) |
| `--enable-performance-insights` | No | boolean | -- | Enable/disable Performance Insights |
| `--performance-insights-kms-key-id` | No | string | -- | KMS key for Performance Insights |
| `--ca-certificate-identifier` | No | string | -- | CA certificate identifier |
| `--certificate-rotation-restart` | No | boolean | false | Restart instance for certificate rotation |

**Output Schema:** Same as `create-db-instance` output.

---

### 2.5 `reboot-db-instance`

Reboots a DocumentDB instance. Rebooting results in a momentary outage.

**Synopsis:**
```bash
aws docdb reboot-db-instance \
    --db-instance-identifier <value> \
    [--force-failover | --no-force-failover] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier to reboot |
| `--force-failover` | No | boolean | false | Force a failover if rebooting the primary instance |

**Output Schema:** Same as `create-db-instance` output.
