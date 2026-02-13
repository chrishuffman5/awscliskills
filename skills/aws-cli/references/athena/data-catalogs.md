# Data Catalogs

### 5.1 `create-data-catalog`

Registers a data catalog (Glue, Hive metastore, or Lambda connector).

**Synopsis:**
```bash
aws athena create-data-catalog \
    --name <value> \
    --type <value> \
    [--description <value>] \
    [--parameters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Catalog name |
| `--type` | **Yes** | string | -- | `LAMBDA`, `GLUE`, or `HIVE` |
| `--description` | No | string | -- | Description |
| `--parameters` | No | map | -- | Parameters. For LAMBDA: `function=<arn>`. For HIVE: `metadata-function=<arn>,sdk-version=<version>` |
| `--tags` | No | list | -- | Tags |

No output on success.

---

### 5.2 `delete-data-catalog`

Deletes a data catalog.

**Synopsis:**
```bash
aws athena delete-data-catalog \
    --name <value> \
    [--delete-catalog-only | --no-delete-catalog-only] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Catalog to delete |
| `--delete-catalog-only` | No | boolean | -- | Delete catalog registration only (keep underlying resource) |

No output on success.

---

### 5.3 `get-data-catalog`

Returns information about a data catalog.

**Synopsis:**
```bash
aws athena get-data-catalog \
    --name <value> \
    [--work-group <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Catalog name |
| `--work-group` | No | string | -- | Workgroup context |

**Output Schema:**
```json
{
    "DataCatalog": {
        "Name": "string",
        "Description": "string",
        "Type": "LAMBDA|GLUE|HIVE",
        "Parameters": {"string": "string"},
        "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|CREATE_FAILED_CLEANUP|DELETE_IN_PROGRESS|DELETE_COMPLETE|DELETE_FAILED"
    }
}
```

---

### 5.4 `update-data-catalog`

Updates a data catalog.

**Synopsis:**
```bash
aws athena update-data-catalog \
    --name <value> \
    --type <value> \
    [--description <value>] \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Catalog to update |
| `--type` | **Yes** | string | -- | Catalog type |
| `--description` | No | string | -- | New description |
| `--parameters` | No | map | -- | New parameters |

No output on success.

---

### 5.5 `list-data-catalogs`

Lists data catalogs. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-data-catalogs \
    [--work-group <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | No | string | -- | Workgroup context |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "DataCatalogsSummary": [
        {
            "CatalogName": "string",
            "Type": "LAMBDA|GLUE|HIVE",
            "Status": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.6 `get-database`

Returns database metadata from a data catalog.

**Synopsis:**
```bash
aws athena get-database \
    --catalog-name <value> \
    --database-name <value> \
    [--work-group <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-name` | **Yes** | string | -- | Catalog name |
| `--database-name` | **Yes** | string | -- | Database name |
| `--work-group` | No | string | -- | Workgroup context |

**Output Schema:**
```json
{
    "Database": {
        "Name": "string",
        "Description": "string",
        "Parameters": {"string": "string"}
    }
}
```

---

### 5.7 `list-databases`

Lists databases in a data catalog. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-databases \
    --catalog-name <value> \
    [--work-group <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-name` | **Yes** | string | -- | Catalog name |
| `--work-group` | No | string | -- | Workgroup context |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "DatabaseList": [
        {
            "Name": "string",
            "Description": "string",
            "Parameters": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 5.8 `get-table-metadata`

Returns table metadata from a data catalog.

**Synopsis:**
```bash
aws athena get-table-metadata \
    --catalog-name <value> \
    --database-name <value> \
    --table-name <value> \
    [--work-group <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-name` | **Yes** | string | -- | Catalog name |
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--work-group` | No | string | -- | Workgroup context |

**Output Schema:**
```json
{
    "TableMetadata": {
        "Name": "string",
        "CreateTime": "timestamp",
        "LastAccessTime": "timestamp",
        "TableType": "string",
        "Columns": [
            {
                "Name": "string",
                "Type": "string",
                "Comment": "string"
            }
        ],
        "PartitionKeys": [
            {
                "Name": "string",
                "Type": "string",
                "Comment": "string"
            }
        ],
        "Parameters": {"string": "string"}
    }
}
```

---

### 5.9 `list-table-metadata`

Lists tables in a database. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-table-metadata \
    --catalog-name <value> \
    --database-name <value> \
    [--expression <value>] \
    [--work-group <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-name` | **Yes** | string | -- | Catalog name |
| `--database-name` | **Yes** | string | -- | Database name |
| `--expression` | No | string | -- | Filter expression (table name prefix) |
| `--work-group` | No | string | -- | Workgroup context |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "TableMetadataList": [
        {
            "Name": "string",
            "CreateTime": "timestamp",
            "TableType": "string",
            "Columns": [],
            "PartitionKeys": [],
            "Parameters": {}
        }
    ],
    "NextToken": "string"
}
```
