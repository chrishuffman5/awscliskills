# LF-Tags

### 2.1 `create-lf-tag`

Creates a new LF-Tag with the specified key and values.

**Synopsis:**
```bash
aws lakeformation create-lf-tag \
    --tag-key <value> \
    --tag-values <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tag-key` | **Yes** | string | -- | LF-Tag key name (1-128 chars) |
| `--tag-values` | **Yes** | list(string) | -- | Possible values for the tag (1-50 values, each 0-256 chars) |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output:** None

---

### 2.2 `get-lf-tag`

Returns the details of an LF-Tag.

**Synopsis:**
```bash
aws lakeformation get-lf-tag \
    --tag-key <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tag-key` | **Yes** | string | -- | LF-Tag key name |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output Schema:**
```json
{
    "CatalogId": "string",
    "TagKey": "string",
    "TagValues": ["string"]
}
```

---

### 2.3 `update-lf-tag`

Updates the allowed values of an LF-Tag. Can add new values or delete existing values.

**Synopsis:**
```bash
aws lakeformation update-lf-tag \
    --tag-key <value> \
    [--catalog-id <value>] \
    [--tag-values-to-delete <value>] \
    [--tag-values-to-add <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tag-key` | **Yes** | string | -- | LF-Tag key name |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--tag-values-to-delete` | No | list(string) | None | Values to remove from the tag |
| `--tag-values-to-add` | No | list(string) | None | Values to add to the tag |

**Output:** None

---

### 2.4 `delete-lf-tag`

Deletes an LF-Tag. All assignments of the tag to resources are also removed.

**Synopsis:**
```bash
aws lakeformation delete-lf-tag \
    --tag-key <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tag-key` | **Yes** | string | -- | LF-Tag key to delete |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output:** None

---

### 2.5 `list-lf-tags`

Lists all LF-Tags in the catalog. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation list-lf-tags \
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
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--resource-share-type` | No | string | None | `ALL`, `FOREIGN` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "LFTags": [
        {
            "CatalogId": "string",
            "TagKey": "string",
            "TagValues": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `add-lf-tags-to-resource`

Assigns one or more LF-Tags to a resource.

**Synopsis:**
```bash
aws lakeformation add-lf-tags-to-resource \
    --resource <value> \
    --lf-tags <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | structure | -- | Resource to tag (Database, Table, TableWithColumns) |
| `--lf-tags` | **Yes** | list | -- | LF-Tags to assign |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**LF-Tags Structure:**
```json
[
    {
        "CatalogId": "string",
        "TagKey": "string",
        "TagValues": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "Failures": [
        {
            "LFTag": {
                "CatalogId": "string",
                "TagKey": "string",
                "TagValues": ["string"]
            },
            "Error": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 2.7 `remove-lf-tags-from-resource`

Removes LF-Tags from a resource.

**Synopsis:**
```bash
aws lakeformation remove-lf-tags-from-resource \
    --resource <value> \
    --lf-tags <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `add-lf-tags-to-resource`.

**Output Schema:** Same as `add-lf-tags-to-resource` output.

---

### 2.8 `get-resource-lf-tags`

Returns the LF-Tags assigned to a resource.

**Synopsis:**
```bash
aws lakeformation get-resource-lf-tags \
    --resource <value> \
    [--catalog-id <value>] \
    [--show-assigned-lf-tags | --no-show-assigned-lf-tags] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | structure | -- | Resource to check |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--show-assigned-lf-tags` | No | boolean | false | Include assigned tags |

**Output Schema:**
```json
{
    "LFTagOnDatabase": [
        {
            "CatalogId": "string",
            "TagKey": "string",
            "TagValues": ["string"]
        }
    ],
    "LFTagsOnTable": [],
    "LFTagsOnColumns": [
        {
            "Name": "string",
            "LFTags": []
        }
    ]
}
```

---

### 2.9 `search-databases-by-lf-tags`

Searches databases by LF-Tag values. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation search-databases-by-lf-tags \
    --expression <value> \
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
| `--expression` | **Yes** | list | -- | LF-Tag expression to search by |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Expression Structure:**
```json
[
    {
        "TagKey": "string",
        "TagValues": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "DatabaseList": [
        {
            "Database": {
                "CatalogId": "string",
                "Name": "string"
            },
            "LFTags": [
                {
                    "CatalogId": "string",
                    "TagKey": "string",
                    "TagValues": ["string"]
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 2.10 `search-tables-by-lf-tags`

Searches tables by LF-Tag values. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation search-tables-by-lf-tags \
    --expression <value> \
    [--catalog-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `search-databases-by-lf-tags`.

**Output Schema:**
```json
{
    "TableList": [
        {
            "Table": {
                "CatalogId": "string",
                "DatabaseName": "string",
                "Name": "string"
            },
            "LFTags": []
        }
    ],
    "NextToken": "string"
}
```

---

### 2.11 `create-lf-tag-expression`

Creates a named LF-Tag expression for reuse in permissions.

**Synopsis:**
```bash
aws lakeformation create-lf-tag-expression \
    --name <value> \
    --expression <value> \
    [--catalog-id <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Expression name |
| `--expression` | **Yes** | list | -- | LF-Tag key-value pairs defining the expression |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--description` | No | string | None | Description of the expression |

**Output:** None

---

### 2.12 `get-lf-tag-expression`

Returns an LF-Tag expression.

**Synopsis:**
```bash
aws lakeformation get-lf-tag-expression \
    --name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Expression name |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output Schema:**
```json
{
    "Name": "string",
    "Description": "string",
    "CatalogId": "string",
    "Expression": [
        {
            "TagKey": "string",
            "TagValues": ["string"]
        }
    ]
}
```

---

### 2.13 `update-lf-tag-expression`

Updates an LF-Tag expression.

**Synopsis:**
```bash
aws lakeformation update-lf-tag-expression \
    --name <value> \
    --expression <value> \
    [--catalog-id <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-lf-tag-expression`.

**Output:** None

---

### 2.14 `delete-lf-tag-expression`

Deletes an LF-Tag expression.

**Synopsis:**
```bash
aws lakeformation delete-lf-tag-expression \
    --name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Expression name to delete |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output:** None

---

### 2.15 `list-lf-tag-expressions`

Lists LF-Tag expressions. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation list-lf-tag-expressions \
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
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "LFTagExpressions": [
        {
            "Name": "string",
            "Description": "string",
            "CatalogId": "string",
            "Expression": [
                {
                    "TagKey": "string",
                    "TagValues": ["string"]
                }
            ]
        }
    ],
    "NextToken": "string"
}
```
