# Partitions

### 5.1 `create-partition`

Creates a new partition in a table.

**Synopsis:**
```bash
aws glue create-partition \
    --database-name <value> \
    --table-name <value> \
    --partition-input <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-input` | **Yes** | structure | -- | Partition definition (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 5.2 `delete-partition`

Deletes a partition from a table.

**Synopsis:**
```bash
aws glue delete-partition \
    --database-name <value> \
    --table-name <value> \
    --partition-values <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-values` | **Yes** | list(string) | -- | Partition key values |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 5.3 `get-partition`

Retrieves a partition definition.

**Synopsis:**
```bash
aws glue get-partition \
    --database-name <value> \
    --table-name <value> \
    --partition-values <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-values` | **Yes** | list(string) | -- | Partition key values |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Partition": {
        "Values": ["string"],
        "DatabaseName": "string",
        "TableName": "string",
        "CreationTime": "timestamp",
        "LastAccessTime": "timestamp",
        "StorageDescriptor": {
            "Columns": [
                {
                    "Name": "string",
                    "Type": "string",
                    "Comment": "string"
                }
            ],
            "Location": "string",
            "InputFormat": "string",
            "OutputFormat": "string",
            "SerdeInfo": {
                "SerializationLibrary": "string",
                "Parameters": {}
            },
            "Parameters": {}
        },
        "Parameters": {},
        "LastAnalyzedTime": "timestamp",
        "CatalogId": "string"
    }
}
```

---

### 5.4 `get-partitions`

Retrieves partitions for a table. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-partitions \
    --database-name <value> \
    --table-name <value> \
    [--catalog-id <value>] \
    [--expression <value>] \
    [--segment <value>] \
    [--exclude-column-schema | --no-exclude-column-schema] \
    [--transaction-id <value>] \
    [--query-as-of-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--expression` | No | string | -- | Filter expression (e.g., `year='2024'`) |
| `--segment` | No | structure | -- | Segment for parallel reads. Shorthand: `SegmentNumber=integer,TotalSegments=integer` |
| `--exclude-column-schema` | No | boolean | false | Exclude column schema from results |
| `--transaction-id` | No | string | -- | Transaction ID |
| `--query-as-of-time` | No | timestamp | -- | Point-in-time query |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Partitions": ["<Partition structure>"],
    "NextToken": "string"
}
```

---

### 5.5 `update-partition`

Updates a partition definition.

**Synopsis:**
```bash
aws glue update-partition \
    --database-name <value> \
    --table-name <value> \
    --partition-value-list <value> \
    --partition-input <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-value-list` | **Yes** | list(string) | -- | Current partition values |
| `--partition-input` | **Yes** | structure | -- | Updated partition definition (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 5.6 `batch-create-partition`

Creates multiple partitions in a batch.

**Synopsis:**
```bash
aws glue batch-create-partition \
    --database-name <value> \
    --table-name <value> \
    --partition-input-list <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-input-list` | **Yes** | list | -- | List of partition definitions (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Errors": [
        {
            "PartitionValues": ["string"],
            "ErrorDetail": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 5.7 `batch-delete-partition`

Deletes multiple partitions in a batch.

**Synopsis:**
```bash
aws glue batch-delete-partition \
    --database-name <value> \
    --table-name <value> \
    --partitions-to-delete <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partitions-to-delete` | **Yes** | list | -- | List of partition value lists (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Errors": [
        {
            "PartitionValues": ["string"],
            "ErrorDetail": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 5.8 `batch-get-partition`

Retrieves multiple partitions in a batch.

**Synopsis:**
```bash
aws glue batch-get-partition \
    --database-name <value> \
    --table-name <value> \
    --partitions-to-get <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partitions-to-get` | **Yes** | list | -- | List of partition value lists (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Partitions": ["<Partition structure>"],
    "UnprocessedKeys": [
        {
            "Values": ["string"]
        }
    ]
}
```

---

### 5.9 `batch-update-partition`

Updates multiple partitions in a batch.

**Synopsis:**
```bash
aws glue batch-update-partition \
    --database-name <value> \
    --table-name <value> \
    --entries <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--entries` | **Yes** | list | -- | List of partition value/input pairs (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Errors": [
        {
            "PartitionValueList": ["string"],
            "ErrorDetail": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 5.10 `get-partition-indexes`

Lists partition indexes for a table. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-partition-indexes \
    --database-name <value> \
    --table-name <value> \
    [--catalog-id <value>] \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--starting-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "PartitionIndexDescriptorList": [
        {
            "IndexName": "string",
            "Keys": [
                {
                    "Name": "string",
                    "Type": "string"
                }
            ],
            "IndexStatus": "CREATING|ACTIVE|DELETING|FAILED"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.11 `create-partition-index`

Creates a partition index on a table.

**Synopsis:**
```bash
aws glue create-partition-index \
    --database-name <value> \
    --table-name <value> \
    --partition-index <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-index` | **Yes** | structure | -- | Index definition. Shorthand: `Keys=string,string,IndexName=string` |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 5.12 `delete-partition-index`

Deletes a partition index from a table.

**Synopsis:**
```bash
aws glue delete-partition-index \
    --database-name <value> \
    --table-name <value> \
    --index-name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--index-name` | **Yes** | string | -- | Partition index name |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.
