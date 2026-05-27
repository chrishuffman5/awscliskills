# Types & Tags

## 3.1 `create-type`

Creates a custom user-defined type (UDT) in a keyspace.

**Synopsis:**
```bash
aws keyspaces create-type \
    --keyspace-name <value> \
    --type-name <value> \
    --field-definitions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--type-name` | **Yes** | string | -- | Type name (1-48 chars, pattern: `[a-zA-Z0-9][a-zA-Z0-9_]{0,47}`) |
| `--field-definitions` | **Yes** | list | -- | List of field name and type pairs |

**Field Definitions Structure:**
```json
[
    { "name": "street", "type": "text" },
    { "name": "city", "type": "text" },
    { "name": "zip_code", "type": "text" }
]
```

**Shorthand:**
```
name=street,type=text name=city,type=text name=zip_code,type=text
```

**Output Schema:**
```json
{
    "keyspaceArn": "string",
    "typeName": "string"
}
```

---

## 3.2 `delete-type`

Deletes a custom user-defined type.

**Synopsis:**
```bash
aws keyspaces delete-type \
    --keyspace-name <value> \
    --type-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--type-name` | **Yes** | string | -- | Type name to delete |

**Output Schema:**
```json
{
    "keyspaceArn": "string",
    "typeName": "string"
}
```

---

## 3.3 `get-type`

Returns details for a custom user-defined type.

**Synopsis:**
```bash
aws keyspaces get-type \
    --keyspace-name <value> \
    --type-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--type-name` | **Yes** | string | -- | Type name |

**Output Schema:**
```json
{
    "keyspaceName": "string",
    "typeName": "string",
    "fieldDefinitions": [
        {
            "name": "string",
            "type": "string"
        }
    ],
    "lastModifiedTimestamp": "timestamp",
    "status": "ACTIVE|CREATING|DELETING|RESTORING",
    "directReferringTables": ["string"],
    "directParentTypes": ["string"],
    "maxNestingDepth": "integer",
    "keyspaceArn": "string"
}
```

---

## 3.4 `list-types`

Lists custom user-defined types in a keyspace. **Paginated operation.**

**Synopsis:**
```bash
aws keyspaces list-types \
    --keyspace-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "types": ["string"],
    "nextToken": "string"
}
```

---

## 3.5 `tag-resource`

Adds tags to a Keyspaces resource (keyspace or table).

**Synopsis:**
```bash
aws keyspaces tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `key=string,value=string ...` |

**Output Schema:**

None (HTTP 200 on success).

---

## 3.6 `untag-resource`

Removes tags from a Keyspaces resource.

**Synopsis:**
```bash
aws keyspaces untag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags to remove. Shorthand: `key=string,value=string ...` |

**Output Schema:**

None (HTTP 200 on success).

---

## 3.7 `list-tags-for-resource`

Lists tags for a Keyspaces resource. **Paginated operation.**

**Synopsis:**
```bash
aws keyspaces list-tags-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ],
    "nextToken": "string"
}
```
