# Snapshots

### 2.1 `create-cluster-snapshot`

Creates a manual snapshot of the specified cluster.

**Synopsis:**
```bash
aws redshift create-cluster-snapshot \
    --snapshot-identifier <value> \
    --cluster-identifier <value> \
    [--manual-snapshot-retention-period <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Unique identifier for the snapshot |
| `--cluster-identifier` | **Yes** | string | -- | Cluster to snapshot |
| `--manual-snapshot-retention-period` | No | integer | -1 | Days to retain (-1 = indefinite) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Snapshot": {
        "SnapshotIdentifier": "string",
        "ClusterIdentifier": "string",
        "SnapshotCreateTime": "timestamp",
        "Status": "creating|available|failed|deleting",
        "Port": "integer",
        "AvailabilityZone": "string",
        "ClusterCreateTime": "timestamp",
        "MasterUsername": "string",
        "ClusterVersion": "string",
        "EngineFullVersion": "string",
        "SnapshotType": "manual|automated",
        "NodeType": "string",
        "NumberOfNodes": "integer",
        "DBName": "string",
        "VpcId": "string",
        "Encrypted": "boolean",
        "KmsKeyId": "string",
        "EncryptedWithHSM": "boolean",
        "AccountsWithRestoreAccess": [],
        "OwnerAccount": "string",
        "TotalBackupSizeInMegaBytes": "double",
        "ActualIncrementalBackupSizeInMegaBytes": "double",
        "BackupProgressInMegaBytes": "double",
        "CurrentBackupRateInMegaBytesPerSecond": "double",
        "EstimatedSecondsToCompletion": "long",
        "ElapsedTimeInSeconds": "long",
        "Tags": [{"Key": "string", "Value": "string"}],
        "EnhancedVpcRouting": "boolean",
        "MaintenanceTrackName": "string",
        "ManualSnapshotRetentionPeriod": "integer",
        "ManualSnapshotRemainingDays": "integer",
        "SnapshotRetentionStartTime": "timestamp",
        "MasterPasswordSecretArn": "string",
        "MasterPasswordSecretKmsKeyId": "string"
    }
}
```

---

### 2.2 `delete-cluster-snapshot`

Deletes a manual snapshot.

**Synopsis:**
```bash
aws redshift delete-cluster-snapshot \
    --snapshot-identifier <value> \
    [--snapshot-cluster-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot to delete |
| `--snapshot-cluster-identifier` | No | string | -- | Cluster that created the snapshot |

**Output Schema:**
```json
{
    "Snapshot": {
        "SnapshotIdentifier": "string",
        "ClusterIdentifier": "string",
        "Status": "deleting"
    }
}
```

---

### 2.3 `describe-cluster-snapshots`

Returns one or more snapshot records. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-cluster-snapshots \
    [--cluster-identifier <value>] \
    [--snapshot-identifier <value>] \
    [--snapshot-arn <value>] \
    [--snapshot-type <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--owner-account <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--cluster-exists | --no-cluster-exists] \
    [--sorting-entities <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | No | string | -- | Filter by cluster |
| `--snapshot-identifier` | No | string | -- | Specific snapshot |
| `--snapshot-arn` | No | string | -- | Snapshot ARN |
| `--snapshot-type` | No | string | -- | `automated` or `manual` |
| `--start-time` | No | timestamp | -- | Filter snapshots created after this time |
| `--end-time` | No | timestamp | -- | Filter snapshots created before this time |
| `--owner-account` | No | string | -- | Filter by owner account |
| `--cluster-exists` | No | boolean | -- | Filter by whether source cluster still exists |
| `--sorting-entities` | No | list | -- | Sort order. Shorthand: `Attribute=SOURCE_TYPE\|TOTAL_SIZE\|CREATE_TIME,SortOrder=ASC\|DESC` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Snapshots": [
        {
            "SnapshotIdentifier": "string",
            "ClusterIdentifier": "string",
            "SnapshotCreateTime": "timestamp",
            "Status": "string",
            "SnapshotType": "string",
            "NodeType": "string",
            "NumberOfNodes": "integer",
            "DBName": "string",
            "Encrypted": "boolean",
            "TotalBackupSizeInMegaBytes": "double",
            "Tags": []
        }
    ],
    "Marker": "string"
}
```

---

### 2.4 `copy-cluster-snapshot`

Copies the specified automated or manual snapshot to a new manual snapshot.

**Synopsis:**
```bash
aws redshift copy-cluster-snapshot \
    --source-snapshot-identifier <value> \
    --target-snapshot-identifier <value> \
    [--source-snapshot-cluster-identifier <value>] \
    [--manual-snapshot-retention-period <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-snapshot-identifier` | **Yes** | string | -- | Source snapshot identifier |
| `--target-snapshot-identifier` | **Yes** | string | -- | Target snapshot identifier |
| `--source-snapshot-cluster-identifier` | No | string | -- | Cluster that created the source snapshot |
| `--manual-snapshot-retention-period` | No | integer | -- | Days to retain the copy |

**Output Schema:**
```json
{
    "Snapshot": {
        "SnapshotIdentifier": "string",
        "ClusterIdentifier": "string",
        "Status": "creating",
        "SnapshotType": "manual"
    }
}
```

---

### 2.5 `authorize-snapshot-access`

Authorizes another AWS account to copy or restore a snapshot.

**Synopsis:**
```bash
aws redshift authorize-snapshot-access \
    --snapshot-identifier <value> \
    --account-with-restore-access <value> \
    [--snapshot-arn <value>] \
    [--snapshot-cluster-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot to share |
| `--account-with-restore-access` | **Yes** | string | -- | AWS account ID to authorize |
| `--snapshot-arn` | No | string | -- | Snapshot ARN |
| `--snapshot-cluster-identifier` | No | string | -- | Cluster that created the snapshot |

**Output Schema:**
```json
{
    "Snapshot": {
        "SnapshotIdentifier": "string",
        "AccountsWithRestoreAccess": [
            {
                "AccountId": "string",
                "AccountAlias": "string"
            }
        ]
    }
}
```

---

### 2.6 `revoke-snapshot-access`

Revokes previously authorized snapshot access.

**Synopsis:**
```bash
aws redshift revoke-snapshot-access \
    --snapshot-identifier <value> \
    --account-with-restore-access <value> \
    [--snapshot-arn <value>] \
    [--snapshot-cluster-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot to revoke access from |
| `--account-with-restore-access` | **Yes** | string | -- | AWS account ID to revoke |
| `--snapshot-arn` | No | string | -- | Snapshot ARN |
| `--snapshot-cluster-identifier` | No | string | -- | Cluster that created the snapshot |

**Output Schema:**
```json
{
    "Snapshot": {
        "SnapshotIdentifier": "string",
        "AccountsWithRestoreAccess": []
    }
}
```

---

### 2.7 `batch-delete-cluster-snapshots`

Deletes a set of cluster snapshots.

**Synopsis:**
```bash
aws redshift batch-delete-cluster-snapshots \
    --identifiers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifiers` | **Yes** | list | -- | List of snapshot identifiers. Shorthand: `SnapshotIdentifier=string,SnapshotClusterIdentifier=string ...` |

**Output Schema:**
```json
{
    "Resources": ["string"],
    "Errors": [
        {
            "SnapshotIdentifier": "string",
            "SnapshotClusterIdentifier": "string",
            "FailureCode": "string",
            "FailureReason": "string"
        }
    ]
}
```

---

### 2.8 `modify-cluster-snapshot-attribute`

Modifies snapshot sharing attributes, such as adding/removing account access.

**Synopsis:**
```bash
aws redshift modify-cluster-snapshot-attribute \
    --snapshot-identifier <value> \
    --attribute-name <value> \
    [--values-to-add <value>] \
    [--values-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot to modify |
| `--attribute-name` | **Yes** | string | -- | Attribute: `restore` |
| `--values-to-add` | No | list(string) | -- | Account IDs to grant access |
| `--values-to-remove` | No | list(string) | -- | Account IDs to revoke access |

**Output Schema:**
```json
{
    "ClusterSnapshotAttribute": {
        "SnapshotIdentifier": "string",
        "AttributeName": "restore",
        "AttributeValues": ["string"]
    }
}
```

---

### 2.9 `enable-snapshot-copy`

Enables cross-region snapshot copy for a cluster.

**Synopsis:**
```bash
aws redshift enable-snapshot-copy \
    --cluster-identifier <value> \
    --destination-region <value> \
    [--retention-period <value>] \
    [--snapshot-copy-grant-name <value>] \
    [--manual-snapshot-retention-period <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to enable copy for |
| `--destination-region` | **Yes** | string | -- | Destination region for copies |
| `--retention-period` | No | integer | 7 | Days to retain copies in destination |
| `--snapshot-copy-grant-name` | No | string | -- | Grant name for encrypted snapshots |
| `--manual-snapshot-retention-period` | No | integer | -- | Manual snapshot retention in destination |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterSnapshotCopyStatus": {
            "DestinationRegion": "string",
            "RetentionPeriod": "long",
            "ManualSnapshotRetentionPeriod": "integer",
            "SnapshotCopyGrantName": "string"
        }
    }
}
```

---

### 2.10 `disable-snapshot-copy`

Disables cross-region snapshot copy for a cluster.

**Synopsis:**
```bash
aws redshift disable-snapshot-copy \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to disable copy for |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterSnapshotCopyStatus": null
    }
}
```

---

### 2.11 `modify-snapshot-copy-retention-period`

Modifies the retention period for cross-region snapshot copies.

**Synopsis:**
```bash
aws redshift modify-snapshot-copy-retention-period \
    --cluster-identifier <value> \
    --retention-period <value> \
    [--manual | --no-manual] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--retention-period` | **Yes** | integer | -- | New retention period in days |
| `--manual` | No | boolean | false | Apply to manual snapshots |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterSnapshotCopyStatus": {
            "DestinationRegion": "string",
            "RetentionPeriod": "long",
            "ManualSnapshotRetentionPeriod": "integer"
        }
    }
}
```

---

### 2.12 `create-snapshot-schedule`

Creates a new snapshot schedule.

**Synopsis:**
```bash
aws redshift create-snapshot-schedule \
    [--schedule-definitions <value>] \
    [--schedule-identifier <value>] \
    [--schedule-description <value>] \
    [--tags <value>] \
    [--dry-run | --no-dry-run] \
    [--next-invocations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schedule-definitions` | No | list(string) | -- | Cron-like schedule expressions (e.g., `rate(12 hours)`) |
| `--schedule-identifier` | No | string | -- | Unique schedule identifier |
| `--schedule-description` | No | string | -- | Description of the schedule |
| `--tags` | No | list | -- | Tags |
| `--dry-run` | No | boolean | false | Validate without creating |
| `--next-invocations` | No | integer | -- | Number of upcoming invocations to return |

**Output Schema:**
```json
{
    "ScheduleDefinitions": ["string"],
    "ScheduleIdentifier": "string",
    "ScheduleDescription": "string",
    "Tags": [{"Key": "string", "Value": "string"}],
    "NextInvocations": ["timestamp"],
    "AssociatedClusterCount": "integer",
    "AssociatedClusters": [
        {
            "ClusterIdentifier": "string",
            "ScheduleAssociationState": "MODIFYING|ACTIVE|FAILED"
        }
    ]
}
```

---

### 2.13 `delete-snapshot-schedule`

Deletes a snapshot schedule.

**Synopsis:**
```bash
aws redshift delete-snapshot-schedule \
    --schedule-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schedule-identifier` | **Yes** | string | -- | Schedule to delete |

No output on success.

---

### 2.14 `describe-snapshot-schedules`

Returns snapshot schedule descriptions. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-snapshot-schedules \
    [--cluster-identifier <value>] \
    [--schedule-identifier <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | No | string | -- | Filter by cluster |
| `--schedule-identifier` | No | string | -- | Specific schedule |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "SnapshotSchedules": [
        {
            "ScheduleDefinitions": ["string"],
            "ScheduleIdentifier": "string",
            "ScheduleDescription": "string",
            "Tags": [],
            "NextInvocations": ["timestamp"],
            "AssociatedClusterCount": "integer",
            "AssociatedClusters": []
        }
    ],
    "Marker": "string"
}
```

---

### 2.15 `modify-snapshot-schedule`

Modifies a snapshot schedule definition.

**Synopsis:**
```bash
aws redshift modify-snapshot-schedule \
    --schedule-identifier <value> \
    --schedule-definitions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--schedule-identifier` | **Yes** | string | -- | Schedule to modify |
| `--schedule-definitions` | **Yes** | list(string) | -- | New schedule definitions |

**Output Schema:**
```json
{
    "ScheduleDefinitions": ["string"],
    "ScheduleIdentifier": "string",
    "ScheduleDescription": "string",
    "Tags": [],
    "NextInvocations": ["timestamp"],
    "AssociatedClusterCount": "integer",
    "AssociatedClusters": []
}
```

---

### 2.16 `modify-cluster-snapshot-schedule`

Associates or disassociates a snapshot schedule with a cluster.

**Synopsis:**
```bash
aws redshift modify-cluster-snapshot-schedule \
    --cluster-identifier <value> \
    [--schedule-identifier <value>] \
    [--disassociate-schedule | --no-disassociate-schedule] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to modify |
| `--schedule-identifier` | No | string | -- | Schedule to associate |
| `--disassociate-schedule` | No | boolean | false | Disassociate the current schedule |

No output on success.

---

### 2.17 `create-snapshot-copy-grant`

Creates a KMS snapshot copy grant in the destination region for cross-region encrypted snapshot copy.

**Synopsis:**
```bash
aws redshift create-snapshot-copy-grant \
    --snapshot-copy-grant-name <value> \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-copy-grant-name` | **Yes** | string | -- | Grant name |
| `--kms-key-id` | No | string | -- | KMS key ID (defaults to default key) |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "SnapshotCopyGrant": {
        "SnapshotCopyGrantName": "string",
        "KmsKeyId": "string",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 2.18 `delete-snapshot-copy-grant`

Deletes a snapshot copy grant.

**Synopsis:**
```bash
aws redshift delete-snapshot-copy-grant \
    --snapshot-copy-grant-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-copy-grant-name` | **Yes** | string | -- | Grant name to delete |

No output on success.

---

### 2.19 `describe-snapshot-copy-grants`

Returns snapshot copy grant descriptions. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-snapshot-copy-grants \
    [--snapshot-copy-grant-name <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-copy-grant-name` | No | string | -- | Specific grant name |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "SnapshotCopyGrants": [
        {
            "SnapshotCopyGrantName": "string",
            "KmsKeyId": "string",
            "Tags": [{"Key": "string", "Value": "string"}]
        }
    ],
    "Marker": "string"
}
```
