# Databases & Tables

### 1.1 `create-database`

Creates a new Timestream database.

**Synopsis:**
```bash
aws timestream-write create-database \
    --database-name <value> \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name. Pattern: `[a-zA-Z0-9_.-]+` |
| `--kms-key-id` | No | string | Timestream-managed key | KMS key for encryption (1-2048 chars) |
| `--tags` | No | list | None | Key-value tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Database": {
        "Arn": "string",
        "DatabaseName": "string",
        "TableCount": "long",
        "KmsKeyId": "string",
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 1.2 `describe-database`

Describes a Timestream database.

**Synopsis:**
```bash
aws timestream-write describe-database \
    --database-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |

**Output Schema:**
```json
{
    "Database": {
        "Arn": "string",
        "DatabaseName": "string",
        "TableCount": "long",
        "KmsKeyId": "string",
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 1.3 `update-database`

Updates the KMS key for an existing database. While updating, the database is still accessible for read and write operations.

**Synopsis:**
```bash
aws timestream-write update-database \
    --database-name <value> \
    --kms-key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--kms-key-id` | **Yes** | string | -- | New KMS key identifier (1-2048 chars) |

**Output Schema:**
```json
{
    "Database": {
        "Arn": "string",
        "DatabaseName": "string",
        "TableCount": "long",
        "KmsKeyId": "string",
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 1.4 `delete-database`

Deletes a Timestream database. All tables in the database must be deleted first. Deleting a database is an irreversible operation.

**Synopsis:**
```bash
aws timestream-write delete-database \
    --database-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name to delete |

**Output:** None

---

### 1.5 `list-databases`

Returns a list of Timestream databases. **Paginated operation.**

**Synopsis:**
```bash
aws timestream-write list-databases \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max: 20) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Databases": [
        {
            "Arn": "string",
            "DatabaseName": "string",
            "TableCount": "long",
            "KmsKeyId": "string",
            "CreationTime": "timestamp",
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `create-table`

Creates a new table in an existing database.

**Synopsis:**
```bash
aws timestream-write create-table \
    --database-name <value> \
    --table-name <value> \
    [--retention-properties <value>] \
    [--tags <value>] \
    [--magnetic-store-write-properties <value>] \
    [--schema <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name. Pattern: `[a-zA-Z0-9_.-]+` |
| `--retention-properties` | No | structure | memory=6h, magnetic=73000d | Retention durations for memory and magnetic stores |
| `--tags` | No | list | None | Key-value tags (max 200) |
| `--magnetic-store-write-properties` | No | structure | None | Enable magnetic store writes and configure rejected data location |
| `--schema` | No | structure | None | Schema with composite partition key definitions |

**Retention Properties Structure:**
```json
{
    "MemoryStoreRetentionPeriodInHours": 24,
    "MagneticStoreRetentionPeriodInDays": 365
}
```
- `MemoryStoreRetentionPeriodInHours`: min 1, max 8766 (1 year)
- `MagneticStoreRetentionPeriodInDays`: min 1, max 73000 (200 years)

**Magnetic Store Write Properties:**
```json
{
    "EnableMagneticStoreWrites": true,
    "MagneticStoreRejectedDataLocation": {
        "S3Configuration": {
            "BucketName": "string",
            "ObjectKeyPrefix": "string",
            "EncryptionOption": "SSE_S3|SSE_KMS",
            "KmsKeyId": "string"
        }
    }
}
```

**Schema Structure:**
```json
{
    "CompositePartitionKey": [
        {
            "Type": "DIMENSION|MEASURE",
            "Name": "string",
            "EnforcementInRecord": "REQUIRED|OPTIONAL"
        }
    ]
}
```

**Output Schema:**
```json
{
    "Table": {
        "Arn": "string",
        "TableName": "string",
        "DatabaseName": "string",
        "TableStatus": "ACTIVE|DELETING|RESTORING",
        "RetentionProperties": {
            "MemoryStoreRetentionPeriodInHours": "long",
            "MagneticStoreRetentionPeriodInDays": "long"
        },
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "MagneticStoreWriteProperties": {
            "EnableMagneticStoreWrites": "boolean",
            "MagneticStoreRejectedDataLocation": {
                "S3Configuration": {
                    "BucketName": "string",
                    "ObjectKeyPrefix": "string",
                    "EncryptionOption": "SSE_S3|SSE_KMS",
                    "KmsKeyId": "string"
                }
            }
        },
        "Schema": {
            "CompositePartitionKey": [
                {
                    "Type": "DIMENSION|MEASURE",
                    "Name": "string",
                    "EnforcementInRecord": "REQUIRED|OPTIONAL"
                }
            ]
        }
    }
}
```

---

### 1.7 `describe-table`

Describes a Timestream table.

**Synopsis:**
```bash
aws timestream-write describe-table \
    --database-name <value> \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |

**Output Schema:** Same as `create-table` output.

---

### 1.8 `update-table`

Updates retention properties, magnetic store writes, and schema for an existing table. Changes take effect immediately.

**Synopsis:**
```bash
aws timestream-write update-table \
    --database-name <value> \
    --table-name <value> \
    [--retention-properties <value>] \
    [--magnetic-store-write-properties <value>] \
    [--schema <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--retention-properties` | No | structure | unchanged | Updated retention durations |
| `--magnetic-store-write-properties` | No | structure | unchanged | Updated magnetic store write configuration |
| `--schema` | No | structure | unchanged | Updated schema (only enforcement level can be changed) |

**Output Schema:** Same as `create-table` output.

---

### 1.9 `delete-table`

Deletes a Timestream table. This is an irreversible operation — all data in the table is deleted.

**Synopsis:**
```bash
aws timestream-write delete-table \
    --database-name <value> \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name to delete |

**Output:** None

---

### 1.10 `list-tables`

Returns a list of tables in a database. **Paginated operation.**

**Synopsis:**
```bash
aws timestream-write list-tables \
    [--database-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | No | string | None | Filter by database name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max: 20) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Tables": [
        {
            "Arn": "string",
            "TableName": "string",
            "DatabaseName": "string",
            "TableStatus": "ACTIVE|DELETING|RESTORING",
            "RetentionProperties": {
                "MemoryStoreRetentionPeriodInHours": "long",
                "MagneticStoreRetentionPeriodInDays": "long"
            },
            "CreationTime": "timestamp",
            "LastUpdatedTime": "timestamp",
            "MagneticStoreWriteProperties": {},
            "Schema": {}
        }
    ],
    "NextToken": "string"
}
```
