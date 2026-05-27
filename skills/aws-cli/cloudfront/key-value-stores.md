# Key Value Stores

### 13.1 `create-key-value-store`

Creates a key value store for use with CloudFront Functions.

**Synopsis:**
```bash
aws cloudfront create-key-value-store \
    --name <value> \
    [--comment <value>] \
    [--import-source <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | **Yes** | string | Key value store name |
| `--comment` | No | string | Description |
| `--import-source` | No | structure | S3 source for initial data. `SourceType`: `S3`, `SourceARN`: S3 object ARN |

**Output Schema:**
```json
{
    "KeyValueStore": {
        "Name": "string",
        "Id": "string",
        "Comment": "string",
        "ARN": "string",
        "Status": "string",
        "LastModifiedTime": "timestamp"
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 13.2 `describe-key-value-store`

Gets details about a key value store.

**Synopsis:**
```bash
aws cloudfront describe-key-value-store \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | **Yes** | string | Key value store name |

**Output Schema:**
```json
{
    "KeyValueStore": {
        "Name": "string",
        "Id": "string",
        "Comment": "string",
        "ARN": "string",
        "Status": "string",
        "LastModifiedTime": "timestamp"
    },
    "ETag": "string"
}
```

---

### 13.3 `list-key-value-stores`

Lists key value stores.

**Synopsis:**
```bash
aws cloudfront list-key-value-stores \
    [--marker <value>] \
    [--max-items <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker |
| `--max-items` | No | string | None | Maximum items to return |
| `--status` | No | string | None | Filter by status |

**Output Schema:**
```json
{
    "KeyValueStoreList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "Name": "string",
                "Id": "string",
                "Comment": "string",
                "ARN": "string",
                "Status": "string",
                "LastModifiedTime": "timestamp"
            }
        ]
    }
}
```

---

### 13.4 `update-key-value-store`

Updates a key value store's comment.

**Synopsis:**
```bash
aws cloudfront update-key-value-store \
    --name <value> \
    --comment <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | **Yes** | string | Key value store name |
| `--comment` | **Yes** | string | Updated description |
| `--if-match` | **Yes** | string | ETag from `describe-key-value-store` |

**Output Schema:** Same as `describe-key-value-store`.

---

### 13.5 `delete-key-value-store`

Deletes a key value store. Must not be associated with any function.

**Synopsis:**
```bash
aws cloudfront delete-key-value-store \
    --name <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | **Yes** | string | Key value store name |
| `--if-match` | **Yes** | string | ETag from `describe-key-value-store` |

**Output:** None.

---
