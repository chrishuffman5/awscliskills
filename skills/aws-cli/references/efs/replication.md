# Replication

### 4.1 `create-replication-configuration`

Creates a replication configuration to replicate an existing EFS file system to a new read-only file system. The source file system cannot already be a source or destination in another replication configuration.

**Synopsis:**
```bash
aws efs create-replication-configuration \
    --source-file-system-id <value> \
    --destinations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-file-system-id` | **Yes** | string | -- | ID of the source file system |
| `--destinations` | **Yes** | list | -- | Destination configuration (only one destination supported) |

**Destination Structure:**
```json
[
    {
        "Region": "string",
        "AvailabilityZoneName": "string",
        "KmsKeyId": "string",
        "FileSystemId": "string"
    }
]
```

Shorthand: `Region=us-west-2` or `Region=us-west-2,KmsKeyId=arn:aws:kms:...`

- `Region` — Destination region. Required if no `FileSystemId` is specified.
- `AvailabilityZoneName` — AZ for a One Zone destination file system.
- `KmsKeyId` — KMS key for encrypting the destination. Uses service-managed key if omitted.
- `FileSystemId` — ID of an existing file system to use as destination (for cross-account replication).

**Output Schema:**
```json
{
    "SourceFileSystemId": "string",
    "SourceFileSystemRegion": "string",
    "SourceFileSystemArn": "string",
    "OriginalSourceFileSystemArn": "string",
    "CreationTime": "timestamp",
    "Destinations": [
        {
            "Status": "ENABLED|ENABLING|DELETING|ERROR|PAUSED|PAUSING",
            "FileSystemId": "string",
            "Region": "string",
            "LastReplicatedTimestamp": "timestamp",
            "OwnerId": "string",
            "StatusMessage": "string"
        }
    ]
}
```

---

### 4.2 `delete-replication-configuration`

Deletes a replication configuration. Deleting a replication configuration ends the replication process. The destination file system becomes writeable after replication is deleted.

**Synopsis:**
```bash
aws efs delete-replication-configuration \
    --source-file-system-id <value> \
    [--deletion-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-file-system-id` | **Yes** | string | -- | ID of the source file system in the replication |
| `--deletion-mode` | No | string | `ALL_CONFIGURATIONS` | Deletion mode: `ALL_CONFIGURATIONS` or `LOCAL_CONFIGURATION_ONLY` |

**Output:** None on success.

---

### 4.3 `describe-replication-configurations`

Retrieves the replication configuration for a specific file system, or all replication configurations in the account. **Paginated operation.**

**Synopsis:**
```bash
aws efs describe-replication-configurations \
    [--file-system-id <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | No | string | -- | File system ID (source or destination) to filter by |
| `--next-token` | No | string | None | Pagination token from previous response |
| `--max-results` | No | integer | None | Maximum number of results (1-100) |

**Output Schema:**
```json
{
    "Replications": [
        {
            "SourceFileSystemId": "string",
            "SourceFileSystemRegion": "string",
            "SourceFileSystemArn": "string",
            "OriginalSourceFileSystemArn": "string",
            "CreationTime": "timestamp",
            "Destinations": [
                {
                    "Status": "ENABLED|ENABLING|DELETING|ERROR|PAUSED|PAUSING",
                    "FileSystemId": "string",
                    "Region": "string",
                    "LastReplicatedTimestamp": "timestamp",
                    "OwnerId": "string",
                    "StatusMessage": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```
