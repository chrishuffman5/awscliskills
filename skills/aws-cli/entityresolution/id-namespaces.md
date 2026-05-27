# ID Namespaces

### 3.1 `create-id-namespace`

Creates an ID namespace that represents a collection of identifiers used for ID mapping workflows.

**Synopsis:**
```bash
aws entityresolution create-id-namespace \
    --id-namespace-name <value> \
    --type <value> \
    [--description <value>] \
    [--input-source-config <value>] \
    [--id-mapping-workflow-properties <value>] \
    [--role-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id-namespace-name` | **Yes** | string | -- | Namespace name (1-255 chars) |
| `--type` | **Yes** | string | -- | `SOURCE` or `TARGET` |
| `--description` | No | string | None | Namespace description (max 255 chars) |
| `--input-source-config` | No | list | None | Input sources (max 20) |
| `--id-mapping-workflow-properties` | No | list | None | ID mapping properties (max 1) |
| `--role-arn` | No | string | None | IAM role ARN |
| `--tags` | No | map | None | Tags (max 200) |

**InputSourceConfig:**
```json
[
    {
        "inputSourceARN": "arn:aws:glue:...:table/db/table",
        "schemaName": "my-schema"
    }
]
```

**IdMappingWorkflowProperties:**
```json
[
    {
        "idMappingType": "PROVIDER|RULE_BASED",
        "ruleBasedProperties": {
            "rules": [{"ruleName": "string", "matchingKeys": ["string"]}],
            "ruleDefinitionTypes": ["SOURCE|TARGET"],
            "attributeMatchingModel": "ONE_TO_ONE|MANY_TO_MANY",
            "recordMatchingModels": ["ONE_SOURCE_TO_ONE_TARGET|MANY_SOURCE_TO_ONE_TARGET"]
        },
        "providerProperties": {
            "providerServiceArn": "string",
            "providerConfiguration": {}
        }
    }
]
```

**Output Schema:**
```json
{
    "idNamespaceName": "string",
    "idNamespaceArn": "string",
    "description": "string",
    "type": "SOURCE|TARGET",
    "roleArn": "string",
    "inputSourceConfig": [],
    "idMappingWorkflowProperties": [],
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "tags": {"string": "string"}
}
```

---

### 3.2 `get-id-namespace`

Gets details of an ID namespace.

**Synopsis:**
```bash
aws entityresolution get-id-namespace \
    --id-namespace-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id-namespace-name` | **Yes** | string | -- | Name of the ID namespace |

**Output Schema:**
```json
{
    "idNamespaceName": "string",
    "idNamespaceArn": "string",
    "description": "string",
    "type": "SOURCE|TARGET",
    "roleArn": "string",
    "inputSourceConfig": [
        {
            "inputSourceARN": "string",
            "schemaName": "string"
        }
    ],
    "idMappingWorkflowProperties": [],
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "tags": {"string": "string"}
}
```

---

### 3.3 `list-id-namespaces`

Lists ID namespaces. **Paginated operation.**

**Synopsis:**
```bash
aws entityresolution list-id-namespaces \
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
    "idNamespaceSummaries": [
        {
            "idNamespaceName": "string",
            "idNamespaceArn": "string",
            "description": "string",
            "type": "SOURCE|TARGET",
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `update-id-namespace`

Updates an ID namespace.

**Synopsis:**
```bash
aws entityresolution update-id-namespace \
    --id-namespace-name <value> \
    [--description <value>] \
    [--input-source-config <value>] \
    [--id-mapping-workflow-properties <value>] \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id-namespace-name` | **Yes** | string | -- | Name of the ID namespace |
| `--description` | No | string | None | Updated description |
| `--input-source-config` | No | list | None | Updated input sources |
| `--id-mapping-workflow-properties` | No | list | None | Updated mapping properties |
| `--role-arn` | No | string | None | Updated IAM role ARN |

**Output Schema:**
```json
{
    "idNamespaceName": "string",
    "idNamespaceArn": "string",
    "description": "string",
    "type": "SOURCE|TARGET",
    "roleArn": "string",
    "inputSourceConfig": [],
    "idMappingWorkflowProperties": [],
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
}
```

---

### 3.5 `delete-id-namespace`

Deletes an ID namespace.

**Synopsis:**
```bash
aws entityresolution delete-id-namespace \
    --id-namespace-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id-namespace-name` | **Yes** | string | -- | Name of the ID namespace to delete |

**Output Schema:**
```json
{
    "message": "string"
}
```
