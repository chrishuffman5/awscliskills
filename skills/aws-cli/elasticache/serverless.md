# Serverless

### 7.1 `create-serverless-cache`

Creates a serverless cache. Serverless caches automatically scale compute and memory based on demand.

**Synopsis:**
```bash
aws elasticache create-serverless-cache \
    --serverless-cache-name <value> \
    --engine <value> \
    [--description <value>] \
    [--major-engine-version <value>] \
    [--cache-usage-limits <value>] \
    [--kms-key-id <value>] \
    [--security-group-ids <value>] \
    [--snapshot-arns-to-restore <value>] \
    [--tags <value>] \
    [--user-group-id <value>] \
    [--subnet-ids <value>] \
    [--snapshot-retention-limit <value>] \
    [--daily-snapshot-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--serverless-cache-name` | **Yes** | string | -- | Name for the serverless cache |
| `--engine` | **Yes** | string | -- | Engine: `redis`, `valkey`, or `memcached` |
| `--description` | No | string | -- | Description |
| `--major-engine-version` | No | string | -- | Major engine version (e.g., `7` for Redis 7) |
| `--cache-usage-limits` | No | structure | -- | Usage limits for scaling |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--security-group-ids` | No | list(string) | -- | VPC security group IDs |
| `--snapshot-arns-to-restore` | No | list(string) | -- | Snapshot ARNs to restore from |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--user-group-id` | No | string | -- | User group ID for RBAC |
| `--subnet-ids` | No | list(string) | -- | Subnet IDs for VPC |
| `--snapshot-retention-limit` | No | integer | -- | Snapshot retention days |
| `--daily-snapshot-time` | No | string | -- | Daily snapshot time (UTC, HH:MM) |

**Cache Usage Limits Structure:**
```json
{
    "DataStorage": {
        "Maximum": "integer",
        "Minimum": "integer",
        "Unit": "GB"
    },
    "ECPUPerSecond": {
        "Maximum": "integer",
        "Minimum": "integer"
    }
}
```

Shorthand: `DataStorage={Maximum=10,Unit=GB},ECPUPerSecond={Maximum=5000}`

**Output Schema:**
```json
{
    "ServerlessCache": {
        "ServerlessCacheName": "string",
        "Description": "string",
        "CreateTime": "timestamp",
        "Status": "creating|available|modifying|deleting|create-failed|delete-failed",
        "Engine": "string",
        "MajorEngineVersion": "string",
        "FullEngineVersion": "string",
        "CacheUsageLimits": {
            "DataStorage": {
                "Maximum": "integer",
                "Minimum": "integer",
                "Unit": "GB"
            },
            "ECPUPerSecond": {
                "Maximum": "integer",
                "Minimum": "integer"
            }
        },
        "KmsKeyId": "string",
        "SecurityGroupIds": ["string"],
        "Endpoint": {
            "Address": "string",
            "Port": "integer"
        },
        "ReaderEndpoint": {
            "Address": "string",
            "Port": "integer"
        },
        "ARN": "string",
        "UserGroupId": "string",
        "SubnetIds": ["string"],
        "SnapshotRetentionLimit": "integer",
        "DailySnapshotTime": "string"
    }
}
```

---

### 7.2 `delete-serverless-cache`

Deletes a serverless cache. Optionally creates a final snapshot before deletion.

**Synopsis:**
```bash
aws elasticache delete-serverless-cache \
    --serverless-cache-name <value> \
    [--final-snapshot-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--serverless-cache-name` | **Yes** | string | -- | Name of the serverless cache to delete |
| `--final-snapshot-name` | No | string | -- | Name for a final snapshot |

**Output Schema:** Same as `create-serverless-cache` output.

---

### 7.3 `describe-serverless-caches`

Returns information about serverless caches. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-serverless-caches \
    [--serverless-cache-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--serverless-cache-name` | No | string | -- | Specific serverless cache name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ServerlessCaches": [
        {
            "ServerlessCacheName": "string",
            "Description": "string",
            "Status": "string",
            "Engine": "string",
            "MajorEngineVersion": "string",
            "Endpoint": {},
            "ReaderEndpoint": {},
            "ARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.4 `modify-serverless-cache`

Modifies a serverless cache. Can change usage limits, security groups, description, and snapshot settings.

**Synopsis:**
```bash
aws elasticache modify-serverless-cache \
    --serverless-cache-name <value> \
    [--description <value>] \
    [--cache-usage-limits <value>] \
    [--remove-user-group | --no-remove-user-group] \
    [--user-group-id <value>] \
    [--security-group-ids <value>] \
    [--snapshot-retention-limit <value>] \
    [--daily-snapshot-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--serverless-cache-name` | **Yes** | string | -- | Name of the serverless cache |
| `--description` | No | string | -- | New description |
| `--cache-usage-limits` | No | structure | -- | New usage limits |
| `--remove-user-group` | No | boolean | false | Disassociate the user group |
| `--user-group-id` | No | string | -- | New user group ID |
| `--security-group-ids` | No | list(string) | -- | New security group IDs |
| `--snapshot-retention-limit` | No | integer | -- | New snapshot retention days |
| `--daily-snapshot-time` | No | string | -- | New daily snapshot time |

**Output Schema:** Same as `create-serverless-cache` output.

---

### 7.5 `create-serverless-cache-snapshot`

Creates a snapshot of a serverless cache.

**Synopsis:**
```bash
aws elasticache create-serverless-cache-snapshot \
    --serverless-cache-snapshot-name <value> \
    --serverless-cache-name <value> \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--serverless-cache-snapshot-name` | **Yes** | string | -- | Name for the snapshot |
| `--serverless-cache-name` | **Yes** | string | -- | Name of the serverless cache |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "ServerlessCacheSnapshot": {
        "ServerlessCacheSnapshotName": "string",
        "ARN": "string",
        "KmsKeyId": "string",
        "SnapshotType": "string",
        "Status": "creating|available|deleting|create-failed|delete-failed",
        "CreateTime": "timestamp",
        "ExpiryTime": "timestamp",
        "BytesUsedForCache": "string",
        "ServerlessCacheConfiguration": {
            "ServerlessCacheName": "string",
            "Engine": "string",
            "MajorEngineVersion": "string"
        }
    }
}
```

---

### 7.6 `delete-serverless-cache-snapshot`

Deletes a serverless cache snapshot.

**Synopsis:**
```bash
aws elasticache delete-serverless-cache-snapshot \
    --serverless-cache-snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--serverless-cache-snapshot-name` | **Yes** | string | -- | Name of the snapshot to delete |

**Output Schema:** Same as `create-serverless-cache-snapshot` output.

---

### 7.7 `describe-serverless-cache-snapshots`

Returns information about serverless cache snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-serverless-cache-snapshots \
    [--serverless-cache-name <value>] \
    [--serverless-cache-snapshot-name <value>] \
    [--snapshot-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--serverless-cache-name` | No | string | -- | Filter by serverless cache name |
| `--serverless-cache-snapshot-name` | No | string | -- | Specific snapshot name |
| `--snapshot-type` | No | string | -- | Filter: `automated` or `user` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ServerlessCacheSnapshots": [
        {
            "ServerlessCacheSnapshotName": "string",
            "ARN": "string",
            "Status": "string",
            "CreateTime": "timestamp",
            "ServerlessCacheConfiguration": {}
        }
    ],
    "NextToken": "string"
}
```
