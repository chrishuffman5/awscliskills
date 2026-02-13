# Key Groups

### 10.1 `create-key-group`

Creates a key group for CloudFront signed URLs and cookies.

**Synopsis:**
```bash
aws cloudfront create-key-group \
    --key-group-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--key-group-config` | **Yes** | structure | Key group configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | **Yes** | string | Key group name |
| `Items` | **Yes** | list(string) | List of public key IDs |
| `Comment` | No | string | Description |

**Output Schema:**
```json
{
    "KeyGroup": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "KeyGroupConfig": {
            "Name": "string",
            "Items": ["string"],
            "Comment": "string"
        }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 10.2 `get-key-group`

Gets a key group.

**Synopsis:**
```bash
aws cloudfront get-key-group \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Key group ID |

**Output Schema:**
```json
{
    "KeyGroup": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "KeyGroupConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 10.3 `get-key-group-config`

Gets the configuration for a key group.

**Synopsis:**
```bash
aws cloudfront get-key-group-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Key group ID |

**Output Schema:**
```json
{
    "KeyGroupConfig": { "..." },
    "ETag": "string"
}
```

---

### 10.4 `list-key-groups`

Lists key groups.

**Synopsis:**
```bash
aws cloudfront list-key-groups \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "KeyGroupList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "KeyGroup": {
                    "Id": "string",
                    "LastModifiedTime": "timestamp",
                    "KeyGroupConfig": { "..." }
                }
            }
        ]
    }
}
```

---

### 10.5 `update-key-group`

Updates a key group.

**Synopsis:**
```bash
aws cloudfront update-key-group \
    --id <value> \
    --key-group-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Key group ID |
| `--key-group-config` | **Yes** | structure | Updated configuration |
| `--if-match` | **Yes** | string | ETag from `get-key-group` |

**Output Schema:** Same as `get-key-group`.

---

### 10.6 `delete-key-group`

Deletes a key group. Must not be referenced by any distribution.

**Synopsis:**
```bash
aws cloudfront delete-key-group \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Key group ID |
| `--if-match` | **Yes** | string | ETag from `get-key-group` |

**Output:** None.

---
