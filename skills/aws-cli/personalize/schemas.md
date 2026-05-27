# Schemas

### 3.1 `create-schema`

Creates an Amazon Personalize schema from an Avro schema definition. Schemas define the structure of datasets.

**Synopsis:**
```bash
aws personalize create-schema \
    --name <value> \
    --schema <value> \
    [--domain <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Schema name (1-63 chars) |
| `--schema` | **Yes** | string | -- | Avro schema JSON string (max 10000 chars) |
| `--domain` | No | string | None | Domain: `ECOMMERCE` or `VIDEO_ON_DEMAND` |

**Output Schema:**
```json
{
    "schemaArn": "string"
}
```

---

### 3.2 `describe-schema`

Describes a schema.

**Synopsis:**
```bash
aws personalize describe-schema \
    --schema-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-arn` | **Yes** | string | -- | ARN of the schema |

**Output Schema:**
```json
{
    "schema": {
        "name": "string",
        "schemaArn": "string",
        "schema": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "domain": "ECOMMERCE|VIDEO_ON_DEMAND"
    }
}
```

---

### 3.3 `list-schemas`

Lists all schemas in the account. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-schemas \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "schemas": [
        {
            "name": "string",
            "schemaArn": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "domain": "ECOMMERCE|VIDEO_ON_DEMAND"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `delete-schema`

Deletes a schema. Cannot delete a schema that is in use by a dataset.

**Synopsis:**
```bash
aws personalize delete-schema \
    --schema-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-arn` | **Yes** | string | -- | ARN of the schema to delete |

**Output:** None
