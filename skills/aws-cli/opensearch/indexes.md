# Indexes

### 7.1 `create-index`

Creates an index on an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch create-index \
    --domain-name <value> \
    --index-name <value> \
    [--number-of-shards <value>] \
    [--number-of-replicas <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--index-name` | **Yes** | string | -- | Index name |
| `--number-of-shards` | No | integer | -- | Number of primary shards |
| `--number-of-replicas` | No | integer | -- | Number of replica shards |

**Output Schema:**
```json
{
    "Index": {
        "IndexName": "string",
        "NumberOfShards": "integer",
        "NumberOfReplicas": "integer",
        "Status": "CREATING|ACTIVE|DELETING|FAILED"
    }
}
```

---

### 7.2 `delete-index`

Deletes an index on an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch delete-index \
    --domain-name <value> \
    --index-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--index-name` | **Yes** | string | -- | Index name |

**Output Schema:**
```json
{
    "Index": {
        "IndexName": "string",
        "Status": "DELETING"
    }
}
```

---

### 7.3 `get-index`

Returns details about an index on an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch get-index \
    --domain-name <value> \
    --index-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--index-name` | **Yes** | string | -- | Index name |

**Output Schema:**
```json
{
    "Index": {
        "IndexName": "string",
        "NumberOfShards": "integer",
        "NumberOfReplicas": "integer",
        "Status": "CREATING|ACTIVE|DELETING|FAILED"
    }
}
```

---

### 7.4 `update-index`

Updates an index on an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch update-index \
    --domain-name <value> \
    --index-name <value> \
    [--number-of-replicas <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--index-name` | **Yes** | string | -- | Index name |
| `--number-of-replicas` | No | integer | -- | Updated replica count |

**Output Schema:**
```json
{
    "Index": {
        "IndexName": "string",
        "NumberOfShards": "integer",
        "NumberOfReplicas": "integer",
        "Status": "string"
    }
}
```
