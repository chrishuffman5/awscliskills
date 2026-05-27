# Report Groups

### 4.1 `create-report-group`

Creates a report group.

**Synopsis:**
```bash
aws codebuild create-report-group \
    --name <value> \
    --type <value> \
    --export-config <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Report group name |
| `--type` | **Yes** | string | -- | Report type: `TEST`, `CODE_COVERAGE` |
| `--export-config` | **Yes** | structure | -- | Export configuration |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |

**Export Config Structure:**
```json
{
    "exportConfigType": "S3|NO_EXPORT",
    "s3Destination": {
        "bucket": "string",
        "bucketOwner": "string",
        "path": "string",
        "packaging": "ZIP|NONE",
        "encryptionKey": "string",
        "encryptionDisabled": true|false
    }
}
```

**Output Schema:**
```json
{
    "reportGroup": {
        "arn": "string",
        "name": "string",
        "type": "TEST|CODE_COVERAGE",
        "exportConfig": {
            "exportConfigType": "S3|NO_EXPORT",
            "s3Destination": {
                "bucket": "string",
                "bucketOwner": "string",
                "path": "string",
                "packaging": "ZIP|NONE",
                "encryptionKey": "string",
                "encryptionDisabled": true|false
            }
        },
        "created": "timestamp",
        "lastModified": "timestamp",
        "tags": [],
        "status": "ACTIVE|DELETING"
    }
}
```

---

### 4.2 `delete-report-group`

Deletes a report group. Before deleting, you must delete its reports or set `--delete-reports`.

**Synopsis:**
```bash
aws codebuild delete-report-group \
    --arn <value> \
    [--delete-reports | --no-delete-reports] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Report group ARN |
| `--delete-reports` | No | boolean | false | Also delete all reports in the group |

**Output Schema:**
```json
{}
```

---

### 4.3 `batch-get-report-groups`

Returns information about one or more report groups.

**Synopsis:**
```bash
aws codebuild batch-get-report-groups \
    --report-group-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-group-arns` | **Yes** | list(string) | -- | Report group ARNs (max 100) |

**Output Schema:**
```json
{
    "reportGroups": [
        {
            "arn": "string",
            "name": "string",
            "type": "TEST|CODE_COVERAGE",
            "exportConfig": { },
            "created": "timestamp",
            "lastModified": "timestamp",
            "tags": [],
            "status": "ACTIVE|DELETING"
        }
    ],
    "reportGroupsNotFound": ["string"]
}
```

---

### 4.4 `list-report-groups`

Gets a list of report group ARNs. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-report-groups \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | string | `NAME` | Sort criterion: `NAME`, `CREATED_TIME`, `LAST_MODIFIED_TIME` |
| `--sort-order` | No | string | `ASCENDING` | Sort order: `ASCENDING`, `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "reportGroups": ["string"],
    "nextToken": "string"
}
```

---

### 4.5 `update-report-group`

Updates a report group.

**Synopsis:**
```bash
aws codebuild update-report-group \
    --arn <value> \
    [--export-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Report group ARN |
| `--export-config` | No | structure | None | Updated export configuration |
| `--tags` | No | list | None | Updated tags |

**Output Schema:**
Same as `create-report-group`.
