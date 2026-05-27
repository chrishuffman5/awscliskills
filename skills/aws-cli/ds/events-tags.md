# Events & Tags

### 12.1 `register-event-topic`

Registers an SNS topic to receive directory event notifications.

**Synopsis:**
```bash
aws ds register-event-topic \
    --directory-id <value> \
    --topic-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--topic-name` | **Yes** | string | -- | SNS topic name to register |

**Output Schema:**

No output on success (HTTP 200).

---

### 12.2 `deregister-event-topic`

Removes a directory event notification from an SNS topic.

**Synopsis:**
```bash
aws ds deregister-event-topic \
    --directory-id <value> \
    --topic-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--topic-name` | **Yes** | string | -- | SNS topic name to deregister |

**Output Schema:**

No output on success (HTTP 200).

---

### 12.3 `describe-event-topics`

Describes the event topics for a directory.

**Synopsis:**
```bash
aws ds describe-event-topics \
    [--directory-id <value>] \
    [--topic-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | No | string | None | Filter by directory ID |
| `--topic-names` | No | list(string) | None | Filter by topic names |

**Output Schema:**
```json
{
    "EventTopics": [
        {
            "DirectoryId": "string",
            "TopicName": "string",
            "TopicArn": "string",
            "CreatedDateTime": "timestamp",
            "Status": "Registered|Topic not found|Failed|Delete failed|Deleted"
        }
    ]
}
```

---

### 12.4 `add-tags-to-resource`

Adds tags to a directory.

**Synopsis:**
```bash
aws ds add-tags-to-resource \
    --resource-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Directory ID to tag |
| `--tags` | **Yes** | list(structure) | -- | Tags. Structure: `Key=string,Value=string` |

**Output Schema:**

No output on success (HTTP 200).

---

### 12.5 `remove-tags-from-resource`

Removes tags from a directory.

**Synopsis:**
```bash
aws ds remove-tags-from-resource \
    --resource-id <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Directory ID |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

No output on success (HTTP 200).

---

### 12.6 `list-tags-for-resource`

Lists all tags for a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds list-tags-for-resource \
    --resource-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Directory ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 12.7 `create-log-subscription`

Creates a CloudWatch Logs log subscription for directory security logs.

**Synopsis:**
```bash
aws ds create-log-subscription \
    --directory-id <value> \
    --log-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--log-group-name` | **Yes** | string | -- | CloudWatch Logs log group name (must already exist) |

**Output Schema:**

No output on success (HTTP 200).

---

### 12.8 `delete-log-subscription`

Deletes a CloudWatch Logs log subscription.

**Synopsis:**
```bash
aws ds delete-log-subscription \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**

No output on success (HTTP 200).

---

### 12.9 `list-log-subscriptions`

Lists all log subscriptions for a directory or all directories. **Paginated operation.**

**Synopsis:**
```bash
aws ds list-log-subscriptions \
    [--directory-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | No | string | All | Filter by directory ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LogSubscriptions": [
        {
            "DirectoryId": "string",
            "LogGroupName": "string",
            "SubscriptionCreatedDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 12.10 `start-schema-extension`

Applies a schema extension to a Managed Microsoft AD directory.

**Synopsis:**
```bash
aws ds start-schema-extension \
    --directory-id <value> \
    --create-snapshot-before-schema-extension | --no-create-snapshot-before-schema-extension \
    --ldif-content <value> \
    --description <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--create-snapshot-before-schema-extension` | **Yes** | boolean | -- | Create snapshot before applying extension |
| `--ldif-content` | **Yes** | string | -- | LDIF content for the schema extension |
| `--description` | **Yes** | string | -- | Description of the extension |

**Output Schema:**
```json
{
    "SchemaExtensionId": "string"
}
```

---

### 12.11 `cancel-schema-extension`

Cancels a directory schema extension.

**Synopsis:**
```bash
aws ds cancel-schema-extension \
    --directory-id <value> \
    --schema-extension-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--schema-extension-id` | **Yes** | string | -- | Schema extension ID to cancel |

**Output Schema:**

No output on success (HTTP 200).

---

### 12.12 `list-schema-extensions`

Lists all schema extensions applied to a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds list-schema-extensions \
    --directory-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SchemaExtensionsInfo": [
        {
            "DirectoryId": "string",
            "SchemaExtensionId": "string",
            "Description": "string",
            "SchemaExtensionStatus": "Initializing|CreatingSnapshot|UpdatingSchema|Replicating|CancelInProgress|RollbackInProgress|Cancelled|Failed|Completed",
            "SchemaExtensionStatusReason": "string",
            "StartDateTime": "timestamp",
            "EndDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
