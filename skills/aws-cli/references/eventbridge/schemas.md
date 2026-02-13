# Schemas

Commands use the `aws schemas` service namespace. EventBridge Schema Registry allows you to discover, create, and manage OpenAPI and JSONSchema schemas for events.

## Schemas

### 8.1 `create-schema`

Creates a schema in a registry.

**Synopsis:**
```bash
aws schemas create-schema \
    --registry-name <value> \
    --schema-name <value> \
    --type <value> \
    --content <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |
| `--schema-name` | **Yes** | string | -- | Schema name |
| `--type` | **Yes** | string | -- | Schema type: `OpenApi3` or `JSONSchemaDraft4` |
| `--content` | **Yes** | string | -- | Schema content (JSON or YAML string) |
| `--description` | No | string | None | Schema description |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "Description": "string",
    "LastModified": "timestamp",
    "SchemaArn": "string",
    "SchemaName": "string",
    "SchemaVersion": "string",
    "Tags": {
        "key": "string"
    },
    "Type": "string",
    "VersionCreatedDate": "timestamp"
}
```

---

### 8.2 `delete-schema`

Deletes a schema and all its versions.

**Synopsis:**
```bash
aws schemas delete-schema \
    --registry-name <value> \
    --schema-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |
| `--schema-name` | **Yes** | string | -- | Schema name to delete |

**Output Schema:**
```json
{}
```

---

### 8.3 `describe-schema`

Retrieves details about a schema, including its content.

**Synopsis:**
```bash
aws schemas describe-schema \
    --registry-name <value> \
    --schema-name <value> \
    [--schema-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |
| `--schema-name` | **Yes** | string | -- | Schema name |
| `--schema-version` | No | string | latest | Specific schema version |

**Output Schema:**
```json
{
    "Content": "string",
    "Description": "string",
    "LastModified": "timestamp",
    "SchemaArn": "string",
    "SchemaName": "string",
    "SchemaVersion": "string",
    "Tags": {
        "key": "string"
    },
    "Type": "string",
    "VersionCreatedDate": "timestamp"
}
```

---

### 8.4 `list-schemas`

Lists schemas in a registry. **Paginated operation.**

**Synopsis:**
```bash
aws schemas list-schemas \
    --registry-name <value> \
    [--schema-name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |
| `--schema-name-prefix` | No | string | None | Filter by schema name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Schemas": [
        {
            "LastModified": "timestamp",
            "SchemaArn": "string",
            "SchemaName": "string",
            "Tags": {
                "key": "string"
            },
            "VersionCount": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-schema`

Updates a schema. Creates a new version if the content changes.

**Synopsis:**
```bash
aws schemas update-schema \
    --registry-name <value> \
    --schema-name <value> \
    [--type <value>] \
    [--content <value>] \
    [--description <value>] \
    [--client-token-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |
| `--schema-name` | **Yes** | string | -- | Schema name |
| `--type` | No | string | None | Updated type: `OpenApi3` or `JSONSchemaDraft4` |
| `--content` | No | string | None | Updated schema content |
| `--description` | No | string | None | Updated description |
| `--client-token-id` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "Description": "string",
    "LastModified": "timestamp",
    "SchemaArn": "string",
    "SchemaName": "string",
    "SchemaVersion": "string",
    "Tags": {},
    "Type": "string",
    "VersionCreatedDate": "timestamp"
}
```

---

### 8.6 `search-schemas`

Search schemas by keyword across all registries or within a specific registry. **Paginated operation.**

**Synopsis:**
```bash
aws schemas search-schemas \
    --registry-name <value> \
    --keywords <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name to search |
| `--keywords` | **Yes** | string | -- | Search keywords |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Schemas": [
        {
            "RegistryName": "string",
            "SchemaArn": "string",
            "SchemaName": "string",
            "SchemaVersions": [
                {
                    "CreatedDate": "timestamp",
                    "SchemaVersion": "string",
                    "Type": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 8.7 `export-schema`

Exports a schema in a specified format.

**Synopsis:**
```bash
aws schemas export-schema \
    --registry-name <value> \
    --schema-name <value> \
    --type <value> \
    [--schema-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |
| `--schema-name` | **Yes** | string | -- | Schema name |
| `--type` | **Yes** | string | -- | Export type: `OpenApi3` or `JSONSchemaDraft4` |
| `--schema-version` | No | string | latest | Specific version to export |

**Output Schema:**
```json
{
    "Content": "string",
    "SchemaArn": "string",
    "SchemaName": "string",
    "SchemaVersion": "string",
    "Type": "string"
}
```

---

## Registries

### 8.8 `create-registry`

Creates a schema registry.

**Synopsis:**
```bash
aws schemas create-registry \
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
| `--description` | No | string | None | Registry description |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "Description": "string",
    "RegistryArn": "string",
    "RegistryName": "string",
    "Tags": {}
}
```

---

### 8.9 `delete-registry`

Deletes a schema registry.

**Synopsis:**
```bash
aws schemas delete-registry \
    --registry-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name to delete |

**Output Schema:**
```json
{}
```

---

### 8.10 `describe-registry`

Retrieves details about a registry.

**Synopsis:**
```bash
aws schemas describe-registry \
    --registry-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |

**Output Schema:**
```json
{
    "Description": "string",
    "RegistryArn": "string",
    "RegistryName": "string",
    "Tags": {}
}
```

---

### 8.11 `list-registries`

Lists all schema registries. **Paginated operation.**

**Synopsis:**
```bash
aws schemas list-registries \
    [--registry-name-prefix <value>] \
    [--scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name-prefix` | No | string | None | Filter by registry name prefix |
| `--scope` | No | string | None | Filter by scope: `LOCAL` or `AWS` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Registries": [
        {
            "RegistryArn": "string",
            "RegistryName": "string",
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 8.12 `update-registry`

Updates a schema registry description.

**Synopsis:**
```bash
aws schemas update-registry \
    --registry-name <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-name` | **Yes** | string | -- | Registry name |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "Description": "string",
    "RegistryArn": "string",
    "RegistryName": "string",
    "Tags": {}
}
```

---

## Discoverers

### 8.13 `create-discoverer`

Creates a discoverer that automatically discovers schemas from events on an event bus.

**Synopsis:**
```bash
aws schemas create-discoverer \
    --source-arn <value> \
    [--description <value>] \
    [--cross-account | --no-cross-account] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-arn` | **Yes** | string | -- | ARN of the event bus to discover schemas from |
| `--description` | No | string | None | Discoverer description |
| `--cross-account` | No | boolean | false | Enable cross-account schema discovery |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "Description": "string",
    "DiscovererArn": "string",
    "DiscovererId": "string",
    "SourceArn": "string",
    "State": "STARTED|STOPPED",
    "CrossAccount": true|false,
    "Tags": {}
}
```

---

### 8.14 `delete-discoverer`

Deletes a discoverer.

**Synopsis:**
```bash
aws schemas delete-discoverer \
    --discoverer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--discoverer-id` | **Yes** | string | -- | Discoverer ID to delete |

**Output Schema:**
```json
{}
```

---

### 8.15 `describe-discoverer`

Retrieves details about a discoverer.

**Synopsis:**
```bash
aws schemas describe-discoverer \
    --discoverer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--discoverer-id` | **Yes** | string | -- | Discoverer ID |

**Output Schema:**
```json
{
    "Description": "string",
    "DiscovererArn": "string",
    "DiscovererId": "string",
    "SourceArn": "string",
    "State": "STARTED|STOPPED",
    "CrossAccount": true|false,
    "Tags": {}
}
```

---

### 8.16 `list-discoverers`

Lists all discoverers. **Paginated operation.**

**Synopsis:**
```bash
aws schemas list-discoverers \
    [--discoverer-id-prefix <value>] \
    [--source-arn-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--discoverer-id-prefix` | No | string | None | Filter by discoverer ID prefix |
| `--source-arn-prefix` | No | string | None | Filter by source ARN prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Discoverers": [
        {
            "DiscovererArn": "string",
            "DiscovererId": "string",
            "SourceArn": "string",
            "State": "STARTED|STOPPED",
            "CrossAccount": true|false,
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 8.17 `start-discoverer`

Starts a schema discoverer. Once started, the discoverer automatically detects schemas from events.

**Synopsis:**
```bash
aws schemas start-discoverer \
    --discoverer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--discoverer-id` | **Yes** | string | -- | Discoverer ID to start |

**Output Schema:**
```json
{
    "DiscovererId": "string",
    "State": "STARTED"
}
```

---

### 8.18 `stop-discoverer`

Stops a schema discoverer.

**Synopsis:**
```bash
aws schemas stop-discoverer \
    --discoverer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--discoverer-id` | **Yes** | string | -- | Discoverer ID to stop |

**Output Schema:**
```json
{
    "DiscovererId": "string",
    "State": "STOPPED"
}
```
