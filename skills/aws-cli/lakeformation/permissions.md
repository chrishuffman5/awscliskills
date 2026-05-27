# Permissions

### 1.1 `grant-permissions`

Grants permissions to a principal on a Data Catalog resource.

**Synopsis:**
```bash
aws lakeformation grant-permissions \
    --principal <value> \
    --resource <value> \
    --permissions <value> \
    [--catalog-id <value>] \
    [--permissions-with-grant-option <value>] \
    [--condition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal` | **Yes** | structure | -- | The principal receiving permissions |
| `--resource` | **Yes** | structure | -- | The resource to grant permissions on |
| `--permissions` | **Yes** | list(string) | -- | Permissions to grant (e.g., `SELECT`, `ALTER`, `ALL`) |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--permissions-with-grant-option` | No | list(string) | None | Permissions the principal can delegate |
| `--condition` | No | structure | None | Cedar Policy Language condition expression |

**Principal Structure:**
```json
{
    "DataLakePrincipalIdentifier": "arn:aws:iam::123456789012:role/MyRole"
}
```

**Resource Structure (one of):**
```json
{
    "Database": {
        "CatalogId": "string",
        "Name": "string"
    }
}
```
```json
{
    "Table": {
        "CatalogId": "string",
        "DatabaseName": "string",
        "Name": "string",
        "TableWildcard": {}
    }
}
```
```json
{
    "TableWithColumns": {
        "CatalogId": "string",
        "DatabaseName": "string",
        "Name": "string",
        "ColumnNames": ["string"],
        "ColumnWildcard": {
            "ExcludedColumnNames": ["string"]
        }
    }
}
```
```json
{
    "DataLocation": {
        "CatalogId": "string",
        "ResourceArn": "arn:aws:s3:::bucket-name"
    }
}
```
```json
{
    "LFTagPolicy": {
        "CatalogId": "string",
        "ResourceType": "DATABASE|TABLE",
        "Expression": [
            {
                "TagKey": "string",
                "TagValues": ["string"]
            }
        ]
    }
}
```

**Output:** None

---

### 1.2 `revoke-permissions`

Revokes permissions from a principal on a Data Catalog resource.

**Synopsis:**
```bash
aws lakeformation revoke-permissions \
    --principal <value> \
    --resource <value> \
    --permissions <value> \
    [--catalog-id <value>] \
    [--permissions-with-grant-option <value>] \
    [--condition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal` | **Yes** | structure | -- | The principal to revoke permissions from |
| `--resource` | **Yes** | structure | -- | The resource to revoke permissions on |
| `--permissions` | **Yes** | list(string) | -- | Permissions to revoke |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--permissions-with-grant-option` | No | list(string) | None | Grant options to revoke |
| `--condition` | No | structure | None | Cedar Policy Language condition |

**Output:** None

---

### 1.3 `batch-grant-permissions`

Grants permissions in batch to multiple principal-resource pairs.

**Synopsis:**
```bash
aws lakeformation batch-grant-permissions \
    --entries <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entries` | **Yes** | list | -- | List of permission entries. Each entry has `Id`, `Principal`, `Resource`, `Permissions`, `PermissionsWithGrantOption` |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Entry Structure:**
```json
[
    {
        "Id": "string",
        "Principal": {
            "DataLakePrincipalIdentifier": "string"
        },
        "Resource": {},
        "Permissions": ["SELECT"],
        "PermissionsWithGrantOption": []
    }
]
```

**Output Schema:**
```json
{
    "Failures": [
        {
            "RequestEntry": {},
            "Error": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 1.4 `batch-revoke-permissions`

Revokes permissions in batch from multiple principal-resource pairs.

**Synopsis:**
```bash
aws lakeformation batch-revoke-permissions \
    --entries <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `batch-grant-permissions`.

**Output Schema:** Same as `batch-grant-permissions` output (returns `Failures` array).

---

### 1.5 `list-permissions`

Lists permissions granted on resources. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation list-permissions \
    [--catalog-id <value>] \
    [--principal <value>] \
    [--resource-type <value>] \
    [--resource <value>] \
    [--include-related <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--principal` | No | structure | None | Filter by principal |
| `--resource-type` | No | string | None | Filter by resource type: `CATALOG`, `DATABASE`, `TABLE`, `DATA_LOCATION`, `LF_TAG`, `LF_TAG_POLICY`, `LF_TAG_POLICY_DATABASE`, `LF_TAG_POLICY_TABLE` |
| `--resource` | No | structure | None | Filter by specific resource |
| `--include-related` | No | string | None | Include related permissions |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PrincipalResourcePermissions": [
        {
            "Principal": {
                "DataLakePrincipalIdentifier": "string"
            },
            "Resource": {},
            "Permissions": ["string"],
            "PermissionsWithGrantOption": ["string"],
            "AdditionalDetails": {
                "ResourceShare": ["string"]
            },
            "LastUpdated": "timestamp",
            "LastUpdatedBy": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `get-effective-permissions-for-path`

Returns the effective Lake Formation permissions for an S3 path. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation get-effective-permissions-for-path \
    --resource-arn <value> \
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
| `--resource-arn` | **Yes** | string | -- | S3 path ARN to check permissions |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "Permissions": [
        {
            "Principal": {
                "DataLakePrincipalIdentifier": "string"
            },
            "Resource": {},
            "Permissions": ["string"],
            "PermissionsWithGrantOption": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 1.7 `get-data-lake-settings`

Retrieves the data lake settings for the account (administrators, default permissions, cross-account settings).

**Synopsis:**
```bash
aws lakeformation get-data-lake-settings \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output Schema:**
```json
{
    "DataLakeSettings": {
        "DataLakeAdmins": [
            {
                "DataLakePrincipalIdentifier": "string"
            }
        ],
        "ReadOnlyAdmins": [
            {
                "DataLakePrincipalIdentifier": "string"
            }
        ],
        "CreateDatabaseDefaultPermissions": [
            {
                "Principal": {
                    "DataLakePrincipalIdentifier": "string"
                },
                "Permissions": ["string"]
            }
        ],
        "CreateTableDefaultPermissions": [
            {
                "Principal": {
                    "DataLakePrincipalIdentifier": "string"
                },
                "Permissions": ["string"]
            }
        ],
        "Parameters": {
            "CROSS_ACCOUNT_VERSION": "1|2|3|4|5"
        },
        "TrustedResourceOwners": ["string"],
        "AllowExternalDataFiltering": "boolean",
        "AllowFullTableExternalDataAccess": "boolean",
        "ExternalDataFilteringAllowList": [
            {
                "DataLakePrincipalIdentifier": "string"
            }
        ],
        "AuthorizedSessionTagValueList": ["string"]
    }
}
```

---

### 1.8 `put-data-lake-settings`

Sets the data lake settings for the account.

**Synopsis:**
```bash
aws lakeformation put-data-lake-settings \
    --data-lake-settings <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-lake-settings` | **Yes** | structure | -- | Data lake settings (same structure as get-data-lake-settings output) |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output:** None

---

### 1.9 `get-data-lake-principal`

Returns the identity of the calling principal.

**Synopsis:**
```bash
aws lakeformation get-data-lake-principal \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "Identity": "string"
}
```
