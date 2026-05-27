# Databases

### 3.1 `create-database`

Creates a new database in the Data Catalog.

**Synopsis:**
```bash
aws glue create-database \
    --database-input <value> \
    [--catalog-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-input` | **Yes** | structure | -- | Database definition. Shorthand: `Name=string,Description=string,LocationUri=string,Parameters={key=value}` |
| `--catalog-id` | No | string | -- | Catalog ID (defaults to caller account) |
| `--tags` | No | map | -- | Tags as JSON |

No output on success.

---

### 3.2 `delete-database`

Deletes a database and all tables within it.

**Synopsis:**
```bash
aws glue delete-database \
    --name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Database name |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 3.3 `get-database`

Retrieves a database definition.

**Synopsis:**
```bash
aws glue get-database \
    --name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Database name |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Database": {
        "Name": "string",
        "Description": "string",
        "LocationUri": "string",
        "Parameters": {},
        "CreateTime": "timestamp",
        "CreateTableDefaultPermissions": [
            {
                "Principal": {
                    "DataLakePrincipalIdentifier": "string"
                },
                "Permissions": ["ALL|SELECT|ALTER|DROP|DELETE|INSERT|CREATE_DATABASE|CREATE_TABLE|DATA_LOCATION_ACCESS"]
            }
        ],
        "TargetDatabase": {
            "CatalogId": "string",
            "DatabaseName": "string",
            "Region": "string"
        },
        "CatalogId": "string",
        "FederatedDatabase": {
            "Identifier": "string",
            "ConnectionName": "string"
        }
    }
}
```

---

### 3.4 `get-databases`

Retrieves all databases in the Data Catalog. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-databases \
    [--catalog-id <value>] \
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
| `--resource-share-type` | No | string | -- | `FOREIGN`, `ALL`, `FEDERATED` |
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
            "LocationUri": "string",
            "Parameters": {},
            "CreateTime": "timestamp",
            "CatalogId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-database`

Updates a database definition.

**Synopsis:**
```bash
aws glue update-database \
    --name <value> \
    --database-input <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Database name |
| `--database-input` | **Yes** | structure | -- | Updated database definition |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.
