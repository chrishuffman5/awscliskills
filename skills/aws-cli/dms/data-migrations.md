# Data Migrations

Data migrations work with migration projects and data providers to perform homogeneous database migrations at scale.

### 6.1 `create-data-migration`

Creates a data migration using the provided settings.

**Synopsis:**
```bash
aws dms create-data-migration \
    --migration-project-identifier <value> \
    --data-migration-type <value> \
    --service-access-role-arn <value> \
    [--data-migration-name <value>] \
    [--enable-cloudwatch-logs | --no-enable-cloudwatch-logs] \
    [--source-data-settings <value>] \
    [--target-data-settings <value>] \
    [--number-of-jobs <value>] \
    [--tags <value>] \
    [--selection-rules <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier |
| `--data-migration-type` | **Yes** | string | -- | `full-load`, `cdc`, or `full-load-and-cdc` |
| `--service-access-role-arn` | **Yes** | string | -- | Service access IAM role ARN |
| `--data-migration-name` | No | string | -- | User-friendly name (1-255 chars) |
| `--enable-cloudwatch-logs` | No | boolean | -- | Enable CloudWatch logs |
| `--source-data-settings` | No | list | -- | Source data settings (CDC start position/time, slot name) |
| `--target-data-settings` | No | list | -- | Target data settings (table preparation mode) |
| `--number-of-jobs` | No | integer | -- | Number of parallel jobs |
| `--tags` | No | list | -- | Tags |
| `--selection-rules` | No | string | -- | JSON selection rules for tables/schemas |

**Source Data Settings Structure:**
```json
[
    {
        "CDCStartPosition": "string",
        "CDCStartTime": "timestamp",
        "CDCStopTime": "timestamp",
        "SlotName": "string"
    }
]
```

**Target Data Settings Structure:**
```json
[
    {
        "TablePreparationMode": "drop-tables-on-target|truncate|do-nothing"
    }
]
```

**Output Schema:**
```json
{
    "DataMigration": {
        "DataMigrationName": "string",
        "DataMigrationArn": "string",
        "DataMigrationCreateTime": "timestamp",
        "DataMigrationStartTime": "timestamp",
        "DataMigrationEndTime": "timestamp",
        "ServiceAccessRoleArn": "string",
        "MigrationProjectArn": "string",
        "DataMigrationType": "string",
        "DataMigrationSettings": {
            "NumberOfJobs": "integer",
            "CloudwatchLogsEnabled": "boolean",
            "SelectionRules": "string"
        },
        "SourceDataSettings": [],
        "TargetDataSettings": [],
        "DataMigrationStatistics": {
            "TablesLoaded": "integer",
            "ElapsedTimeMillis": "long",
            "FullLoadPercentage": "integer",
            "CDCLatency": "integer"
        },
        "DataMigrationStatus": "string",
        "PublicIpAddresses": ["string"],
        "DataMigrationCidrBlocks": ["string"],
        "LastFailureMessage": "string",
        "StopReason": "string"
    }
}
```

---

### 6.2 `delete-data-migration`

Deletes the specified data migration.

**Synopsis:**
```bash
aws dms delete-data-migration \
    --data-migration-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-migration-identifier` | **Yes** | string | -- | Data migration identifier or ARN |

**Output Schema:** Same as `create-data-migration`.

---

### 6.3 `describe-data-migrations`

Returns information about data migrations. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-data-migrations \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--without-settings | --no-without-settings] \
    [--without-statistics | --no-without-statistics] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `data-migration-arn`, `data-migration-name`, `migration-project-identifier`, `service-access-role-arn`, `data-migration-type` |
| `--without-settings` | No | boolean | false | Omit settings to reduce overhead |
| `--without-statistics` | No | boolean | false | Omit statistics to reduce overhead |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "DataMigrations": [
        {
            "DataMigrationName": "string",
            "DataMigrationArn": "string",
            "DataMigrationCreateTime": "timestamp",
            "DataMigrationStartTime": "timestamp",
            "DataMigrationEndTime": "timestamp",
            "ServiceAccessRoleArn": "string",
            "MigrationProjectArn": "string",
            "DataMigrationType": "string",
            "DataMigrationSettings": {},
            "SourceDataSettings": [],
            "TargetDataSettings": [],
            "DataMigrationStatistics": {},
            "DataMigrationStatus": "string",
            "PublicIpAddresses": ["string"],
            "LastFailureMessage": "string",
            "StopReason": "string"
        }
    ]
}
```

---

### 6.4 `modify-data-migration`

Modifies an existing data migration.

**Synopsis:**
```bash
aws dms modify-data-migration \
    --data-migration-identifier <value> \
    [--data-migration-name <value>] \
    [--enable-cloudwatch-logs | --no-enable-cloudwatch-logs] \
    [--service-access-role-arn <value>] \
    [--data-migration-type <value>] \
    [--source-data-settings <value>] \
    [--target-data-settings <value>] \
    [--number-of-jobs <value>] \
    [--selection-rules <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-migration-identifier` | **Yes** | string | -- | Data migration identifier or ARN |
| `--data-migration-name` | No | string | -- | New name |
| `--enable-cloudwatch-logs` | No | boolean | -- | Enable/disable CloudWatch logs |
| `--service-access-role-arn` | No | string | -- | New service access role |
| `--data-migration-type` | No | string | -- | New migration type |
| `--source-data-settings` | No | list | -- | New source data settings |
| `--target-data-settings` | No | list | -- | New target data settings |
| `--number-of-jobs` | No | integer | -- | New number of parallel jobs |
| `--selection-rules` | No | string | -- | New selection rules |

**Output Schema:** Same as `create-data-migration`.

---

### 6.5 `start-data-migration`

Starts the specified data migration.

**Synopsis:**
```bash
aws dms start-data-migration \
    --data-migration-identifier <value> \
    --start-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-migration-identifier` | **Yes** | string | -- | Data migration identifier or ARN |
| `--start-type` | **Yes** | string | -- | `start-replication`, `resume-processing`, or `reload-target` |

**Output Schema:** Same as `create-data-migration`.

---

### 6.6 `stop-data-migration`

Stops the specified data migration.

**Synopsis:**
```bash
aws dms stop-data-migration \
    --data-migration-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-migration-identifier` | **Yes** | string | -- | Data migration identifier or ARN |

**Output Schema:** Same as `create-data-migration`.
