# File Caches

Amazon File Cache provides a high-speed cache on AWS for processing data stored in on-premises NFS or S3 data repositories. Currently supports only Lustre-based caches.

### 7.1 `create-file-cache`

Creates a Lustre file cache.

**Synopsis:**
```bash
aws fsx create-file-cache \
    --file-cache-type <value> \
    --file-cache-type-version <value> \
    --storage-capacity <value> \
    --subnet-ids <value> \
    [--security-group-ids <value>] \
    [--tags <value>] \
    [--copy-tags-to-data-repository-associations | --no-copy-tags-to-data-repository-associations] \
    [--kms-key-id <value>] \
    [--lustre-configuration <value>] \
    [--data-repository-associations <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-cache-type` | **Yes** | string | -- | Must be `LUSTRE` |
| `--file-cache-type-version` | **Yes** | string | -- | Must be `2.12` |
| `--storage-capacity` | **Yes** | integer | -- | Capacity in GiB (1200, 2400, or increments of 2400) |
| `--subnet-ids` | **Yes** | list | -- | Exactly one subnet ID |
| `--security-group-ids` | No | list | Default SG | Security group IDs |
| `--tags` | No | list | None | Tags (max 50) |
| `--copy-tags-to-data-repository-associations` | No | boolean | false | Copy tags to DRAs |
| `--kms-key-id` | No | string | None | KMS key for encryption |
| `--lustre-configuration` | No | structure | None | Lustre cache config |
| `--data-repository-associations` | No | list | None | DRA configs (max 8) |

**Lustre Configuration:**
```json
{
    "PerUnitStorageThroughput": 1000,
    "DeploymentType": "CACHE_1",
    "WeeklyMaintenanceStartTime": "string (d:HH:MM)",
    "MetadataConfiguration": {
        "StorageCapacity": 2400
    }
}
```

**Data Repository Association (for cache):**
```json
{
    "FileCachePath": "string (required)",
    "DataRepositoryPath": "string (required, s3:// or nfs://)",
    "DataRepositorySubdirectories": ["string"],
    "NFS": {
        "Version": "NFS3",
        "DnsIps": ["string"]
    }
}
```

**Output Schema:**
```json
{
    "FileCache": {
        "OwnerId": "string",
        "CreationTime": "timestamp",
        "FileCacheId": "string",
        "FileCacheType": "LUSTRE",
        "FileCacheTypeVersion": "string",
        "Lifecycle": "AVAILABLE|CREATING|DELETING|UPDATING|FAILED",
        "StorageCapacity": "integer",
        "VpcId": "string",
        "SubnetIds": ["string"],
        "DNSName": "string",
        "KmsKeyId": "string",
        "ResourceARN": "string",
        "Tags": [],
        "CopyTagsToDataRepositoryAssociations": "boolean",
        "LustreConfiguration": {
            "PerUnitStorageThroughput": "integer",
            "DeploymentType": "CACHE_1",
            "MountName": "string",
            "WeeklyMaintenanceStartTime": "string",
            "MetadataConfiguration": {
                "StorageCapacity": "integer"
            },
            "LogConfiguration": {}
        },
        "DataRepositoryAssociationIds": ["string"]
    }
}
```

---

### 7.2 `describe-file-caches`

Returns descriptions of file caches. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-file-caches \
    [--file-cache-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-cache-ids` | No | list | None | File cache IDs (max 50) |

**Output Schema:**
```json
{
    "FileCaches": [
        {
            "FileCacheId": "string",
            "FileCacheType": "LUSTRE",
            "Lifecycle": "string",
            "StorageCapacity": "integer",
            "VpcId": "string",
            "DNSName": "string",
            "ResourceARN": "string",
            "LustreConfiguration": {},
            "DataRepositoryAssociationIds": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 7.3 `update-file-cache`

Updates a file cache's Lustre configuration.

**Synopsis:**
```bash
aws fsx update-file-cache \
    --file-cache-id <value> \
    [--lustre-configuration <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-cache-id` | **Yes** | string | -- | File cache ID |
| `--lustre-configuration` | No | structure | None | Updated Lustre config (maintenance window) |

**Output:** Same as `create-file-cache`

---

### 7.4 `delete-file-cache`

Deletes a file cache.

**Synopsis:**
```bash
aws fsx delete-file-cache \
    --file-cache-id <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-cache-id` | **Yes** | string | -- | File cache ID |

**Output Schema:**
```json
{
    "FileCacheId": "string",
    "Lifecycle": "DELETING"
}
```
