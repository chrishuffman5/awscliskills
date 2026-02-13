# Custom Entity Types

Custom entity types define patterns for sensitive data detection in AWS Glue.

### 19.1 `create-custom-entity-type`

Creates a custom entity type for sensitive data detection.

**Synopsis:**
```bash
aws glue create-custom-entity-type \
    --name <value> \
    --regex-string <value> \
    [--context-words <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Entity type name |
| `--regex-string` | **Yes** | string | -- | Regular expression pattern |
| `--context-words` | No | list(string) | -- | Context words to improve detection accuracy |
| `--tags` | No | map | -- | Tags as JSON |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 19.2 `delete-custom-entity-type`

Deletes a custom entity type.

**Synopsis:**
```bash
aws glue delete-custom-entity-type \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Entity type name |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 19.3 `get-custom-entity-type`

Retrieves a custom entity type.

**Synopsis:**
```bash
aws glue get-custom-entity-type \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Entity type name |

**Output Schema:**
```json
{
    "Name": "string",
    "RegexString": "string",
    "ContextWords": ["string"]
}
```

---

### 19.4 `batch-get-custom-entity-types`

Retrieves multiple custom entity types.

**Synopsis:**
```bash
aws glue batch-get-custom-entity-types \
    --names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list(string) | -- | Entity type names |

**Output Schema:**
```json
{
    "CustomEntityTypes": [
        {
            "Name": "string",
            "RegexString": "string",
            "ContextWords": ["string"]
        }
    ],
    "CustomEntityTypesNotFound": ["string"]
}
```

---

### 19.5 `list-custom-entity-types`

Lists custom entity types. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-custom-entity-types \
    [--tags <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | No | map | -- | Filter by tags |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "CustomEntityTypes": [
        {
            "Name": "string",
            "RegexString": "string",
            "ContextWords": ["string"]
        }
    ],
    "NextToken": "string"
}
```
