# API Keys & Cache

### 7.1 `create-api-key`

Creates an API key for a GraphQL API.

**Synopsis:**
```bash
aws appsync create-api-key \
    --api-id <value> \
    [--description <value>] \
    [--expires <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--description` | No | string | None | Description of the API key |
| `--expires` | No | long | 7 days | Expiry time in seconds since epoch (rounded to nearest hour) |

**Output Schema:**
```json
{
    "apiKey": {
        "id": "string",
        "description": "string",
        "expires": long,
        "deletes": long
    }
}
```

---

### 7.2 `list-api-keys`

Lists API keys for a GraphQL API. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-api-keys \
    --api-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "apiKeys": [
        {
            "id": "string",
            "description": "string",
            "expires": long,
            "deletes": long
        }
    ],
    "nextToken": "string"
}
```

---

### 7.3 `update-api-key`

Updates an API key (description or expiry).

**Synopsis:**
```bash
aws appsync update-api-key \
    --api-id <value> \
    --id <value> \
    [--description <value>] \
    [--expires <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--id` | **Yes** | string | -- | The API key ID |
| `--description` | No | string | None | Updated description |
| `--expires` | No | long | None | Updated expiry (seconds since epoch) |

**Output Schema:**
```json
{
    "apiKey": {
        "id": "string",
        "description": "string",
        "expires": long,
        "deletes": long
    }
}
```

---

### 7.4 `delete-api-key`

Deletes an API key.

**Synopsis:**
```bash
aws appsync delete-api-key \
    --api-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--id` | **Yes** | string | -- | The API key ID to delete |

**Output:** None

---

### 7.5 `create-api-cache`

Creates caching for a GraphQL API.

**Synopsis:**
```bash
aws appsync create-api-cache \
    --api-id <value> \
    --ttl <value> \
    --api-caching-behavior <value> \
    --type <value> \
    [--transit-encryption-enabled | --no-transit-encryption-enabled] \
    [--at-rest-encryption-enabled | --no-at-rest-encryption-enabled] \
    [--health-metrics-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--ttl` | **Yes** | long | -- | TTL in seconds (1-3600) |
| `--api-caching-behavior` | **Yes** | string | -- | `FULL_REQUEST_CACHING`, `PER_RESOLVER_CACHING`, `OPERATION_LEVEL_CACHING` |
| `--type` | **Yes** | string | -- | Cache instance type: `SMALL`, `MEDIUM`, `LARGE`, `XLARGE`, `LARGE_2X`, `LARGE_4X`, `LARGE_8X`, `LARGE_12X` |
| `--transit-encryption-enabled` | No | boolean | None | Enable transit encryption (immutable after creation) |
| `--at-rest-encryption-enabled` | No | boolean | None | Enable at-rest encryption (immutable after creation) |
| `--health-metrics-config` | No | string | None | `ENABLED` or `DISABLED` |

**Output Schema:**
```json
{
    "apiCache": {
        "ttl": long,
        "apiCachingBehavior": "FULL_REQUEST_CACHING|PER_RESOLVER_CACHING|OPERATION_LEVEL_CACHING",
        "transitEncryptionEnabled": boolean,
        "atRestEncryptionEnabled": boolean,
        "type": "SMALL|MEDIUM|LARGE|XLARGE|LARGE_2X|LARGE_4X|LARGE_8X|LARGE_12X",
        "status": "AVAILABLE|CREATING|DELETING|MODIFYING|FAILED",
        "healthMetricsConfig": "ENABLED|DISABLED"
    }
}
```

---

### 7.6 `get-api-cache`

Retrieves the API cache configuration.

**Synopsis:**
```bash
aws appsync get-api-cache \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |

**Output Schema:** Same as `create-api-cache`.

---

### 7.7 `update-api-cache`

Updates the API cache configuration.

**Synopsis:**
```bash
aws appsync update-api-cache \
    --api-id <value> \
    --ttl <value> \
    --api-caching-behavior <value> \
    --type <value> \
    [--health-metrics-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--ttl` | **Yes** | long | -- | Updated TTL in seconds (1-3600) |
| `--api-caching-behavior` | **Yes** | string | -- | Updated caching behavior |
| `--type` | **Yes** | string | -- | Updated cache instance type |
| `--health-metrics-config` | No | string | None | `ENABLED` or `DISABLED` |

**Output Schema:** Same as `create-api-cache`.

---

### 7.8 `delete-api-cache`

Deletes an API cache.

**Synopsis:**
```bash
aws appsync delete-api-cache \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |

**Output:** None

---

### 7.9 `flush-api-cache`

Flushes (invalidates) all entries in an API cache.

**Synopsis:**
```bash
aws appsync flush-api-cache \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |

**Output:** None
