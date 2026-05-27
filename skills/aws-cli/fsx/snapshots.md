# Snapshots

### 4.1 `create-snapshot`

Creates a snapshot of an ONTAP or OpenZFS volume.

**Synopsis:**
```bash
aws fsx create-snapshot \
    --name <value> \
    --volume-id <value> \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Snapshot name (1-203 chars) |
| `--volume-id` | **Yes** | string | -- | Volume ID (`fsvol-...`) |
| `--tags` | No | list | None | Tags (max 50) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Snapshot": {
        "ResourceARN": "string",
        "SnapshotId": "string",
        "Name": "string",
        "VolumeId": "string",
        "CreationTime": "timestamp",
        "Lifecycle": "PENDING|CREATING|DELETING|AVAILABLE",
        "LifecycleTransitionReason": {
            "Message": "string"
        },
        "Tags": [],
        "AdministrativeActions": []
    }
}
```

---

### 4.2 `describe-snapshots`

Returns descriptions of snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-snapshots \
    [--snapshot-ids <value>] \
    [--filters <value>] \
    [--include-shared | --no-include-shared] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-ids` | No | list | None | Snapshot IDs (max 50) |
| `--filters` | No | list | None | Filters: `file-system-id`, `volume-id` |
| `--include-shared` | No | boolean | false | Include shared snapshots |

**Output Schema:**
```json
{
    "Snapshots": [
        {
            "SnapshotId": "string",
            "Name": "string",
            "VolumeId": "string",
            "CreationTime": "timestamp",
            "Lifecycle": "PENDING|CREATING|DELETING|AVAILABLE",
            "ResourceARN": "string",
            "Tags": [],
            "AdministrativeActions": []
        }
    ],
    "NextToken": "string"
}
```

---

### 4.3 `update-snapshot`

Renames a snapshot.

**Synopsis:**
```bash
aws fsx update-snapshot \
    --snapshot-id <value> \
    --name <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-id` | **Yes** | string | -- | Snapshot ID |
| `--name` | **Yes** | string | -- | New name |

**Output:** Same as `create-snapshot`

---

### 4.4 `delete-snapshot`

Deletes a snapshot.

**Synopsis:**
```bash
aws fsx delete-snapshot \
    --snapshot-id <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-id` | **Yes** | string | -- | Snapshot ID |

**Output Schema:**
```json
{
    "SnapshotId": "string",
    "Lifecycle": "DELETING"
}
```
