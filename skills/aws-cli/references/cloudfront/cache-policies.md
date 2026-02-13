# Cache Policies

### 4.1 `create-cache-policy`

Creates a cache policy that controls what CloudFront includes in the cache key.

**Synopsis:**
```bash
aws cloudfront create-cache-policy \
    --cache-policy-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--cache-policy-config` | **Yes** | structure | Cache policy configuration |

**Cache Policy Config structure:**

| Field | Required | Type | Default | Description |
|-------|----------|------|---------|-------------|
| `Name` | **Yes** | string | -- | Unique name for the cache policy |
| `MinTTL` | **Yes** | long | -- | Minimum TTL in seconds |
| `ParametersInCacheKeyAndForwardedToOrigin` | **Yes** | structure | -- | Cache key parameters |
| `Comment` | No | string | None | Description (max 128 chars) |
| `DefaultTTL` | No | long | 86400 | Default TTL in seconds |
| `MaxTTL` | No | long | 31536000 | Maximum TTL in seconds |

**ParametersInCacheKeyAndForwardedToOrigin:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `EnableAcceptEncodingGzip` | **Yes** | boolean | Include Accept-Encoding gzip in cache key |
| `HeadersConfig` | **Yes** | structure | `HeaderBehavior`: `none` or `whitelist` |
| `CookiesConfig` | **Yes** | structure | `CookieBehavior`: `none`, `whitelist`, `allExcept`, `all` |
| `QueryStringsConfig` | **Yes** | structure | `QueryStringBehavior`: `none`, `whitelist`, `allExcept`, `all` |
| `EnableAcceptEncodingBrotli` | No | boolean | Include Accept-Encoding brotli in cache key |

**Output Schema:**
```json
{
    "CachePolicy": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "CachePolicyConfig": {
            "Comment": "string",
            "Name": "string",
            "DefaultTTL": "long",
            "MaxTTL": "long",
            "MinTTL": "long",
            "ParametersInCacheKeyAndForwardedToOrigin": { "..." }
        }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 4.2 `get-cache-policy`

Gets a cache policy.

**Synopsis:**
```bash
aws cloudfront get-cache-policy \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Cache policy ID |

**Output Schema:**
```json
{
    "CachePolicy": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "CachePolicyConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 4.3 `get-cache-policy-config`

Gets the configuration for a cache policy.

**Synopsis:**
```bash
aws cloudfront get-cache-policy-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Cache policy ID |

**Output Schema:**
```json
{
    "CachePolicyConfig": { "..." },
    "ETag": "string"
}
```

---

### 4.4 `list-cache-policies`

Lists cache policies.

**Synopsis:**
```bash
aws cloudfront list-cache-policies \
    [--type <value>] \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | `managed`, `custom`, or omit for all |
| `--marker` | No | string | None | Pagination marker |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "CachePolicyList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "Type": "managed|custom",
                "CachePolicy": {
                    "Id": "string",
                    "LastModifiedTime": "timestamp",
                    "CachePolicyConfig": { "..." }
                }
            }
        ]
    }
}
```

---

### 4.5 `update-cache-policy`

Updates a cache policy.

**Synopsis:**
```bash
aws cloudfront update-cache-policy \
    --id <value> \
    --cache-policy-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Cache policy ID |
| `--cache-policy-config` | **Yes** | structure | Updated cache policy configuration |
| `--if-match` | **Yes** | string | ETag from `get-cache-policy` |

**Output Schema:** Same as `get-cache-policy`.

---

### 4.6 `delete-cache-policy`

Deletes a cache policy. Must not be attached to any distribution.

**Synopsis:**
```bash
aws cloudfront delete-cache-policy \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Cache policy ID |
| `--if-match` | **Yes** | string | ETag from `get-cache-policy` |

**Output:** None.

---
