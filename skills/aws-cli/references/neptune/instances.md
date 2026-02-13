# Instances

### 2.1 `create-db-instance`

Creates a new Neptune DB instance in a cluster.

**Synopsis:**
```bash
aws neptune create-db-instance \
    --db-instance-identifier <value> \
    --db-instance-class <value> \
    --engine <value> \
    [--db-cluster-identifier <value>] \
    [--availability-zone <value>] \
    [--preferred-maintenance-window <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--tags <value>] \
    [--copy-tags-to-snapshot | --no-copy-tags-to-snapshot] \
    [--promotion-tier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier (1-63 chars) |
| `--db-instance-class` | **Yes** | string | -- | Instance class (e.g., `db.r6g.large`, `db.serverless`) |
| `--engine` | **Yes** | string | -- | Engine: `neptune` |
| `--db-cluster-identifier` | No | string | -- | Cluster to add instance to |
| `--availability-zone` | No | string | -- | Preferred availability zone |
| `--preferred-maintenance-window` | No | string | -- | Weekly maintenance window |
| `--auto-minor-version-upgrade` | No | boolean | true | Enable auto minor version upgrades |
| `--tags` | No | list | None | Tags |
| `--promotion-tier` | No | integer | 1 | Failover priority (0-15, lower = higher priority) |

**Output Schema:**
```json
{
    "DBInstance": {
        "DBInstanceIdentifier": "string",
        "DBInstanceClass": "string",
        "Engine": "neptune",
        "DBInstanceStatus": "creating",
        "Endpoint": {
            "Address": "string",
            "Port": "integer"
        },
        "AvailabilityZone": "string",
        "DBClusterIdentifier": "string",
        "DBInstanceArn": "string",
        "PromotionTier": "integer"
    }
}
```

---

### 2.2 `modify-db-instance`

Modifies a Neptune DB instance.

**Synopsis:**
```bash
aws neptune modify-db-instance \
    --db-instance-identifier <value> \
    [--db-instance-class <value>] \
    [--apply-immediately | --no-apply-immediately] \
    [--preferred-maintenance-window <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--new-db-instance-identifier <value>] \
    [--promotion-tier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier |
| `--db-instance-class` | No | string | -- | New instance class |
| `--apply-immediately` | No | boolean | false | Apply changes immediately |
| `--new-db-instance-identifier` | No | string | -- | New instance identifier |
| `--promotion-tier` | No | integer | -- | Updated failover priority |

**Output Schema:**
```json
{
    "DBInstance": {
        "DBInstanceIdentifier": "string",
        "DBInstanceClass": "string",
        "DBInstanceStatus": "string",
        "PendingModifiedValues": {}
    }
}
```

---

### 2.3 `delete-db-instance`

Deletes a Neptune DB instance.

**Synopsis:**
```bash
aws neptune delete-db-instance \
    --db-instance-identifier <value> \
    [--skip-final-snapshot | --no-skip-final-snapshot] \
    [--final-db-snapshot-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier |
| `--skip-final-snapshot` | No | boolean | false | Skip final snapshot |
| `--final-db-snapshot-identifier` | No | string | -- | Final snapshot identifier |

**Output Schema:**
```json
{
    "DBInstance": {
        "DBInstanceIdentifier": "string",
        "DBInstanceStatus": "deleting"
    }
}
```

---

### 2.4 `describe-db-instances`

Describes one or more Neptune DB instances. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-instances \
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
| `--db-instance-identifier` | No | string | -- | Specific instance to describe |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "DBInstances": [
        {
            "DBInstanceIdentifier": "string",
            "DBInstanceClass": "string",
            "Engine": "neptune",
            "DBInstanceStatus": "string",
            "Endpoint": {"Address": "string", "Port": "integer"},
            "AvailabilityZone": "string",
            "DBClusterIdentifier": "string",
            "DBInstanceArn": "string",
            "PromotionTier": "integer",
            "InstanceCreateTime": "timestamp",
            "AutoMinorVersionUpgrade": "boolean"
        }
    ]
}
```

---

### 2.5 `reboot-db-instance`

Reboots a Neptune DB instance.

**Synopsis:**
```bash
aws neptune reboot-db-instance \
    --db-instance-identifier <value> \
    [--force-failover | --no-force-failover] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier |
| `--force-failover` | No | boolean | false | Force a Multi-AZ failover |

**Output Schema:**
```json
{
    "DBInstance": {
        "DBInstanceIdentifier": "string",
        "DBInstanceStatus": "rebooting"
    }
}
```

---

### 2.6 `describe-orderable-db-instance-options`

Lists available instance options for Neptune. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-orderable-db-instance-options \
    --engine <value> \
    [--engine-version <value>] \
    [--db-instance-class <value>] \
    [--vpc | --no-vpc] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine` | **Yes** | string | -- | Engine name: `neptune` |
| `--engine-version` | No | string | -- | Filter by engine version |
| `--db-instance-class` | No | string | -- | Filter by instance class |

**Output Schema:**
```json
{
    "OrderableDBInstanceOptions": [
        {
            "Engine": "string",
            "EngineVersion": "string",
            "DBInstanceClass": "string",
            "StorageType": "string",
            "AvailabilityZones": []
        }
    ]
}
```

---

### 2.7 `describe-valid-db-instance-modifications`

Returns valid modifications for a DB instance.

**Synopsis:**
```bash
aws neptune describe-valid-db-instance-modifications \
    --db-instance-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Instance identifier |

**Output Schema:**
```json
{
    "ValidDBInstanceModificationsMessage": {
        "Storage": [{"StorageType": "string", "StorageSize": [], "Iops": []}]
    }
}
```

---

### 2.8 `describe-db-engine-versions`

Lists available Neptune engine versions. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-engine-versions \
    [--engine <value>] \
    [--engine-version <value>] \
    [--db-parameter-group-family <value>] \
    [--default-only | --no-default-only] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine` | No | string | -- | Engine name: `neptune` |
| `--engine-version` | No | string | -- | Specific version |
| `--default-only` | No | boolean | false | Only return default version |

**Output Schema:**
```json
{
    "DBEngineVersions": [
        {
            "Engine": "string",
            "EngineVersion": "string",
            "DBParameterGroupFamily": "string",
            "DBEngineDescription": "string",
            "DBEngineVersionDescription": "string",
            "ValidUpgradeTarget": [
                {"Engine": "string", "EngineVersion": "string", "AutoUpgrade": "boolean"}
            ],
            "SupportsGlobalDatabases": "boolean"
        }
    ]
}
```
