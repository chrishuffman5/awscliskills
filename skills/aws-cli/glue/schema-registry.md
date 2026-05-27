# Schema Registry

### 14.1 `create-registry`

Creates a schema registry.

**Synopsis:**
```bash
aws glue create-registry \
    --registry-name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |
| `--description` | No | string | -- | Description |
| `--tags` | No | map | -- | Tags as JSON |

**Output Schema:**
```json
{
    "RegistryArn": "string",
    "RegistryName": "string",
    "Description": "string",
    "Tags": {}
}
```

---

### 14.2 `delete-registry`

Deletes a schema registry.

**Synopsis:**
```bash
aws glue delete-registry \
    --registry-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-id` | **Yes** | structure | -- | Registry identifier. Shorthand: `RegistryName=string` or `RegistryArn=string` |

**Output Schema:**
```json
{
    "RegistryName": "string",
    "RegistryArn": "string",
    "Status": "AVAILABLE|DELETING"
}
```

---

### 14.3 `get-registry`

Retrieves a registry.

**Synopsis:**
```bash
aws glue get-registry \
    --registry-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-id` | **Yes** | structure | -- | Registry identifier. Shorthand: `RegistryName=string` or `RegistryArn=string` |

**Output Schema:**
```json
{
    "RegistryName": "string",
    "RegistryArn": "string",
    "Description": "string",
    "Status": "AVAILABLE|DELETING",
    "CreatedTime": "string",
    "UpdatedTime": "string"
}
```

---

### 14.4 `update-registry`

Updates a registry.

**Synopsis:**
```bash
aws glue update-registry \
    --registry-id <value> \
    --description <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-id` | **Yes** | structure | -- | Registry identifier |
| `--description` | **Yes** | string | -- | Updated description |

**Output Schema:**
```json
{
    "RegistryName": "string",
    "RegistryArn": "string"
}
```

---

### 14.5 `list-registries`

Lists all registries. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-registries \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Registries": [
        {
            "RegistryName": "string",
            "RegistryArn": "string",
            "Description": "string",
            "Status": "AVAILABLE|DELETING",
            "CreatedTime": "string",
            "UpdatedTime": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 14.6 `create-schema`

Creates a schema in a registry.

**Synopsis:**
```bash
aws glue create-schema \
    --schema-name <value> \
    --data-format <value> \
    [--registry-id <value>] \
    [--compatibility <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--schema-definition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-name` | **Yes** | string | -- | Schema name |
| `--data-format` | **Yes** | string | -- | `AVRO`, `JSON`, `PROTOBUF` |
| `--registry-id` | No | structure | -- | Registry identifier. Shorthand: `RegistryName=string` |
| `--compatibility` | No | string | NONE | `NONE`, `DISABLED`, `BACKWARD`, `BACKWARD_ALL`, `FORWARD`, `FORWARD_ALL`, `FULL`, `FULL_ALL` |
| `--description` | No | string | -- | Description |
| `--tags` | No | map | -- | Tags as JSON |
| `--schema-definition` | No | string | -- | Schema definition string or `file://path` |

**Output Schema:**
```json
{
    "RegistryName": "string",
    "RegistryArn": "string",
    "SchemaName": "string",
    "SchemaArn": "string",
    "Description": "string",
    "DataFormat": "AVRO|JSON|PROTOBUF",
    "Compatibility": "string",
    "SchemaCheckpoint": "long",
    "LatestSchemaVersion": "long",
    "NextSchemaVersion": "long",
    "SchemaStatus": "AVAILABLE|PENDING|DELETING",
    "Tags": {},
    "SchemaVersionId": "string",
    "SchemaVersionStatus": "AVAILABLE|PENDING|FAILURE|DELETING"
}
```

---

### 14.7 `delete-schema`

Deletes a schema.

**Synopsis:**
```bash
aws glue delete-schema \
    --schema-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | **Yes** | structure | -- | Schema identifier. Shorthand: `SchemaName=string,RegistryName=string` or `SchemaArn=string` |

**Output Schema:**
```json
{
    "SchemaArn": "string",
    "SchemaName": "string",
    "Status": "AVAILABLE|PENDING|DELETING"
}
```

---

### 14.8 `get-schema`

Retrieves a schema.

**Synopsis:**
```bash
aws glue get-schema \
    --schema-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | **Yes** | structure | -- | Schema identifier |

**Output Schema:**
```json
{
    "RegistryName": "string",
    "RegistryArn": "string",
    "SchemaName": "string",
    "SchemaArn": "string",
    "Description": "string",
    "DataFormat": "AVRO|JSON|PROTOBUF",
    "Compatibility": "string",
    "SchemaCheckpoint": "long",
    "LatestSchemaVersion": "long",
    "NextSchemaVersion": "long",
    "SchemaStatus": "AVAILABLE|PENDING|DELETING",
    "CreatedTime": "string",
    "UpdatedTime": "string"
}
```

---

### 14.9 `get-schema-version`

Retrieves a schema version.

**Synopsis:**
```bash
aws glue get-schema-version \
    [--schema-id <value>] \
    [--schema-version-id <value>] \
    [--schema-version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | No | structure | -- | Schema identifier |
| `--schema-version-id` | No | string | -- | Specific version ID (UUID) |
| `--schema-version-number` | No | structure | -- | Version number. Shorthand: `LatestVersion=boolean,VersionNumber=long` |

**Output Schema:**
```json
{
    "SchemaVersionId": "string",
    "SchemaDefinition": "string",
    "DataFormat": "AVRO|JSON|PROTOBUF",
    "SchemaArn": "string",
    "VersionNumber": "long",
    "Status": "AVAILABLE|PENDING|FAILURE|DELETING",
    "CreatedTime": "string"
}
```

---

### 14.10 `update-schema`

Updates a schema (compatibility or checkpoint).

**Synopsis:**
```bash
aws glue update-schema \
    --schema-id <value> \
    [--schema-version-number <value>] \
    [--compatibility <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | **Yes** | structure | -- | Schema identifier |
| `--schema-version-number` | No | structure | -- | Version to set as checkpoint |
| `--compatibility` | No | string | -- | Updated compatibility mode |
| `--description` | No | string | -- | Updated description |

**Output Schema:**
```json
{
    "SchemaArn": "string",
    "SchemaName": "string",
    "RegistryName": "string"
}
```

---

### 14.11 `list-schemas`

Lists schemas. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-schemas \
    [--registry-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-id` | No | structure | -- | Filter by registry |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Schemas": [
        {
            "RegistryName": "string",
            "SchemaName": "string",
            "SchemaArn": "string",
            "Description": "string",
            "SchemaStatus": "string",
            "CreatedTime": "string",
            "UpdatedTime": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 14.12 `list-schema-versions`

Lists schema versions. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-schema-versions \
    --schema-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | **Yes** | structure | -- | Schema identifier |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Schemas": [
        {
            "SchemaArn": "string",
            "SchemaVersionId": "string",
            "VersionNumber": "long",
            "Status": "string",
            "CreatedTime": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 14.13 `register-schema-version`

Registers a new version of a schema.

**Synopsis:**
```bash
aws glue register-schema-version \
    --schema-id <value> \
    --schema-definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | **Yes** | structure | -- | Schema identifier |
| `--schema-definition` | **Yes** | string | -- | Schema definition string |

**Output Schema:**
```json
{
    "SchemaVersionId": "string",
    "VersionNumber": "long",
    "Status": "AVAILABLE|PENDING|FAILURE|DELETING"
}
```

---

### 14.14 `get-schema-by-definition`

Retrieves a schema version by its definition.

**Synopsis:**
```bash
aws glue get-schema-by-definition \
    --schema-id <value> \
    --schema-definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | **Yes** | structure | -- | Schema identifier |
| `--schema-definition` | **Yes** | string | -- | Schema definition to look up |

**Output Schema:**
```json
{
    "SchemaVersionId": "string",
    "SchemaArn": "string",
    "DataFormat": "AVRO|JSON|PROTOBUF",
    "Status": "string",
    "CreatedTime": "string"
}
```

---

### 14.15 `get-schema-versions-diff`

Returns the diff between two schema versions.

**Synopsis:**
```bash
aws glue get-schema-versions-diff \
    --schema-id <value> \
    --first-schema-version-number <value> \
    --second-schema-version-number <value> \
    --schema-diff-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | **Yes** | structure | -- | Schema identifier |
| `--first-schema-version-number` | **Yes** | structure | -- | First version. Shorthand: `LatestVersion=boolean,VersionNumber=long` |
| `--second-schema-version-number` | **Yes** | structure | -- | Second version |
| `--schema-diff-type` | **Yes** | string | -- | `SYNTAX_DIFF` |

**Output Schema:**
```json
{
    "Diff": "string"
}
```

---

### 14.16 `put-schema-version-metadata`

Adds metadata to a schema version.

**Synopsis:**
```bash
aws glue put-schema-version-metadata \
    --metadata-key-value <value> \
    [--schema-id <value>] \
    [--schema-version-number <value>] \
    [--schema-version-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metadata-key-value` | **Yes** | structure | -- | Metadata. Shorthand: `MetadataKey=string,MetadataValue=string` |
| `--schema-id` | No | structure | -- | Schema identifier |
| `--schema-version-number` | No | structure | -- | Version number |
| `--schema-version-id` | No | string | -- | Version ID |

**Output Schema:**
```json
{
    "SchemaArn": "string",
    "SchemaName": "string",
    "RegistryName": "string",
    "LatestVersion": "boolean",
    "VersionNumber": "long",
    "SchemaVersionId": "string",
    "MetadataKey": "string",
    "MetadataValue": "string"
}
```

---

### 14.17 `remove-schema-version-metadata`

Removes metadata from a schema version.

**Synopsis:**
```bash
aws glue remove-schema-version-metadata \
    --metadata-key-value <value> \
    [--schema-id <value>] \
    [--schema-version-number <value>] \
    [--schema-version-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metadata-key-value` | **Yes** | structure | -- | Metadata to remove. Shorthand: `MetadataKey=string,MetadataValue=string` |
| `--schema-id` | No | structure | -- | Schema identifier |
| `--schema-version-number` | No | structure | -- | Version number |
| `--schema-version-id` | No | string | -- | Version ID |

**Output Schema:**
```json
{
    "SchemaArn": "string",
    "SchemaName": "string",
    "RegistryName": "string",
    "LatestVersion": "boolean",
    "VersionNumber": "long",
    "SchemaVersionId": "string",
    "MetadataKey": "string",
    "MetadataValue": "string"
}
```

---

### 14.18 `query-schema-version-metadata`

Queries metadata for schema versions.

**Synopsis:**
```bash
aws glue query-schema-version-metadata \
    [--schema-id <value>] \
    [--schema-version-number <value>] \
    [--schema-version-id <value>] \
    [--metadata-list <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | No | structure | -- | Schema identifier |
| `--schema-version-number` | No | structure | -- | Version number |
| `--schema-version-id` | No | string | -- | Version ID |
| `--metadata-list` | No | list | -- | Metadata key-value pairs to filter |
| `--max-results` | No | integer | -- | Maximum results |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "MetadataInfoMap": {
        "key": {
            "MetadataValue": "string",
            "CreatedTime": "string",
            "OtherMetadataValueList": []
        }
    },
    "SchemaVersionId": "string",
    "NextToken": "string"
}
```

---

### 14.19 `delete-schema-versions`

Deletes one or more schema versions.

**Synopsis:**
```bash
aws glue delete-schema-versions \
    --schema-id <value> \
    --versions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schema-id` | **Yes** | structure | -- | Schema identifier |
| `--versions` | **Yes** | string | -- | Version range (e.g., `1-5` or `1,3,5`) |

**Output Schema:**
```json
{
    "SchemaVersionErrors": [
        {
            "VersionNumber": "long",
            "ErrorDetails": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 14.20 `check-schema-version-validity`

Validates a schema version against its compatibility rules.

**Synopsis:**
```bash
aws glue check-schema-version-validity \
    --data-format <value> \
    --schema-definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-format` | **Yes** | string | -- | `AVRO`, `JSON`, `PROTOBUF` |
| `--schema-definition` | **Yes** | string | -- | Schema definition to validate |

**Output Schema:**
```json
{
    "Valid": "boolean",
    "Error": "string"
}
```
