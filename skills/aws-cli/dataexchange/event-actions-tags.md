# Event Actions & Tags

## 5.1 `create-event-action`

Creates an event action that automatically runs when a specific event occurs (e.g., new revision published).

**Synopsis:**
```bash
aws dataexchange create-event-action \
    --action <value> \
    --event <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action` | **Yes** | structure | -- | Action to perform when the event fires |
| `--event` | **Yes** | structure | -- | Event that triggers the action |

**Event Structure (Revision Published):**
```json
{
    "RevisionPublished": {
        "DataSetId": "string"
    }
}
```

**Action Structure (Export to S3):**
```json
{
    "ExportRevisionToS3": {
        "RevisionDestination": {
            "Bucket": "export-bucket",
            "KeyPattern": "${Revision.CreatedAt}/${Asset.Name}"
        },
        "Encryption": {
            "Type": "AES256"
        }
    }
}
```

**Output Schema:**
```json
{
    "Action": {
        "ExportRevisionToS3": {
            "Encryption": {
                "KmsKeyArn": "string",
                "Type": "aws:kms|AES256"
            },
            "RevisionDestination": {
                "Bucket": "string",
                "KeyPattern": "string"
            }
        }
    },
    "Arn": "string",
    "CreatedAt": "timestamp",
    "Event": {
        "RevisionPublished": {
            "DataSetId": "string"
        }
    },
    "Id": "string",
    "UpdatedAt": "timestamp"
}
```

---

## 5.2 `get-event-action`

Returns details for an event action.

**Synopsis:**
```bash
aws dataexchange get-event-action \
    --event-action-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-action-id` | **Yes** | string | -- | Event action ID |

**Output Schema:**
```json
{
    "Action": {
        "ExportRevisionToS3": {
            "Encryption": {},
            "RevisionDestination": {}
        }
    },
    "Arn": "string",
    "CreatedAt": "timestamp",
    "Event": {
        "RevisionPublished": {
            "DataSetId": "string"
        }
    },
    "Id": "string",
    "UpdatedAt": "timestamp"
}
```

---

## 5.3 `list-event-actions`

Lists event actions. **Paginated operation.**

**Synopsis:**
```bash
aws dataexchange list-event-actions \
    [--event-source-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-source-id` | No | string | None | Filter by event source (data set ID) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EventActions": [
        {
            "Action": {},
            "Arn": "string",
            "CreatedAt": "timestamp",
            "Event": {},
            "Id": "string",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 5.4 `update-event-action`

Updates an event action.

**Synopsis:**
```bash
aws dataexchange update-event-action \
    --event-action-id <value> \
    [--action <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-action-id` | **Yes** | string | -- | Event action ID |
| `--action` | No | structure | None | Updated action configuration |

**Output Schema:**
```json
{
    "Action": {},
    "Arn": "string",
    "CreatedAt": "timestamp",
    "Event": {},
    "Id": "string",
    "UpdatedAt": "timestamp"
}
```

---

## 5.5 `delete-event-action`

Deletes an event action.

**Synopsis:**
```bash
aws dataexchange delete-event-action \
    --event-action-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-action-id` | **Yes** | string | -- | Event action ID to delete |

**Output Schema:**

None (HTTP 204 on success).

---

## 5.6 `tag-resource`

Adds tags to a Data Exchange resource.

**Synopsis:**
```bash
aws dataexchange tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | map | -- | Key-value tags to add |

**Output Schema:**

None (HTTP 204 on success).

---

## 5.7 `untag-resource`

Removes tags from a Data Exchange resource.

**Synopsis:**
```bash
aws dataexchange untag-resource \
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

**Output Schema:**

None (HTTP 204 on success).

---

## 5.8 `list-tags-for-resource`

Lists tags for a Data Exchange resource.

**Synopsis:**
```bash
aws dataexchange list-tags-for-resource \
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
    "Tags": {
        "string": "string"
    }
}
```
