# Data Repository

Data repository associations link FSx for Lustre file systems to S3 buckets or NFS data sources, enabling automatic data synchronization. Data repository tasks perform bulk operations on these linked paths.

---

## Associations

### 6.1 `create-data-repository-association`

Creates a link between a Lustre file system path and an S3 or NFS data repository.

**Synopsis:**
```bash
aws fsx create-data-repository-association \
    --file-system-id <value> \
    --data-repository-path <value> \
    [--file-system-path <value>] \
    [--batch-import-meta-data-on-create | --no-batch-import-meta-data-on-create] \
    [--imported-file-chunk-size <value>] \
    [--s3 <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | Lustre file system ID |
| `--data-repository-path` | **Yes** | string | -- | S3 path (`s3://bucket/prefix/`) or NFS path |
| `--file-system-path` | No | string | None | Mount path on file system (e.g., `/ns1/`) |
| `--batch-import-meta-data-on-create` | No | boolean | false | Run import task after creation |
| `--imported-file-chunk-size` | No | integer | 1024 | Stripe size in MiB (1-512000) |
| `--s3` | No | structure | None | S3 auto-import/export policies |
| `--tags` | No | list | None | Tags (max 50) |

**S3 Configuration:**
```json
{
    "AutoImportPolicy": {
        "Events": ["NEW", "CHANGED", "DELETED"]
    },
    "AutoExportPolicy": {
        "Events": ["NEW", "CHANGED", "DELETED"]
    }
}
```

**Output Schema:**
```json
{
    "Association": {
        "AssociationId": "string",
        "ResourceARN": "string",
        "FileSystemId": "string",
        "Lifecycle": "CREATING|AVAILABLE|MISCONFIGURED|UPDATING|DELETING|FAILED",
        "FileSystemPath": "string",
        "DataRepositoryPath": "string",
        "BatchImportMetaDataOnCreate": "boolean",
        "ImportedFileChunkSize": "integer",
        "S3": {},
        "Tags": [],
        "CreationTime": "timestamp",
        "NFS": {
            "Version": "NFS3",
            "DnsIps": ["string"]
        }
    }
}
```

---

### 6.2 `describe-data-repository-associations`

Returns descriptions of data repository associations. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-data-repository-associations \
    [--association-ids <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-ids` | No | list | None | Association IDs (max 50) |
| `--filters` | No | list | None | Filters: `file-system-id`, `backup-type`, `file-system-type`, `data-repository-type` |

**Output Schema:**
```json
{
    "Associations": [
        {
            "AssociationId": "string",
            "FileSystemId": "string",
            "Lifecycle": "string",
            "FileSystemPath": "string",
            "DataRepositoryPath": "string",
            "S3": {},
            "NFS": {},
            "Tags": [],
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.3 `update-data-repository-association`

Updates a data repository association's S3 configuration.

**Synopsis:**
```bash
aws fsx update-data-repository-association \
    --association-id <value> \
    [--s3 <value>] \
    [--imported-file-chunk-size <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-id` | **Yes** | string | -- | Association ID |
| `--s3` | No | structure | None | Updated S3 policies |
| `--imported-file-chunk-size` | No | integer | None | Updated chunk size |

**Output:** Same as `create-data-repository-association`

---

### 6.4 `delete-data-repository-association`

Deletes a data repository association.

**Synopsis:**
```bash
aws fsx delete-data-repository-association \
    --association-id <value> \
    [--delete-data-in-file-system | --no-delete-data-in-file-system] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-id` | **Yes** | string | -- | Association ID |
| `--delete-data-in-file-system` | No | boolean | false | Delete associated data from file system |

**Output Schema:**
```json
{
    "AssociationId": "string",
    "Lifecycle": "DELETING",
    "DeleteDataInFileSystem": "boolean"
}
```

---

## Tasks

### 6.5 `create-data-repository-task`

Creates a data repository task (export, import, release, or auto-release).

**Synopsis:**
```bash
aws fsx create-data-repository-task \
    --type <value> \
    --file-system-id <value> \
    --report <value> \
    [--paths <value>] \
    [--capacity-to-release <value>] \
    [--release-configuration <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | `EXPORT_TO_REPOSITORY`, `IMPORT_METADATA_FROM_REPOSITORY`, `RELEASE_DATA_FROM_FILESYSTEM`, or `AUTO_RELEASE_DATA` |
| `--file-system-id` | **Yes** | string | -- | Lustre file system ID |
| `--report` | **Yes** | structure | -- | Completion report config |
| `--paths` | No | list | None | Paths to process (max 100) |
| `--capacity-to-release` | No | long | None | GiB to release (for AUTO_RELEASE_DATA) |
| `--release-configuration` | No | structure | None | Release criteria |
| `--tags` | No | list | None | Tags |

**Report Structure:**
```json
{
    "Enabled": "boolean (required)",
    "Path": "string (required if Enabled=true, s3://...)",
    "Format": "REPORT_CSV_20191124",
    "Scope": "FAILED_FILES_ONLY"
}
```

**Release Configuration:**
```json
{
    "DurationSinceLastAccess": {
        "Unit": "DAYS",
        "Value": "long"
    }
}
```

**Output Schema:**
```json
{
    "DataRepositoryTask": {
        "TaskId": "string",
        "Lifecycle": "PENDING|EXECUTING|FAILED|SUCCEEDED|CANCELED|CANCELING",
        "Type": "string",
        "CreationTime": "timestamp",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "FileSystemId": "string",
        "Paths": ["string"],
        "Report": {},
        "Status": {
            "TotalCount": "long",
            "SucceededCount": "long",
            "FailedCount": "long",
            "LastUpdatedTime": "timestamp",
            "ReleasedCapacity": "long"
        },
        "ResourceARN": "string",
        "Tags": []
    }
}
```

---

### 6.6 `describe-data-repository-tasks`

Returns descriptions of data repository tasks. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-data-repository-tasks \
    [--task-ids <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-ids` | No | list | None | Task IDs (max 50) |
| `--filters` | No | list | None | Filters: `file-system-id`, `task-lifecycle` |

**Output Schema:**
```json
{
    "DataRepositoryTasks": [
        {
            "TaskId": "string",
            "Lifecycle": "string",
            "Type": "string",
            "FileSystemId": "string",
            "Status": {},
            "Report": {},
            "CreationTime": "timestamp",
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.7 `cancel-data-repository-task`

Cancels a running data repository task.

**Synopsis:**
```bash
aws fsx cancel-data-repository-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID |

**Output Schema:**
```json
{
    "Lifecycle": "CANCELING",
    "TaskId": "string"
}
```
