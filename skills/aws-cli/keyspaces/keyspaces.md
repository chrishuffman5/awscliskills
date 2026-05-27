# Keyspaces

## 1.1 `create-keyspace`

Creates a new keyspace in Amazon Keyspaces.

**Synopsis:**
```bash
aws keyspaces create-keyspace \
    --keyspace-name <value> \
    [--tags <value>] \
    [--replication-specification <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name (1-48 chars, pattern: `[a-zA-Z0-9][a-zA-Z0-9_]{0,47}`) |
| `--tags` | No | list | None | Key-value tags (max 60) |
| `--replication-specification` | No | structure | `SINGLE_REGION` | Replication strategy and regions |

**Replication Specification Structure:**
```json
{
    "replicationStrategy": "SINGLE_REGION|MULTI_REGION",
    "regionList": ["us-east-1", "eu-west-1"]
}
```

**Shorthand:**
```
replicationStrategy=MULTI_REGION,regionList=us-east-1,eu-west-1
```

**Output Schema:**
```json
{
    "resourceArn": "string"
}
```

---

## 1.2 `delete-keyspace`

Deletes a keyspace and all tables within it.

**Synopsis:**
```bash
aws keyspaces delete-keyspace \
    --keyspace-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name to delete |

**Output Schema:**

None (HTTP 200 on success).

---

## 1.3 `get-keyspace`

Returns details for a keyspace.

**Synopsis:**
```bash
aws keyspaces get-keyspace \
    --keyspace-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |

**Output Schema:**
```json
{
    "keyspaceName": "string",
    "resourceArn": "string",
    "replicationStrategy": "SINGLE_REGION|MULTI_REGION",
    "replicationRegions": ["string"]
}
```

---

## 1.4 `list-keyspaces`

Lists all keyspaces in the account. **Paginated operation.**

**Synopsis:**
```bash
aws keyspaces list-keyspaces \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "keyspaces": [
        {
            "keyspaceName": "string",
            "resourceArn": "string",
            "replicationStrategy": "SINGLE_REGION|MULTI_REGION",
            "replicationRegions": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

## 1.5 `update-keyspace`

Updates the replication configuration of a keyspace (e.g., adding regions for multi-region).

**Synopsis:**
```bash
aws keyspaces update-keyspace \
    --keyspace-name <value> \
    --replication-specification <value> \
    [--client-side-timestamps-specification <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--keyspace-name` | **Yes** | string | -- | Keyspace name |
| `--replication-specification` | **Yes** | structure | -- | Updated replication configuration |
| `--client-side-timestamps-specification` | No | structure | None | Client-side timestamps configuration |

**Output Schema:**
```json
{
    "resourceArn": "string"
}
```
