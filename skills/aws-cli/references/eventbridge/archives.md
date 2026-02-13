# Archives

### 4.1 `create-archive`

Creates an archive of events from an event bus. Archived events can be replayed later.

**Synopsis:**
```bash
aws events create-archive \
    --archive-name <value> \
    --event-source-arn <value> \
    [--description <value>] \
    [--event-pattern <value>] \
    [--retention-days <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--archive-name` | **Yes** | string | -- | Name of the archive |
| `--event-source-arn` | **Yes** | string | -- | ARN of the event bus to archive from |
| `--description` | No | string | None | Description of the archive |
| `--event-pattern` | No | string | None | JSON event pattern to filter which events are archived |
| `--retention-days` | No | integer | 0 (unlimited) | Number of days to retain events (0 = indefinite) |

**Output Schema:**
```json
{
    "ArchiveArn": "string",
    "State": "ENABLED|DISABLED|CREATING|UPDATING|CREATE_FAILED|UPDATE_FAILED",
    "StateReason": "string",
    "CreationTime": "timestamp"
}
```

---

### 4.2 `delete-archive`

Deletes an archive.

**Synopsis:**
```bash
aws events delete-archive \
    --archive-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--archive-name` | **Yes** | string | -- | Name of the archive to delete |

**Output Schema:**
```json
{}
```

---

### 4.3 `describe-archive`

Retrieves details about an archive.

**Synopsis:**
```bash
aws events describe-archive \
    --archive-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--archive-name` | **Yes** | string | -- | Name of the archive |

**Output Schema:**
```json
{
    "ArchiveArn": "string",
    "ArchiveName": "string",
    "EventSourceArn": "string",
    "Description": "string",
    "EventPattern": "string",
    "State": "ENABLED|DISABLED|CREATING|UPDATING|CREATE_FAILED|UPDATE_FAILED",
    "StateReason": "string",
    "RetentionDays": "integer",
    "SizeBytes": "long",
    "EventCount": "long",
    "CreationTime": "timestamp"
}
```

---

### 4.4 `list-archives`

Lists all archives. Supports filtering by name prefix, source ARN, or state. **Paginated operation.**

**Synopsis:**
```bash
aws events list-archives \
    [--name-prefix <value>] \
    [--event-source-arn <value>] \
    [--state <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by archive name prefix |
| `--event-source-arn` | No | string | None | Filter by event source ARN |
| `--state` | No | string | None | Filter by state: `ENABLED`, `DISABLED`, `CREATING`, `UPDATING`, `CREATE_FAILED`, `UPDATE_FAILED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Archives": [
        {
            "ArchiveName": "string",
            "EventSourceArn": "string",
            "State": "ENABLED|DISABLED|CREATING|UPDATING|CREATE_FAILED|UPDATE_FAILED",
            "StateReason": "string",
            "RetentionDays": "integer",
            "SizeBytes": "long",
            "EventCount": "long",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-archive`

Updates the specified archive.

**Synopsis:**
```bash
aws events update-archive \
    --archive-name <value> \
    [--description <value>] \
    [--event-pattern <value>] \
    [--retention-days <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--archive-name` | **Yes** | string | -- | Name of the archive to update |
| `--description` | No | string | None | Updated description |
| `--event-pattern` | No | string | None | Updated event pattern filter |
| `--retention-days` | No | integer | None | Updated retention period (0 = indefinite) |

**Output Schema:**
```json
{
    "ArchiveArn": "string",
    "State": "ENABLED|DISABLED|CREATING|UPDATING|CREATE_FAILED|UPDATE_FAILED",
    "StateReason": "string",
    "CreationTime": "timestamp"
}
```
