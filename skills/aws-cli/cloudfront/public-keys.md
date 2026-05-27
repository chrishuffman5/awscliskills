# Public Keys

### 11.1 `create-public-key`

Uploads a public key to CloudFront for use with signed URLs and signed cookies.

**Synopsis:**
```bash
aws cloudfront create-public-key \
    --public-key-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--public-key-config` | **Yes** | structure | Public key configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `CallerReference` | **Yes** | string | Unique value to prevent replay |
| `Name` | **Yes** | string | Public key name |
| `EncodedKey` | **Yes** | string | PEM-encoded public key |
| `Comment` | No | string | Description |

**Output Schema:**
```json
{
    "PublicKey": {
        "Id": "string",
        "CreatedTime": "timestamp",
        "PublicKeyConfig": {
            "CallerReference": "string",
            "Name": "string",
            "EncodedKey": "string",
            "Comment": "string"
        }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 11.2 `get-public-key`

Gets a public key.

**Synopsis:**
```bash
aws cloudfront get-public-key \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Public key ID |

**Output Schema:**
```json
{
    "PublicKey": {
        "Id": "string",
        "CreatedTime": "timestamp",
        "PublicKeyConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 11.3 `get-public-key-config`

Gets the configuration for a public key.

**Synopsis:**
```bash
aws cloudfront get-public-key-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Public key ID |

**Output Schema:**
```json
{
    "PublicKeyConfig": { "..." },
    "ETag": "string"
}
```

---

### 11.4 `list-public-keys`

Lists public keys.

**Synopsis:**
```bash
aws cloudfront list-public-keys \
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
    "PublicKeyList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "Id": "string",
                "Name": "string",
                "CreatedTime": "timestamp",
                "EncodedKey": "string",
                "Comment": "string"
            }
        ]
    }
}
```

---

### 11.5 `update-public-key`

Updates a public key's configuration (name, comment only -- encoded key cannot be changed).

**Synopsis:**
```bash
aws cloudfront update-public-key \
    --id <value> \
    --public-key-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Public key ID |
| `--public-key-config` | **Yes** | structure | Updated configuration |
| `--if-match` | **Yes** | string | ETag from `get-public-key` |

**Output Schema:** Same as `get-public-key`.

---

### 11.6 `delete-public-key`

Deletes a public key. Must not be referenced by any key group.

**Synopsis:**
```bash
aws cloudfront delete-public-key \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Public key ID |
| `--if-match` | **Yes** | string | ETag from `get-public-key` |

**Output:** None.

---
