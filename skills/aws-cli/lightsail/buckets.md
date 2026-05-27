# Buckets

### 9.1 `create-bucket`

Creates a Lightsail object storage bucket.

**Synopsis:**
```bash
aws lightsail create-bucket \
    --bucket-name <value> \
    --bundle-id <value> \
    [--tags <value>] \
    [--enable-object-versioning | --no-enable-object-versioning] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | **Yes** | string | -- | Name for the bucket (globally unique) |
| `--bundle-id` | **Yes** | string | -- | Bundle ID: `small_1_0` (5 GB), `medium_1_0` (100 GB), `large_1_0` (250 GB) |
| `--tags` | No | list | None | Tags |
| `--enable-object-versioning` | No | boolean | false | Enable object versioning |

**Output Schema:**
```json
{
    "bucket": {
        "resourceType": "Bucket",
        "accessRules": {
            "getObject": "public|private",
            "allowPublicOverrides": true|false
        },
        "arn": "string",
        "bundleId": "string",
        "createdAt": "timestamp",
        "url": "string",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "name": "string",
        "supportCode": "string",
        "tags": [],
        "objectVersioning": "string",
        "ableToUpdateBundle": true|false,
        "readonlyAccessAccounts": ["string"],
        "resourcesReceivingAccess": [],
        "state": {
            "code": "string",
            "message": "string"
        },
        "accessLogConfig": {
            "enabled": true|false,
            "destination": "string",
            "prefix": "string"
        }
    },
    "operations": []
}
```

---

### 9.2 `delete-bucket`

Deletes a bucket.

**Synopsis:**
```bash
aws lightsail delete-bucket \
    --bucket-name <value> \
    [--force-delete | --no-force-delete] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | **Yes** | string | -- | Name of the bucket to delete |
| `--force-delete` | No | boolean | false | Force delete even if bucket is not empty |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Bucket",
            "operationType": "DeleteBucket",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 9.3 `get-buckets`

Returns information about buckets. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-buckets \
    [--bucket-name <value>] \
    [--page-token <value>] \
    [--include-connected-resources | --no-include-connected-resources] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | No | string | None | Specific bucket name |
| `--page-token` | No | string | None | Pagination token |
| `--include-connected-resources` | No | boolean | false | Include connected instance resources |

**Output Schema:**
```json
{
    "buckets": [
        {
            "name": "string",
            "arn": "string",
            "bundleId": "string",
            "url": "string",
            "objectVersioning": "string",
            "state": {
                "code": "string",
                "message": "string"
            }
        }
    ],
    "nextPageToken": "string",
    "accountLevelBpaSync": {
        "status": "InSync|Failed|NeverSynced|Defaulted",
        "lastSyncedAt": "timestamp",
        "message": "DEFAULTED_FOR_SLR_MISSING|...",
        "bpaImpactsLightsail": true|false
    }
}
```

---

### 9.4 `update-bucket`

Updates the configuration of a bucket.

**Synopsis:**
```bash
aws lightsail update-bucket \
    --bucket-name <value> \
    [--access-rules <value>] \
    [--versioning <value>] \
    [--readonly-access-accounts <value>] \
    [--access-log-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | **Yes** | string | -- | Name of the bucket |
| `--access-rules` | No | structure | None | Access rules. Shorthand: `getObject=public\|private,allowPublicOverrides=boolean` |
| `--versioning` | No | string | None | Versioning: `Enabled`, `Suspended` |
| `--readonly-access-accounts` | No | list(string) | None | AWS account IDs for read-only cross-account access |
| `--access-log-config` | No | structure | None | Access log config. Shorthand: `enabled=boolean,destination=string,prefix=string` |

**Output Schema:**
```json
{
    "bucket": {
        "name": "string",
        "arn": "string",
        "bundleId": "string",
        "accessRules": {
            "getObject": "public|private",
            "allowPublicOverrides": true|false
        },
        "objectVersioning": "string"
    },
    "operations": []
}
```

---

### 9.5 `update-bucket-bundle`

Updates the bundle (plan) for a bucket.

**Synopsis:**
```bash
aws lightsail update-bucket-bundle \
    --bucket-name <value> \
    --bundle-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | **Yes** | string | -- | Name of the bucket |
| `--bundle-id` | **Yes** | string | -- | New bundle ID |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Bucket",
            "operationType": "UpdateBucketBundle",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 9.6 `get-bucket-bundles`

Returns available bucket bundles.

**Synopsis:**
```bash
aws lightsail get-bucket-bundles \
    [--include-inactive | --no-include-inactive] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include-inactive` | No | boolean | false | Include inactive bundles |

**Output Schema:**
```json
{
    "bundles": [
        {
            "bundleId": "string",
            "name": "string",
            "price": "float",
            "storagePerMonthInGb": "integer",
            "transferPerMonthInGb": "integer",
            "isActive": true|false
        }
    ]
}
```

---

### 9.7 `get-bucket-access-keys`

Returns access keys for a bucket.

**Synopsis:**
```bash
aws lightsail get-bucket-access-keys \
    --bucket-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | **Yes** | string | -- | Name of the bucket |

**Output Schema:**
```json
{
    "accessKeys": [
        {
            "accessKeyId": "string",
            "secretAccessKey": "string",
            "status": "Active|Inactive",
            "createdAt": "timestamp",
            "lastUsed": {
                "lastUsedDate": "timestamp",
                "region": "string",
                "serviceName": "string"
            }
        }
    ]
}
```

---

### 9.8 `create-bucket-access-key`

Creates an access key for a bucket.

**Synopsis:**
```bash
aws lightsail create-bucket-access-key \
    --bucket-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | **Yes** | string | -- | Name of the bucket |

**Output Schema:**
```json
{
    "accessKey": {
        "accessKeyId": "string",
        "secretAccessKey": "string",
        "status": "Active",
        "createdAt": "timestamp"
    },
    "operations": []
}
```

---

### 9.9 `delete-bucket-access-key`

Deletes an access key for a bucket.

**Synopsis:**
```bash
aws lightsail delete-bucket-access-key \
    --bucket-name <value> \
    --access-key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | **Yes** | string | -- | Name of the bucket |
| `--access-key-id` | **Yes** | string | -- | Access key ID to delete |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Bucket",
            "operationType": "DeleteBucketAccessKey",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 9.10 `get-bucket-metric-data`

Returns metric data for a bucket.

**Synopsis:**
```bash
aws lightsail get-bucket-metric-data \
    --bucket-name <value> \
    --metric-name <value> \
    --start-time <value> \
    --end-time <value> \
    --period <value> \
    --statistics <value> \
    --unit <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | **Yes** | string | -- | Name of the bucket |
| `--metric-name` | **Yes** | string | -- | Metric: `BucketSizeBytes`, `NumberOfObjects` |
| `--start-time` | **Yes** | timestamp | -- | Start time |
| `--end-time` | **Yes** | timestamp | -- | End time |
| `--period` | **Yes** | integer | -- | Granularity in seconds |
| `--statistics` | **Yes** | list(string) | -- | Statistics: `Minimum`, `Maximum`, `Sum`, `Average`, `SampleCount` |
| `--unit` | **Yes** | string | -- | Unit for the metric |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricData": [
        {
            "average": "double",
            "maximum": "double",
            "minimum": "double",
            "sampleCount": "double",
            "sum": "double",
            "timestamp": "timestamp",
            "unit": "string"
        }
    ]
}
```

---

### 9.11 `set-resource-access-for-bucket`

Sets whether an instance can access a bucket.

**Synopsis:**
```bash
aws lightsail set-resource-access-for-bucket \
    --resource-name <value> \
    --bucket-name <value> \
    --access <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the instance |
| `--bucket-name` | **Yes** | string | -- | Name of the bucket |
| `--access` | **Yes** | string | -- | Access level: `allow`, `deny` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Bucket",
            "operationType": "SetResourceAccessForBucket",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```
