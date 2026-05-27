# Tables

### 4.1 `create-table`

Creates a new table in the Data Catalog.

**Synopsis:**
```bash
aws glue create-table \
    --database-name <value> \
    --table-input <value> \
    [--catalog-id <value>] \
    [--partition-indexes <value>] \
    [--open-table-format-input <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-input` | **Yes** | structure | -- | Table definition (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--partition-indexes` | No | list | -- | Partition indexes to create with the table |
| `--open-table-format-input` | No | structure | -- | Open table format config (Iceberg) |

No output on success.

---

### 4.2 `delete-table`

Deletes a table from the Data Catalog.

**Synopsis:**
```bash
aws glue delete-table \
    --database-name <value> \
    --name <value> \
    [--catalog-id <value>] \
    [--transaction-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--name` | **Yes** | string | -- | Table name |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--transaction-id` | No | string | -- | Transaction ID (for governed tables) |

No output on success.

---

### 4.3 `get-table`

Retrieves a table definition.

**Synopsis:**
```bash
aws glue get-table \
    --database-name <value> \
    --name <value> \
    [--catalog-id <value>] \
    [--transaction-id <value>] \
    [--query-as-of-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--name` | **Yes** | string | -- | Table name |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--transaction-id` | No | string | -- | Transaction ID |
| `--query-as-of-time` | No | timestamp | -- | Point-in-time query |

**Output Schema:**
```json
{
    "Table": {
        "Name": "string",
        "DatabaseName": "string",
        "Description": "string",
        "Owner": "string",
        "CreateTime": "timestamp",
        "UpdateTime": "timestamp",
        "LastAccessTime": "timestamp",
        "LastAnalyzedTime": "timestamp",
        "Retention": "integer",
        "StorageDescriptor": {
            "Columns": [
                {
                    "Name": "string",
                    "Type": "string",
                    "Comment": "string",
                    "Parameters": {}
                }
            ],
            "Location": "string",
            "AdditionalLocations": ["string"],
            "InputFormat": "string",
            "OutputFormat": "string",
            "Compressed": "boolean",
            "NumberOfBuckets": "integer",
            "SerdeInfo": {
                "Name": "string",
                "SerializationLibrary": "string",
                "Parameters": {}
            },
            "BucketColumns": ["string"],
            "SortColumns": [
                {
                    "Column": "string",
                    "SortOrder": "integer"
                }
            ],
            "Parameters": {},
            "StoredAsSubDirectories": "boolean",
            "SchemaReference": {}
        },
        "PartitionKeys": [
            {
                "Name": "string",
                "Type": "string",
                "Comment": "string"
            }
        ],
        "ViewOriginalText": "string",
        "ViewExpandedText": "string",
        "TableType": "string",
        "Parameters": {},
        "CreatedBy": "string",
        "IsRegisteredWithLakeFormation": "boolean",
        "TargetTable": {},
        "CatalogId": "string",
        "VersionId": "string",
        "FederatedTable": {},
        "IsMultiDialectView": "boolean"
    }
}
```

---

### 4.4 `get-tables`

Retrieves tables in a database. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-tables \
    --database-name <value> \
    [--catalog-id <value>] \
    [--expression <value>] \
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
| `--catalog-id` | No | string | -- | Catalog ID |
| `--expression` | No | string | -- | Regular expression filter on table names |
| `--transaction-id` | No | string | -- | Transaction ID |
| `--query-as-of-time` | No | timestamp | -- | Point-in-time query |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "TableList": ["<Table structure>"],
    "NextToken": "string"
}
```

---

### 4.5 `update-table`

Updates a table definition.

**Synopsis:**
```bash
aws glue update-table \
    --database-name <value> \
    --table-input <value> \
    [--catalog-id <value>] \
    [--skip-archive | --no-skip-archive] \
    [--transaction-id <value>] \
    [--version-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-input` | **Yes** | structure | -- | Updated table definition (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--skip-archive` | No | boolean | false | Skip archiving old version |
| `--transaction-id` | No | string | -- | Transaction ID |
| `--version-id` | No | string | -- | Current version ID for optimistic locking |

No output on success.

---

### 4.6 `batch-delete-table`

Deletes multiple tables at once.

**Synopsis:**
```bash
aws glue batch-delete-table \
    --database-name <value> \
    --tables-to-delete <value> \
    [--catalog-id <value>] \
    [--transaction-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--tables-to-delete` | **Yes** | list(string) | -- | Table names to delete |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--transaction-id` | No | string | -- | Transaction ID |

**Output Schema:**
```json
{
    "Errors": [
        {
            "TableName": "string",
            "ErrorDetail": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 4.7 `get-table-version`

Retrieves a specific version of a table.

**Synopsis:**
```bash
aws glue get-table-version \
    --database-name <value> \
    --table-name <value> \
    [--catalog-id <value>] \
    [--version-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--version-id` | No | string | -- | Version ID (latest if omitted) |

**Output Schema:**
```json
{
    "TableVersion": {
        "Table": "<Table structure>",
        "VersionId": "string"
    }
}
```

---

### 4.8 `get-table-versions`

Retrieves all versions of a table. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-table-versions \
    --database-name <value> \
    --table-name <value> \
    [--catalog-id <value>] \
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
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "TableVersions": [
        {
            "Table": "<Table structure>",
            "VersionId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.9 `delete-table-version`

Deletes a specific version of a table.

**Synopsis:**
```bash
aws glue delete-table-version \
    --database-name <value> \
    --table-name <value> \
    --version-id <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--version-id` | **Yes** | string | -- | Version ID to delete |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 4.10 `batch-delete-table-version`

Deletes multiple versions of a table.

**Synopsis:**
```bash
aws glue batch-delete-table-version \
    --database-name <value> \
    --table-name <value> \
    --version-ids <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--version-ids` | **Yes** | list(string) | -- | Version IDs to delete |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Errors": [
        {
            "TableName": "string",
            "VersionId": "string",
            "ErrorDetail": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 4.11 `search-tables`

Searches for tables matching specified criteria. **Paginated operation.**

**Synopsis:**
```bash
aws glue search-tables \
    [--catalog-id <value>] \
    [--filters <value>] \
    [--search-text <value>] \
    [--sort-criteria <value>] \
    [--resource-share-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | -- | Catalog ID |
| `--filters` | No | list | -- | Property predicates for filtering |
| `--search-text` | No | string | -- | Text to search for |
| `--sort-criteria` | No | list | -- | Sort criteria |
| `--resource-share-type` | No | string | -- | `FOREIGN`, `ALL`, `FEDERATED` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "TableList": ["<Table structure>"],
    "NextToken": "string"
}
```
