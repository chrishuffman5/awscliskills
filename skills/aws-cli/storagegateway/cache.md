# Cache

### 6.1 `add-cache`

Configures one or more local disks as cache storage on a gateway. Supported for cached volume, tape, and file gateways.

**Synopsis:**
```bash
aws storagegateway add-cache \
    --gateway-arn <value> \
    --disk-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN (50-500 chars) |
| `--disk-ids` | **Yes** | list(string) | -- | Local disk IDs to use as cache (use `list-local-disks` to find available disks) |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 6.2 `describe-cache`

Returns information about the cache of a gateway, including allocation, usage, and hit/miss percentages.

**Synopsis:**
```bash
aws storagegateway describe-cache \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "DiskIds": ["string"],
    "CacheAllocatedInBytes": "long",
    "CacheUsedPercentage": "double",
    "CacheDirtyPercentage": "double",
    "CacheHitPercentage": "double",
    "CacheMissPercentage": "double"
}
```

| Field | Description |
|-------|-------------|
| `CacheAllocatedInBytes` | Total cache allocated in bytes |
| `CacheUsedPercentage` | Percent of cache currently used |
| `CacheDirtyPercentage` | Percent of cache not yet persisted to AWS |
| `CacheHitPercentage` | Percent of read operations served from cache |
| `CacheMissPercentage` | Percent of read operations not served from cache |

---

### 6.3 `reset-cache`

Resets all cache disks that have encountered an error and makes the disks available for reconfiguration as cache. Use if the cache disk goes into `ERROR` state. **This operation is destructive and will delete all data on the cache disk.**

**Synopsis:**
```bash
aws storagegateway reset-cache \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```
