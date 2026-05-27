# Tables

## 2.1 `create-table`

Creates a new table in a keyspace.

**Synopsis:**
```bash
aws keyspaces create-table \
    --keyspace-name <value> \
    --table-name <value> \
    --schema-definition <value> \
    [--comment <value>] \
    [--capacity-specification <value>] \
    [--encryption-specification <value>] \
    [--point-in-time-recovery <value>] \
    [--ttl <value>] \
    [--default-time-to-live <value>] \
    [--tags <value>] \
    [--client-side-timestamps <value>] \
    [--auto-scaling-specification <value>] \
    [--replica-specifications <value>] \
    [--cdc-specification <value>] \
    [--warm-throughput-specification <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--table-name` | **Yes** | string | -- | Table name (1-48 chars) |
| `--schema-definition` | **Yes** | structure | -- | Table schema (columns, partition keys, clustering keys) |
| `--comment` | No | structure | None | Table description. Shorthand: `message=string` |
| `--capacity-specification` | No | structure | `PAY_PER_REQUEST` | Throughput mode and capacity units |
| `--encryption-specification` | No | structure | `AWS_OWNED_KMS_KEY` | Encryption settings |
| `--point-in-time-recovery` | No | structure | `DISABLED` | PITR status |
| `--ttl` | No | structure | `DISABLED` | TTL status. Shorthand: `status=ENABLED` |
| `--default-time-to-live` | No | integer | None | Default TTL in seconds (0-630720000) |
| `--tags` | No | list | None | Key-value tags (max 60) |
| `--client-side-timestamps` | No | structure | `DISABLED` | Client-side timestamps. Shorthand: `status=ENABLED` |
| `--auto-scaling-specification` | No | structure | None | Auto-scaling for read/write capacity |
| `--replica-specifications` | No | list | None | Multi-region replica settings |
| `--cdc-specification` | No | structure | None | Change Data Capture settings |
| `--warm-throughput-specification` | No | structure | None | Pre-warming configuration |

**Schema Definition Structure:**
```json
{
    "allColumns": [
        { "name": "user_id", "type": "uuid" },
        { "name": "email", "type": "text" },
        { "name": "created_at", "type": "timestamp" },
        { "name": "status", "type": "text" }
    ],
    "partitionKeys": [
        { "name": "user_id" }
    ],
    "clusteringKeys": [
        { "name": "created_at", "orderBy": "DESC" }
    ],
    "staticColumns": [
        { "name": "status" }
    ]
}
```

**Capacity Specification Structure:**
```json
{
    "throughputMode": "PAY_PER_REQUEST|PROVISIONED",
    "readCapacityUnits": 100,
    "writeCapacityUnits": 100
}
```

**Auto-Scaling Specification Structure:**
```json
{
    "writeCapacityAutoScaling": {
        "autoScalingDisabled": false,
        "minimumUnits": 5,
        "maximumUnits": 1000,
        "scalingPolicy": {
            "targetTrackingScalingPolicyConfiguration": {
                "disableScaleIn": false,
                "scaleInCooldown": 60,
                "scaleOutCooldown": 60,
                "targetValue": 70.0
            }
        }
    },
    "readCapacityAutoScaling": {
        "autoScalingDisabled": false,
        "minimumUnits": 5,
        "maximumUnits": 1000,
        "scalingPolicy": {
            "targetTrackingScalingPolicyConfiguration": {
                "targetValue": 70.0
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "resourceArn": "string"
}
```

---

## 2.2 `delete-table`

Deletes a table from a keyspace.

**Synopsis:**
```bash
aws keyspaces delete-table \
    --keyspace-name <value> \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--table-name` | **Yes** | string | -- | Table name to delete |

**Output Schema:**

None (HTTP 200 on success).

---

## 2.3 `get-table`

Returns details for a table including schema, capacity, encryption, PITR, TTL, and CDC settings.

**Synopsis:**
```bash
aws keyspaces get-table \
    --keyspace-name <value> \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--table-name` | **Yes** | string | -- | Table name |

**Output Schema:**
```json
{
    "keyspaceName": "string",
    "tableName": "string",
    "resourceArn": "string",
    "creationTimestamp": "timestamp",
    "status": "ACTIVE|CREATING|UPDATING|DELETING|DELETED|RESTORING|INACCESSIBLE_ENCRYPTION_CREDENTIALS",
    "schemaDefinition": {
        "allColumns": [
            { "name": "string", "type": "string" }
        ],
        "partitionKeys": [
            { "name": "string" }
        ],
        "clusteringKeys": [
            { "name": "string", "orderBy": "ASC|DESC" }
        ],
        "staticColumns": [
            { "name": "string" }
        ]
    },
    "capacitySpecification": {
        "throughputMode": "PAY_PER_REQUEST|PROVISIONED",
        "readCapacityUnits": "long",
        "writeCapacityUnits": "long",
        "lastUpdateToPayPerRequestTimestamp": "timestamp"
    },
    "encryptionSpecification": {
        "type": "CUSTOMER_MANAGED_KMS_KEY|AWS_OWNED_KMS_KEY",
        "kmsKeyIdentifier": "string"
    },
    "pointInTimeRecovery": {
        "status": "ENABLED|DISABLED",
        "earliestRestorableTimestamp": "timestamp"
    },
    "ttl": {
        "status": "ENABLED"
    },
    "defaultTimeToLive": "integer",
    "comment": {
        "message": "string"
    },
    "clientSideTimestamps": {
        "status": "ENABLED"
    },
    "replicaSpecifications": [
        {
            "region": "string",
            "status": "string",
            "capacitySpecification": {},
            "warmThroughputSpecification": {}
        }
    ],
    "latestStreamArn": "string",
    "cdcSpecification": {
        "status": "ENABLED|ENABLING|DISABLED|DISABLING",
        "viewType": "NEW_IMAGE|OLD_IMAGE|KEYS_ONLY|NEW_AND_OLD_IMAGES"
    },
    "warmThroughputSpecification": {
        "readUnitsPerSecond": "long",
        "writeUnitsPerSecond": "long",
        "status": "AVAILABLE|UPDATING"
    }
}
```

---

## 2.4 `list-tables`

Lists tables in a keyspace. **Paginated operation.**

**Synopsis:**
```bash
aws keyspaces list-tables \
    --keyspace-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "tables": [
        {
            "keyspaceName": "string",
            "tableName": "string",
            "resourceArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 2.5 `update-table`

Updates a table's configuration (capacity, encryption, PITR, TTL, columns, CDC, etc.).

**Synopsis:**
```bash
aws keyspaces update-table \
    --keyspace-name <value> \
    --table-name <value> \
    [--add-columns <value>] \
    [--capacity-specification <value>] \
    [--encryption-specification <value>] \
    [--point-in-time-recovery <value>] \
    [--ttl <value>] \
    [--default-time-to-live <value>] \
    [--client-side-timestamps <value>] \
    [--auto-scaling-specification <value>] \
    [--replica-specifications <value>] \
    [--cdc-specification <value>] \
    [--warm-throughput-specification <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--add-columns` | No | list | None | New columns to add |
| `--capacity-specification` | No | structure | None | Updated capacity settings |
| `--encryption-specification` | No | structure | None | Updated encryption settings |
| `--point-in-time-recovery` | No | structure | None | PITR settings. Shorthand: `status=ENABLED\|DISABLED` |
| `--ttl` | No | structure | None | TTL settings. Shorthand: `status=ENABLED` |
| `--default-time-to-live` | No | integer | None | Default TTL in seconds |
| `--client-side-timestamps` | No | structure | None | Client-side timestamps |
| `--auto-scaling-specification` | No | structure | None | Auto-scaling settings |
| `--replica-specifications` | No | list | None | Multi-region replica settings |
| `--cdc-specification` | No | structure | None | CDC settings |
| `--warm-throughput-specification` | No | structure | None | Pre-warming configuration |

**Output Schema:**
```json
{
    "resourceArn": "string"
}
```

---

## 2.6 `restore-table`

Restores a table to a point in time from backup.

**Synopsis:**
```bash
aws keyspaces restore-table \
    --source-keyspace-name <value> \
    --source-table-name <value> \
    --target-keyspace-name <value> \
    --target-table-name <value> \
    [--restore-timestamp <value>] \
    [--capacity-specification-override <value>] \
    [--encryption-specification-override <value>] \
    [--point-in-time-recovery-override <value>] \
    [--tags-override <value>] \
    [--auto-scaling-specification <value>] \
    [--replica-specifications <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-keyspace-name` | **Yes** | string | -- | Source keyspace name |
| `--source-table-name` | **Yes** | string | -- | Source table name |
| `--target-keyspace-name` | **Yes** | string | -- | Target keyspace name |
| `--target-table-name` | **Yes** | string | -- | Target table name |
| `--restore-timestamp` | No | timestamp | None | Point-in-time to restore to (if omitted, restores to latest) |
| `--capacity-specification-override` | No | structure | None | Override capacity for restored table |
| `--encryption-specification-override` | No | structure | None | Override encryption for restored table |
| `--point-in-time-recovery-override` | No | structure | None | Override PITR for restored table |
| `--tags-override` | No | list | None | Override tags for restored table |
| `--auto-scaling-specification` | No | structure | None | Auto-scaling for restored table |
| `--replica-specifications` | No | list | None | Replica settings for restored table |

**Output Schema:**
```json
{
    "restoredTableARN": "string"
}
```

---

## 2.7 `get-table-auto-scaling-settings`

Returns the auto-scaling settings for a table.

**Synopsis:**
```bash
aws keyspaces get-table-auto-scaling-settings \
    --keyspace-name <value> \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--table-name` | **Yes** | string | -- | Table name |

**Output Schema:**
```json
{
    "keyspaceName": "string",
    "tableName": "string",
    "resourceArn": "string",
    "autoScalingSpecification": {
        "writeCapacityAutoScaling": {
            "autoScalingDisabled": "boolean",
            "minimumUnits": "long",
            "maximumUnits": "long",
            "scalingPolicy": {
                "targetTrackingScalingPolicyConfiguration": {
                    "disableScaleIn": "boolean",
                    "scaleInCooldown": "integer",
                    "scaleOutCooldown": "integer",
                    "targetValue": "double"
                }
            }
        },
        "readCapacityAutoScaling": {
            "autoScalingDisabled": "boolean",
            "minimumUnits": "long",
            "maximumUnits": "long",
            "scalingPolicy": {
                "targetTrackingScalingPolicyConfiguration": {
                    "disableScaleIn": "boolean",
                    "scaleInCooldown": "integer",
                    "scaleOutCooldown": "integer",
                    "targetValue": "double"
                }
            }
        }
    },
    "replicaSpecifications": [
        {
            "region": "string",
            "autoScalingSpecification": {}
        }
    ]
}
```
