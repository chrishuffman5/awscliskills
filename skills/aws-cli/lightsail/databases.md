# Databases

### 5.1 `create-relational-database`

Creates a new Lightsail managed relational database.

**Synopsis:**
```bash
aws lightsail create-relational-database \
    --relational-database-name <value> \
    --relational-database-blueprint-id <value> \
    --relational-database-bundle-id <value> \
    --master-database-name <value> \
    --master-username <value> \
    [--availability-zone <value>] \
    [--master-user-password <value>] \
    [--preferred-backup-window <value>] \
    [--preferred-maintenance-window <value>] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name for the database |
| `--relational-database-blueprint-id` | **Yes** | string | -- | Blueprint ID (e.g., `mysql_8_0`, `postgres_16`) |
| `--relational-database-bundle-id` | **Yes** | string | -- | Bundle ID (e.g., `micro_2_0`, `small_2_0`) |
| `--master-database-name` | **Yes** | string | -- | Name for the master database |
| `--master-username` | **Yes** | string | -- | Master username |
| `--availability-zone` | No | string | None | Availability zone |
| `--master-user-password` | No | string | auto-generated | Master user password |
| `--preferred-backup-window` | No | string | None | Backup window (UTC, e.g., `03:00-03:30`) |
| `--preferred-maintenance-window` | No | string | None | Maintenance window (e.g., `tue:04:00-tue:04:30`) |
| `--publicly-accessible` | No | boolean | true | Allow public access |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabase",
            "operationType": "CreateRelationalDatabase",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.2 `create-relational-database-from-snapshot`

Creates a new database from a snapshot.

**Synopsis:**
```bash
aws lightsail create-relational-database-from-snapshot \
    --relational-database-name <value> \
    [--availability-zone <value>] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--relational-database-snapshot-name <value>] \
    [--relational-database-bundle-id <value>] \
    [--source-relational-database-name <value>] \
    [--restore-time <value>] \
    [--use-latest-restorable-time | --no-use-latest-restorable-time] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name for the new database |
| `--availability-zone` | No | string | None | Availability zone |
| `--publicly-accessible` | No | boolean | None | Allow public access |
| `--relational-database-snapshot-name` | No | string | None | Snapshot to restore from |
| `--relational-database-bundle-id` | No | string | None | Bundle ID for the new database |
| `--source-relational-database-name` | No | string | None | Source database for point-in-time restore |
| `--restore-time` | No | timestamp | None | Point in time to restore to |
| `--use-latest-restorable-time` | No | boolean | false | Use the latest restorable time |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabase",
            "operationType": "CreateRelationalDatabaseFromSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.3 `delete-relational-database`

Deletes a managed relational database.

**Synopsis:**
```bash
aws lightsail delete-relational-database \
    --relational-database-name <value> \
    [--skip-final-snapshot | --no-skip-final-snapshot] \
    [--final-relational-database-snapshot-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database to delete |
| `--skip-final-snapshot` | No | boolean | false | Skip creating a final snapshot |
| `--final-relational-database-snapshot-name` | No | string | None | Name for the final snapshot |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabase",
            "operationType": "DeleteRelationalDatabase",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.4 `get-relational-database`

Returns information about a specific managed database.

**Synopsis:**
```bash
aws lightsail get-relational-database \
    --relational-database-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |

**Output Schema:**
```json
{
    "relationalDatabase": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "RelationalDatabase",
        "tags": [],
        "relationalDatabaseBlueprintId": "string",
        "relationalDatabaseBundleId": "string",
        "masterDatabaseName": "string",
        "hardware": {
            "cpuCount": "integer",
            "diskSizeInGb": "integer",
            "ramSizeInGb": "float"
        },
        "state": "string",
        "secondaryAvailabilityZone": "string",
        "backupRetentionEnabled": true|false,
        "pendingModifiedValues": {
            "masterUserPassword": "string",
            "engineVersion": "string",
            "backupRetentionEnabled": true|false
        },
        "engine": "string",
        "engineVersion": "string",
        "latestRestorableTime": "timestamp",
        "masterUsername": "string",
        "parameterApplyStatus": "string",
        "preferredBackupWindow": "string",
        "preferredMaintenanceWindow": "string",
        "publiclyAccessible": true|false,
        "masterEndpoint": {
            "port": "integer",
            "address": "string"
        },
        "pendingMaintenanceActions": [],
        "caCertificateIdentifier": "string"
    }
}
```

---

### 5.5 `get-relational-databases`

Returns information about all managed databases. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-relational-databases \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "relationalDatabases": [
        {
            "name": "string",
            "arn": "string",
            "engine": "string",
            "engineVersion": "string",
            "state": "string",
            "masterUsername": "string",
            "masterEndpoint": {
                "port": "integer",
                "address": "string"
            }
        }
    ],
    "nextPageToken": "string"
}
```

---

### 5.6 `reboot-relational-database`

Reboots a managed database.

**Synopsis:**
```bash
aws lightsail reboot-relational-database \
    --relational-database-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database to reboot |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabase",
            "operationType": "RebootRelationalDatabase",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.7 `start-relational-database`

Starts a stopped managed database.

**Synopsis:**
```bash
aws lightsail start-relational-database \
    --relational-database-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database to start |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabase",
            "operationType": "StartRelationalDatabase",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.8 `stop-relational-database`

Stops a running managed database.

**Synopsis:**
```bash
aws lightsail stop-relational-database \
    --relational-database-name <value> \
    [--relational-database-snapshot-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database to stop |
| `--relational-database-snapshot-name` | No | string | None | Name for a snapshot before stopping |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabase",
            "operationType": "StopRelationalDatabase",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.9 `update-relational-database`

Updates settings for a managed database.

**Synopsis:**
```bash
aws lightsail update-relational-database \
    --relational-database-name <value> \
    [--master-user-password <value>] \
    [--rotate-master-user-password | --no-rotate-master-user-password] \
    [--preferred-backup-window <value>] \
    [--preferred-maintenance-window <value>] \
    [--enable-backup-retention | --disable-backup-retention] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--apply-immediately | --no-apply-immediately] \
    [--ca-certificate-identifier <value>] \
    [--relational-database-blueprint-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |
| `--master-user-password` | No | string | None | New master password |
| `--rotate-master-user-password` | No | boolean | false | Auto-rotate the master password |
| `--preferred-backup-window` | No | string | None | Backup window (UTC) |
| `--preferred-maintenance-window` | No | string | None | Maintenance window |
| `--enable-backup-retention` | No | boolean | None | Enable backup retention |
| `--disable-backup-retention` | No | boolean | None | Disable backup retention |
| `--publicly-accessible` | No | boolean | None | Allow public access |
| `--apply-immediately` | No | boolean | false | Apply changes immediately |
| `--ca-certificate-identifier` | No | string | None | CA certificate identifier |
| `--relational-database-blueprint-id` | No | string | None | New blueprint for engine upgrade |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabase",
            "operationType": "UpdateRelationalDatabase",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.10 `update-relational-database-parameters`

Updates the database engine parameters.

**Synopsis:**
```bash
aws lightsail update-relational-database-parameters \
    --relational-database-name <value> \
    --parameters <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |
| `--parameters` | **Yes** | list | -- | Parameters to update. Shorthand: `parameterName=string,parameterValue=string,applyMethod=immediate\|pending-reboot ...` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabase",
            "operationType": "UpdateRelationalDatabaseParameters",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.11 `get-relational-database-parameters`

Returns the database engine parameters. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-relational-database-parameters \
    --relational-database-name <value> \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "parameters": [
        {
            "allowedValues": "string",
            "applyMethod": "string",
            "applyType": "string",
            "dataType": "string",
            "description": "string",
            "isModifiable": true|false,
            "parameterName": "string",
            "parameterValue": "string"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 5.12 `get-relational-database-master-user-password`

Returns the current master user password for a database.

**Synopsis:**
```bash
aws lightsail get-relational-database-master-user-password \
    --relational-database-name <value> \
    [--password-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |
| `--password-version` | No | string | `CURRENT` | Password version: `CURRENT`, `PREVIOUS`, `PENDING` |

**Output Schema:**
```json
{
    "masterUserPassword": "string",
    "createdAt": "timestamp"
}
```

---

### 5.13 `get-relational-database-metric-data`

Returns metric data for a database.

**Synopsis:**
```bash
aws lightsail get-relational-database-metric-data \
    --relational-database-name <value> \
    --metric-name <value> \
    --period <value> \
    --start-time <value> \
    --end-time <value> \
    --unit <value> \
    --statistics <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |
| `--metric-name` | **Yes** | string | -- | Metric: `CPUUtilization`, `DatabaseConnections`, `DiskQueueDepth`, `FreeStorageSpace`, `NetworkReceiveThroughput`, `NetworkTransmitThroughput` |
| `--period` | **Yes** | integer | -- | Granularity in seconds |
| `--start-time` | **Yes** | timestamp | -- | Start time |
| `--end-time` | **Yes** | timestamp | -- | End time |
| `--unit` | **Yes** | string | -- | Unit for the metric |
| `--statistics` | **Yes** | list(string) | -- | Statistics: `Minimum`, `Maximum`, `Sum`, `Average`, `SampleCount` |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricData": [
        {
            "average": "double",
            "maximum": "double",
            "minimum": "double",
            "sampleCount": "double",
            "sum": "double",
            "timestamp": "timestamp",
            "unit": "string"
        }
    ]
}
```

---

### 5.14 `get-relational-database-events`

Returns events for a database. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-relational-database-events \
    --relational-database-name <value> \
    [--duration-in-minutes <value>] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |
| `--duration-in-minutes` | No | integer | None | Number of minutes to look back |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "relationalDatabaseEvents": [
        {
            "resource": "string",
            "createdAt": "timestamp",
            "message": "string",
            "eventCategories": ["string"]
        }
    ],
    "nextPageToken": "string"
}
```

---

### 5.15 `get-relational-database-log-events`

Returns log events for a database. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-relational-database-log-events \
    --relational-database-name <value> \
    --log-stream-name <value> \
    [--start-time <value>] \
    [--end-time <value>] \
    [--start-from-head | --no-start-from-head] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |
| `--log-stream-name` | **Yes** | string | -- | Name of the log stream (e.g., `error`, `general`, `slowquery`) |
| `--start-time` | No | timestamp | None | Start time for log events |
| `--end-time` | No | timestamp | None | End time for log events |
| `--start-from-head` | No | boolean | false | Start from the earliest log event |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "resourceLogEvents": [
        {
            "createdAt": "timestamp",
            "message": "string"
        }
    ],
    "nextBackwardToken": "string",
    "nextForwardToken": "string"
}
```

---

### 5.16 `get-relational-database-log-streams`

Returns available log streams for a database.

**Synopsis:**
```bash
aws lightsail get-relational-database-log-streams \
    --relational-database-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |

**Output Schema:**
```json
{
    "logStreams": ["string"]
}
```

---

### 5.17 `get-relational-database-blueprints`

Returns available database engine blueprints. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-relational-database-blueprints \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "blueprints": [
        {
            "blueprintId": "string",
            "engine": "string",
            "engineVersion": "string",
            "engineDescription": "string",
            "engineVersionDescription": "string",
            "isEngineDefault": true|false
        }
    ],
    "nextPageToken": "string"
}
```

---

### 5.18 `get-relational-database-bundles`

Returns available database bundles (hardware sizes). **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-relational-database-bundles \
    [--page-token <value>] \
    [--include-inactive | --no-include-inactive] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |
| `--include-inactive` | No | boolean | false | Include inactive bundles |

**Output Schema:**
```json
{
    "bundles": [
        {
            "bundleId": "string",
            "name": "string",
            "price": "float",
            "ramSizeInGb": "float",
            "diskSizeInGb": "integer",
            "transferPerMonthInGb": "integer",
            "cpuCount": "integer",
            "isEncrypted": true|false,
            "isActive": true|false
        }
    ],
    "nextPageToken": "string"
}
```

---

### 5.19 `create-relational-database-snapshot`

Creates a snapshot of a managed database.

**Synopsis:**
```bash
aws lightsail create-relational-database-snapshot \
    --relational-database-name <value> \
    --relational-database-snapshot-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-name` | **Yes** | string | -- | Name of the database |
| `--relational-database-snapshot-name` | **Yes** | string | -- | Name for the snapshot |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabaseSnapshot",
            "operationType": "CreateRelationalDatabaseSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.20 `delete-relational-database-snapshot`

Deletes a database snapshot.

**Synopsis:**
```bash
aws lightsail delete-relational-database-snapshot \
    --relational-database-snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-snapshot-name` | **Yes** | string | -- | Name of the snapshot to delete |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "RelationalDatabaseSnapshot",
            "operationType": "DeleteRelationalDatabaseSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 5.21 `get-relational-database-snapshot`

Returns information about a specific database snapshot.

**Synopsis:**
```bash
aws lightsail get-relational-database-snapshot \
    --relational-database-snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--relational-database-snapshot-name` | **Yes** | string | -- | Name of the snapshot |

**Output Schema:**
```json
{
    "relationalDatabaseSnapshot": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "RelationalDatabaseSnapshot",
        "tags": [],
        "engine": "string",
        "engineVersion": "string",
        "sizeInGb": "integer",
        "state": "string",
        "fromRelationalDatabaseName": "string",
        "fromRelationalDatabaseArn": "string",
        "fromRelationalDatabaseBlueprintId": "string",
        "fromRelationalDatabaseBundleId": "string"
    }
}
```

---

### 5.22 `get-relational-database-snapshots`

Returns all database snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-relational-database-snapshots \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "relationalDatabaseSnapshots": [
        {
            "name": "string",
            "arn": "string",
            "engine": "string",
            "engineVersion": "string",
            "sizeInGb": "integer",
            "state": "string",
            "fromRelationalDatabaseName": "string",
            "createdAt": "timestamp"
        }
    ],
    "nextPageToken": "string"
}
```
