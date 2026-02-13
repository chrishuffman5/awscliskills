# Snapshots

### 5.1 `create-snapshot`

Creates a snapshot of a directory.

**Synopsis:**
```bash
aws ds create-snapshot \
    --directory-id <value> \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--name` | No | string | None | Descriptive name for the snapshot |

**Output Schema:**
```json
{
    "SnapshotId": "string"
}
```

---

### 5.2 `delete-snapshot`

Deletes a directory snapshot.

**Synopsis:**
```bash
aws ds delete-snapshot \
    --snapshot-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-id` | **Yes** | string | -- | Snapshot ID to delete (pattern: `s-[0-9a-f]{10}`) |

**Output Schema:**
```json
{
    "SnapshotId": "string"
}
```

---

### 5.3 `describe-snapshots`

Describes directory snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-snapshots \
    [--directory-id <value>] \
    [--snapshot-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | No | string | None | Filter by directory ID |
| `--snapshot-ids` | No | list(string) | None | Filter by snapshot IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Snapshots": [
        {
            "DirectoryId": "string",
            "SnapshotId": "string",
            "Type": "Auto|Manual",
            "Name": "string",
            "Status": "Creating|Completed|Failed",
            "StartTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `restore-from-snapshot`

Restores a directory using an existing snapshot.

**Synopsis:**
```bash
aws ds restore-from-snapshot \
    --snapshot-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-id` | **Yes** | string | -- | Snapshot ID to restore from |

**Output Schema:**

No output on success (HTTP 200).

---

### 5.5 `get-snapshot-limits`

Gets the snapshot limits for a directory.

**Synopsis:**
```bash
aws ds get-snapshot-limits \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**
```json
{
    "SnapshotLimits": {
        "ManualSnapshotsLimit": "integer",
        "ManualSnapshotsCurrentCount": "integer",
        "ManualSnapshotsLimitReached": "boolean"
    }
}
```
