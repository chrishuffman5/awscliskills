# Data Cells Filters

### 3.1 `create-data-cells-filter`

Creates a data cells filter for row-level and column-level security on a table.

**Synopsis:**
```bash
aws lakeformation create-data-cells-filter \
    --table-data <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-data` | **Yes** | structure | -- | Data cells filter definition including table, row filter, and column scope |

**Table Data Structure:**
```json
{
    "TableCatalogId": "string",
    "DatabaseName": "string",
    "TableName": "string",
    "Name": "string",
    "RowFilter": {
        "FilterExpression": "string",
        "AllRowsWildcard": {}
    },
    "ColumnNames": ["string"],
    "ColumnWildcard": {
        "ExcludedColumnNames": ["string"]
    },
    "VersionId": "string"
}
```

- Use `ColumnNames` to include specific columns, or `ColumnWildcard` for all columns (optionally excluding some)
- `RowFilter.FilterExpression` uses a PartiQL-compatible expression (e.g., `country='US'`)
- Use `AllRowsWildcard` instead of `FilterExpression` to include all rows

**Output:** None

---

### 3.2 `update-data-cells-filter`

Updates an existing data cells filter.

**Synopsis:**
```bash
aws lakeformation update-data-cells-filter \
    --table-data <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-data` | **Yes** | structure | -- | Updated data cells filter definition |

**Output:** None

---

### 3.3 `delete-data-cells-filter`

Deletes a data cells filter.

**Synopsis:**
```bash
aws lakeformation delete-data-cells-filter \
    [--table-catalog-id <value>] \
    [--database-name <value>] \
    [--table-name <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-catalog-id` | No | string | account ID | Catalog identifier |
| `--database-name` | No | string | None | Database name |
| `--table-name` | No | string | None | Table name |
| `--name` | No | string | None | Filter name |

**Output:** None

---

### 3.4 `get-data-cells-filter`

Returns the details of a data cells filter.

**Synopsis:**
```bash
aws lakeformation get-data-cells-filter \
    --table-catalog-id <value> \
    --database-name <value> \
    --table-name <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-catalog-id` | **Yes** | string | -- | Catalog identifier |
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--name` | **Yes** | string | -- | Filter name |

**Output Schema:**
```json
{
    "DataCellsFilter": {
        "TableCatalogId": "string",
        "DatabaseName": "string",
        "TableName": "string",
        "Name": "string",
        "RowFilter": {
            "FilterExpression": "string",
            "AllRowsWildcard": {}
        },
        "ColumnNames": ["string"],
        "ColumnWildcard": {
            "ExcludedColumnNames": ["string"]
        },
        "VersionId": "string"
    }
}
```

---

### 3.5 `list-data-cells-filter`

Lists data cells filters. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation list-data-cells-filter \
    [--table <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table` | No | structure | None | Filter by table (CatalogId, DatabaseName, Name) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "DataCellsFilters": [
        {
            "TableCatalogId": "string",
            "DatabaseName": "string",
            "TableName": "string",
            "Name": "string",
            "RowFilter": {},
            "ColumnNames": ["string"],
            "ColumnWildcard": {},
            "VersionId": "string"
        }
    ],
    "NextToken": "string"
}
```
