# HBase

### 8.1 `schedule-hbase-backup`

Schedules an automatic incremental backup of an HBase cluster. This is a high-level EMR CLI command.

**Synopsis:**
```bash
aws emr schedule-hbase-backup \
    --cluster-id <value> \
    --type <value> \
    --dir <value> \
    --interval <value> \
    --unit <value> \
    [--start-time <value>] \
    [--consistent]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID running HBase |
| `--type` | **Yes** | string | -- | Backup type: `full` or `incremental` |
| `--dir` | **Yes** | string | -- | S3 directory for backup (e.g., `s3://bucket/hbase-backup/`) |
| `--interval` | **Yes** | integer | -- | Backup interval value |
| `--unit` | **Yes** | string | -- | Interval unit: `minutes`, `hours`, `days` |
| `--start-time` | No | string | -- | Start time (ISO 8601) |
| `--consistent` | No | boolean | false | Use consistent backup |

No output on success (submits a step to the cluster).

---

### 8.2 `restore-hbase-backup`

Restores an HBase cluster from a backup. This is a high-level EMR CLI command.

**Synopsis:**
```bash
aws emr restore-hbase-backup \
    --cluster-id <value> \
    --dir <value> \
    --backup-version <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID to restore to |
| `--dir` | **Yes** | string | -- | S3 directory of the backup |
| `--backup-version` | **Yes** | string | -- | Backup version to restore |

No output on success (submits a step to the cluster).
