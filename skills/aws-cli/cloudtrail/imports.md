# Imports

### 6.1 `create-import`

Creates an import to copy trail events from an S3 bucket into a CloudTrail Lake event data store. Use this to import historical events.

**Synopsis:**
```bash
aws cloudtrail create-import \
    --destinations <value> \
    --import-source <value> \
    [--start-event-time <value>] \
    [--end-event-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destinations` | **Yes** | list(string) | -- | Event data store ARNs to import into |
| `--import-source` | **Yes** | structure | -- | Source S3 bucket and optional prefix |
| `--start-event-time` | No | timestamp | None | Only import events after this time |
| `--end-event-time` | No | timestamp | None | Only import events before this time |

**Import Source Structure:**
```json
{
    "S3": {
        "S3LocationUri": "s3://bucket-name/optional-prefix/",
        "S3BucketRegion": "us-east-1",
        "S3BucketAccessRoleArn": "arn:aws:iam::123456789012:role/ImportRole"
    }
}
```

**Output Schema:**
```json
{
    "ImportId": "string",
    "Destinations": ["string"],
    "ImportSource": {
        "S3": {
            "S3LocationUri": "string",
            "S3BucketRegion": "string",
            "S3BucketAccessRoleArn": "string"
        }
    },
    "StartEventTime": "timestamp",
    "EndEventTime": "timestamp",
    "ImportStatus": "INITIALIZING|IN_PROGRESS|FAILED|STOPPED|COMPLETED",
    "CreatedTimestamp": "timestamp",
    "UpdatedTimestamp": "timestamp"
}
```

---

### 6.2 `get-import`

Returns details about an import, including status, statistics, and source configuration.

**Synopsis:**
```bash
aws cloudtrail get-import \
    --import-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--import-id` | **Yes** | string | -- | Import ID |

**Output Schema:**
```json
{
    "ImportId": "string",
    "Destinations": ["string"],
    "ImportSource": {
        "S3": {
            "S3LocationUri": "string",
            "S3BucketRegion": "string",
            "S3BucketAccessRoleArn": "string"
        }
    },
    "StartEventTime": "timestamp",
    "EndEventTime": "timestamp",
    "ImportStatus": "INITIALIZING|IN_PROGRESS|FAILED|STOPPED|COMPLETED",
    "CreatedTimestamp": "timestamp",
    "UpdatedTimestamp": "timestamp",
    "ImportStatistics": {
        "PrefixesFound": "long",
        "PrefixesCompleted": "long",
        "FilesCompleted": "long",
        "EventsCompleted": "long",
        "FailedEntries": "long"
    }
}
```

---

### 6.3 `list-imports`

Lists imports in the current account. Optionally filter by destination event data store or import status. **Paginated operation.**

**Synopsis:**
```bash
aws cloudtrail list-imports \
    [--destination <value>] \
    [--import-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination` | No | string | None | Filter by destination event data store ARN |
| `--import-status` | No | string | None | Filter by status: `INITIALIZING`, `IN_PROGRESS`, `FAILED`, `STOPPED`, `COMPLETED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Imports": [
        {
            "ImportId": "string",
            "ImportStatus": "INITIALIZING|IN_PROGRESS|FAILED|STOPPED|COMPLETED",
            "Destinations": ["string"],
            "CreatedTimestamp": "timestamp",
            "UpdatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `start-import`

Starts a new import or restarts a stopped import. When restarting, provide the original `--import-id`.

**Synopsis:**
```bash
aws cloudtrail start-import \
    [--destinations <value>] \
    [--import-source <value>] \
    [--start-event-time <value>] \
    [--end-event-time <value>] \
    [--import-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destinations` | No | list(string) | None | Event data store ARNs (required for new import) |
| `--import-source` | No | structure | None | Source configuration (required for new import) |
| `--start-event-time` | No | timestamp | None | Only import events after this time |
| `--end-event-time` | No | timestamp | None | Only import events before this time |
| `--import-id` | No | string | None | Import ID to restart |

**Output Schema:**
```json
{
    "ImportId": "string",
    "Destinations": ["string"],
    "ImportSource": {
        "S3": {
            "S3LocationUri": "string",
            "S3BucketRegion": "string",
            "S3BucketAccessRoleArn": "string"
        }
    },
    "StartEventTime": "timestamp",
    "EndEventTime": "timestamp",
    "ImportStatus": "INITIALIZING|IN_PROGRESS|FAILED|STOPPED|COMPLETED",
    "CreatedTimestamp": "timestamp",
    "UpdatedTimestamp": "timestamp"
}
```
