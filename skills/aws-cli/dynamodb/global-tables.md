# Global Tables

### 10.1 `create-global-table`

Creates a global table from one or more existing identical DynamoDB tables. Tables must have streams enabled.

**Synopsis:**
```bash
aws dynamodb create-global-table \
    --global-table-name <value> \
    --replication-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-table-name` | **Yes** | string | -- | Global table name (3-255 chars) |
| `--replication-group` | **Yes** | list | -- | Regions for the global table. Shorthand: `RegionName=string ...` |

**Output Schema:**
```json
{
    "GlobalTableDescription": {
        "ReplicationGroup": [
            { "RegionName": "string" }
        ],
        "GlobalTableArn": "string",
        "CreationDateTime": "timestamp",
        "GlobalTableStatus": "CREATING|ACTIVE|DELETING|UPDATING",
        "GlobalTableName": "string"
    }
}
```

---

### 10.2 `describe-global-table`

Describes a global table.

**Synopsis:**
```bash
aws dynamodb describe-global-table \
    --global-table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-table-name` | **Yes** | string | -- | Global table name (3-255 chars) |

**Output Schema:** Same as `create-global-table`.

---

### 10.3 `list-global-tables`

Lists all global tables with a given region as a replica.

**Synopsis:**
```bash
aws dynamodb list-global-tables \
    [--exclusive-start-global-table-name <value>] \
    [--limit <value>] \
    [--region-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--exclusive-start-global-table-name` | No | string | -- | Pagination: start after this table name |
| `--limit` | No | integer | -- | Max tables to return |
| `--region-name` | No | string | -- | Filter by replica region |

**Output Schema:**
```json
{
    "GlobalTables": [
        {
            "GlobalTableName": "string",
            "ReplicationGroup": [
                { "RegionName": "string" }
            ]
        }
    ],
    "LastEvaluatedGlobalTableName": "string"
}
```

---

### 10.4 `update-global-table`

Adds or removes replicas from a global table.

**Synopsis:**
```bash
aws dynamodb update-global-table \
    --global-table-name <value> \
    --replica-updates <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-table-name` | **Yes** | string | -- | Global table name (3-255 chars) |
| `--replica-updates` | **Yes** | list | -- | List of Create or Delete actions. Each has `RegionName` |

**Output Schema:** Same as `create-global-table`.

---

### 10.5 `describe-global-table-settings`

Describes region-specific settings for a global table.

**Synopsis:**
```bash
aws dynamodb describe-global-table-settings \
    --global-table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-table-name` | **Yes** | string | -- | Global table name (3-255 chars) |

**Output Schema:**
```json
{
    "GlobalTableName": "string",
    "ReplicaSettings": [
        {
            "RegionName": "string",
            "ReplicaStatus": "CREATING|CREATION_FAILED|UPDATING|DELETING|ACTIVE",
            "ReplicaBillingModeSummary": {},
            "ReplicaProvisionedReadCapacityUnits": "long",
            "ReplicaProvisionedReadCapacityAutoScalingSettings": {},
            "ReplicaProvisionedWriteCapacityUnits": "long",
            "ReplicaProvisionedWriteCapacityAutoScalingSettings": {},
            "ReplicaGlobalSecondaryIndexSettings": [
                {
                    "IndexName": "string",
                    "IndexStatus": "CREATING|UPDATING|DELETING|ACTIVE",
                    "ProvisionedReadCapacityUnits": "long",
                    "ProvisionedReadCapacityAutoScalingSettings": {},
                    "ProvisionedWriteCapacityUnits": "long",
                    "ProvisionedWriteCapacityAutoScalingSettings": {}
                }
            ],
            "ReplicaTableClassSummary": {}
        }
    ]
}
```

---

### 10.6 `update-global-table-settings`

Updates settings for a global table (throughput, auto-scaling) on all replicas.

**Synopsis:**
```bash
aws dynamodb update-global-table-settings \
    --global-table-name <value> \
    [--global-table-billing-mode <value>] \
    [--global-table-provisioned-write-capacity-units <value>] \
    [--global-table-provisioned-write-capacity-auto-scaling-settings-update <value>] \
    [--global-table-global-secondary-index-settings-update <value>] \
    [--replica-settings-update <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-table-name` | **Yes** | string | -- | Global table name (3-255 chars) |
| `--global-table-billing-mode` | No | string | -- | `PROVISIONED` or `PAY_PER_REQUEST` |
| `--global-table-provisioned-write-capacity-units` | No | long | -- | Global write capacity units (min: 1) |
| `--global-table-provisioned-write-capacity-auto-scaling-settings-update` | No | structure | -- | Auto-scaling settings for write capacity |
| `--global-table-global-secondary-index-settings-update` | No | list | -- | GSI settings updates |
| `--replica-settings-update` | No | list | -- | Per-replica settings updates |

**Output Schema:** Same as `describe-global-table-settings`.

---
