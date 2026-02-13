# Analytics Config

### 8.1 `add-application-cloud-watch-logging-option`

Adds a CloudWatch log stream to monitor an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 add-application-cloud-watch-logging-option \
    --application-name <value> \
    --cloud-watch-logging-option <value> \
    [--current-application-version-id <value>] \
    [--conditional-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--cloud-watch-logging-option` | **Yes** | structure | -- | CloudWatch config. Shorthand: `LogStreamARN=string` |
| `--current-application-version-id` | No | long | -- | Current application version ID |
| `--conditional-token` | No | string | -- | Conditional update token |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long",
    "CloudWatchLoggingOptionDescriptions": [
        {
            "CloudWatchLoggingOptionId": "string",
            "LogStreamARN": "string",
            "RoleARN": "string"
        }
    ]
}
```

---

### 8.2 `delete-application-cloud-watch-logging-option`

Removes a CloudWatch log stream from an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 delete-application-cloud-watch-logging-option \
    --application-name <value> \
    --cloud-watch-logging-option-id <value> \
    [--current-application-version-id <value>] \
    [--conditional-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--cloud-watch-logging-option-id` | **Yes** | string | -- | ID of the CloudWatch logging option to remove |
| `--current-application-version-id` | No | long | -- | Current application version ID |
| `--conditional-token` | No | string | -- | Conditional update token |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long",
    "CloudWatchLoggingOptionDescriptions": []
}
```

---

### 8.3 `create-application-snapshot`

Creates a snapshot of an analytics application's state.

**Synopsis:**
```bash
aws kinesisanalyticsv2 create-application-snapshot \
    --application-name <value> \
    --snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--snapshot-name` | **Yes** | string | -- | Snapshot name (1-256 chars, pattern: `[a-zA-Z0-9_.-]+`) |

**Output:** None

---

### 8.4 `delete-application-snapshot`

Deletes a snapshot of an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 delete-application-snapshot \
    --application-name <value> \
    --snapshot-name <value> \
    --snapshot-creation-timestamp <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--snapshot-name` | **Yes** | string | -- | Name of the snapshot to delete |
| `--snapshot-creation-timestamp` | **Yes** | timestamp | -- | Creation timestamp of the snapshot |

**Output:** None

---

### 8.5 `describe-application-snapshot`

Describes a snapshot of an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 describe-application-snapshot \
    --application-name <value> \
    --snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--snapshot-name` | **Yes** | string | -- | Name of the snapshot |

**Output Schema:**
```json
{
    "SnapshotDetails": {
        "SnapshotName": "string",
        "SnapshotStatus": "CREATING|READY|DELETING|FAILED",
        "ApplicationVersionId": "long",
        "SnapshotCreationTimestamp": "timestamp",
        "RuntimeEnvironment": "string"
    }
}
```

---

### 8.6 `list-application-snapshots`

Lists snapshots for an analytics application. **Paginated operation.**

**Synopsis:**
```bash
aws kinesisanalyticsv2 list-application-snapshots \
    --application-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SnapshotSummaries": [
        {
            "SnapshotName": "string",
            "SnapshotStatus": "CREATING|READY|DELETING|FAILED",
            "ApplicationVersionId": "long",
            "SnapshotCreationTimestamp": "timestamp",
            "RuntimeEnvironment": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.7 `create-application-presigned-url`

Creates a presigned URL for accessing the Flink dashboard or Zeppelin notebook.

**Synopsis:**
```bash
aws kinesisanalyticsv2 create-application-presigned-url \
    --application-name <value> \
    --url-type <value> \
    [--session-expiration-duration-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--url-type` | **Yes** | string | -- | URL type: `FLINK_DASHBOARD_URL` or `ZEPPELIN_UI_URL` |
| `--session-expiration-duration-in-seconds` | No | long | 1800 | Session expiration (min 1800) |

**Output Schema:**
```json
{
    "AuthorizedUrl": "string"
}
```

---

### 8.8 `update-application-maintenance-configuration`

Updates the maintenance configuration for a Flink application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 update-application-maintenance-configuration \
    --application-name <value> \
    --application-maintenance-configuration-update <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--application-maintenance-configuration-update` | **Yes** | structure | -- | Maintenance config. Shorthand: `ApplicationMaintenanceWindowStartTimeUpdate=string` |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationMaintenanceConfigurationDescription": {
        "ApplicationMaintenanceWindowStartTime": "string",
        "ApplicationMaintenanceWindowEndTime": "string"
    }
}
```

---

### 8.9 `tag-resource` (kinesisanalyticsv2)

Adds tags to an analytics application resource.

**Synopsis:**
```bash
aws kinesisanalyticsv2 tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 8.10 `untag-resource` (kinesisanalyticsv2)

Removes tags from an analytics application resource.

**Synopsis:**
```bash
aws kinesisanalyticsv2 untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 8.11 `list-tags-for-resource` (kinesisanalyticsv2)

Lists tags for an analytics application resource.

**Synopsis:**
```bash
aws kinesisanalyticsv2 list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
