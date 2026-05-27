# Buckets

### 7.1 `describe-buckets`

Retrieves statistical data and other information about one or more S3 buckets that Macie monitors. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 describe-buckets \
    [--criteria <value>] \
    [--sort-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--criteria` | No | map | None | Filter criteria for buckets |
| `--sort-criteria` | No | structure | None | Sort criteria |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "buckets": [
        {
            "accountId": "string",
            "allowsUnencryptedObjectUploads": "TRUE|FALSE|UNKNOWN",
            "automatedDiscoveryMonitoringStatus": "MONITORED|NOT_MONITORED",
            "bucketArn": "string",
            "bucketCreatedAt": "timestamp",
            "bucketName": "string",
            "classifiableObjectCount": "long",
            "classifiableSizeInBytes": "long",
            "errorCode": "ACCESS_DENIED",
            "errorMessage": "string",
            "jobDetails": {
                "isDefinedInJob": "TRUE|FALSE|UNKNOWN",
                "isMonitoredByJob": "TRUE|FALSE|UNKNOWN",
                "lastJobId": "string",
                "lastJobRunTime": "timestamp"
            },
            "lastAutomatedDiscoveryTime": "timestamp",
            "lastUpdated": "timestamp",
            "objectCount": "long",
            "objectCountByEncryptionType": {
                "customerManaged": "long",
                "kmsManaged": "long",
                "s3Managed": "long",
                "unencrypted": "long",
                "unknown": "long"
            },
            "publicAccess": {
                "effectivePermission": "PUBLIC|NOT_PUBLIC|UNKNOWN",
                "permissionConfiguration": {}
            },
            "region": "string",
            "replicationDetails": {},
            "sensitivityScore": "integer",
            "serverSideEncryption": {},
            "sharedAccess": "EXTERNAL|INTERNAL|NOT_SHARED|UNKNOWN",
            "sizeInBytes": "long",
            "sizeInBytesCompressed": "long",
            "tags": [],
            "unclassifiableObjectCount": {},
            "unclassifiableObjectSizeInBytes": {},
            "versioning": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.2 `get-bucket-statistics`

Retrieves aggregated statistical data for all S3 buckets.

**Synopsis:**
```bash
aws macie2 get-bucket-statistics \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | No | string | None | AWS account ID to get stats for |

**Output Schema:**
```json
{
    "bucketCount": "long",
    "bucketCountByEffectivePermission": {
        "publiclyAccessible": "long",
        "publiclyReadable": "long",
        "publiclyWritable": "long",
        "unknown": "long"
    },
    "bucketCountByEncryptionType": {
        "kmsManaged": "long",
        "s3Managed": "long",
        "unencrypted": "long",
        "unknown": "long"
    },
    "bucketCountByObjectEncryptionRequirement": {
        "allowsUnencryptedObjectUploads": "long",
        "deniesUnencryptedObjectUploads": "long",
        "unknown": "long"
    },
    "bucketCountBySharedAccessType": {
        "external": "long",
        "internal": "long",
        "notShared": "long",
        "unknown": "long"
    },
    "bucketStatisticsBySensitivity": {},
    "classifiableObjectCount": "long",
    "classifiableSizeInBytes": "long",
    "lastUpdated": "timestamp",
    "objectCount": "long",
    "sizeInBytes": "long",
    "sizeInBytesCompressed": "long",
    "unclassifiableObjectCount": {},
    "unclassifiableObjectSizeInBytes": {}
}
```

---

### 7.3 `search-resources`

Retrieves statistical data and other information about Macie resources. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 search-resources \
    [--bucket-criteria <value>] \
    [--sort-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-criteria` | No | structure | None | Filter criteria for resources |
| `--sort-criteria` | No | structure | None | Sort criteria |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "matchingResources": [
        {
            "matchingBucket": {
                "accountId": "string",
                "bucketName": "string",
                "classifiableObjectCount": "long",
                "classifiableSizeInBytes": "long",
                "errorCode": "string",
                "errorMessage": "string",
                "objectCount": "long",
                "objectCountByEncryptionType": {},
                "sizeInBytes": "long",
                "sizeInBytesCompressed": "long",
                "unclassifiableObjectCount": {},
                "unclassifiableObjectSizeInBytes": {}
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `get-classification-export-configuration`

Retrieves the configuration settings for exporting data classification results.

**Synopsis:**
```bash
aws macie2 get-classification-export-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "configuration": {
        "s3Destination": {
            "bucketName": "string",
            "keyPrefix": "string",
            "kmsKeyArn": "string"
        }
    }
}
```

---

### 7.5 `put-classification-export-configuration`

Creates or updates the configuration settings for exporting data classification results.

**Synopsis:**
```bash
aws macie2 put-classification-export-configuration \
    --configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration` | **Yes** | structure | -- | Export configuration |

**Configuration Structure:**
```json
{
    "s3Destination": {
        "bucketName": "string",
        "keyPrefix": "string",
        "kmsKeyArn": "string"
    }
}
```

**Output Schema:**
```json
{
    "configuration": {
        "s3Destination": {
            "bucketName": "string",
            "keyPrefix": "string",
            "kmsKeyArn": "string"
        }
    }
}
```

---

### 7.6 `get-classification-scope`

Retrieves the classification scope settings for an account.

**Synopsis:**
```bash
aws macie2 get-classification-scope \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Classification scope ID |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "s3": {
        "excludes": {
            "bucketNames": ["string"]
        }
    }
}
```

---

### 7.7 `list-classification-scopes`

Lists classification scopes. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-classification-scopes \
    [--name <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Filter by name |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "classificationScopes": [
        {
            "id": "string",
            "name": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.8 `update-classification-scope`

Updates the classification scope settings.

**Synopsis:**
```bash
aws macie2 update-classification-scope \
    --id <value> \
    [--s3 <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Classification scope ID |
| `--s3` | No | structure | None | S3 scope update |

**Output:** None (HTTP 200 on success)
