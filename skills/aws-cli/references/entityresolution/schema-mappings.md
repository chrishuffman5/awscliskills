# Schema Mappings

### 4.1 `create-schema-mapping`

Creates a schema mapping that defines how input fields map to Entity Resolution attribute types.

**Synopsis:**
```bash
aws entityresolution create-schema-mapping \
    --schema-name <value> \
    --mapped-input-fields <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-name` | **Yes** | string | -- | Schema name (1-255 chars) |
| `--mapped-input-fields` | **Yes** | list | -- | Field mappings (2-35 fields) |
| `--description` | No | string | None | Schema description (max 255 chars) |
| `--tags` | No | map | None | Tags (max 200) |

**MappedInputFields Structure:**
```json
[
    {
        "fieldName": "customer_name",
        "type": "NAME",
        "groupName": "name_group",
        "matchKey": "name",
        "subType": "string",
        "hashed": false
    }
]
```

**Supported Field Types:**
- Name: `NAME`, `NAME_FIRST`, `NAME_MIDDLE`, `NAME_LAST`
- Address: `ADDRESS`, `ADDRESS_STREET1`, `ADDRESS_STREET2`, `ADDRESS_STREET3`, `ADDRESS_CITY`, `ADDRESS_STATE`, `ADDRESS_COUNTRY`, `ADDRESS_POSTALCODE`
- Phone: `PHONE`, `PHONE_NUMBER`, `PHONE_COUNTRYCODE`
- Other: `EMAIL_ADDRESS`, `UNIQUE_ID`, `DATE`, `STRING`, `PROVIDER_ID`, `IPV4`, `IPV6`, `MAID`

**Output Schema:**
```json
{
    "schemaName": "string",
    "schemaArn": "string",
    "description": "string",
    "mappedInputFields": [
        {
            "fieldName": "string",
            "type": "string",
            "groupName": "string",
            "matchKey": "string",
            "subType": "string",
            "hashed": "boolean"
        }
    ]
}
```

---

### 4.2 `get-schema-mapping`

Gets details of a schema mapping.

**Synopsis:**
```bash
aws entityresolution get-schema-mapping \
    --schema-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-name` | **Yes** | string | -- | Name of the schema |

**Output Schema:**
```json
{
    "schemaName": "string",
    "schemaArn": "string",
    "description": "string",
    "mappedInputFields": [
        {
            "fieldName": "string",
            "type": "string",
            "groupName": "string",
            "matchKey": "string",
            "subType": "string",
            "hashed": "boolean"
        }
    ],
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "hasWorkflows": "boolean",
    "tags": {"string": "string"}
}
```

---

### 4.3 `list-schema-mappings`

Lists schema mappings. **Paginated operation.**

**Synopsis:**
```bash
aws entityresolution list-schema-mappings \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-25) |

**Output Schema:**
```json
{
    "schemaList": [
        {
            "schemaName": "string",
            "schemaArn": "string",
            "createdAt": "timestamp",
            "updatedAt": "timestamp",
            "hasWorkflows": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `update-schema-mapping`

Updates a schema mapping. Cannot update if it has active workflows.

**Synopsis:**
```bash
aws entityresolution update-schema-mapping \
    --schema-name <value> \
    --mapped-input-fields <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-name` | **Yes** | string | -- | Name of the schema |
| `--mapped-input-fields` | **Yes** | list | -- | Updated field mappings (2-35 fields) |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "schemaName": "string",
    "schemaArn": "string",
    "description": "string",
    "mappedInputFields": []
}
```

---

### 4.5 `delete-schema-mapping`

Deletes a schema mapping. Cannot delete if it has active workflows.

**Synopsis:**
```bash
aws entityresolution delete-schema-mapping \
    --schema-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-name` | **Yes** | string | -- | Name of the schema to delete |

**Output Schema:**
```json
{
    "message": "string"
}
```
