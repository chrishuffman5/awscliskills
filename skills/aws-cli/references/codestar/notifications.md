# Notifications

### 5.1 `create-notification-rule`

Creates a notification rule for a resource (CodeCommit repository, CodeBuild project, CodePipeline pipeline, etc.).

**Synopsis:**
```bash
aws codestar-notifications create-notification-rule \
    --name <value> \
    --event-type-ids <value> \
    --resource <value> \
    --targets <value> \
    --detail-type <value> \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the notification rule (1-64 chars) |
| `--event-type-ids` | **Yes** | list(string) | -- | Event type IDs to trigger notifications (e.g., `codecommit-repository-comments-on-commits`) |
| `--resource` | **Yes** | string | -- | ARN of the resource to monitor |
| `--targets` | **Yes** | list | -- | Notification targets. Shorthand: `TargetType=SNS,TargetAddress=arn:aws:sns:... ...` |
| `--detail-type` | **Yes** | string | -- | Detail level: `BASIC`, `FULL` |
| `--client-request-token` | No | string | Auto-generated | Idempotency token |
| `--tags` | No | map | None | Tags. JSON: `{"key":"value"}` |
| `--status` | No | string | `ENABLED` | Rule status: `ENABLED`, `DISABLED` |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 5.2 `delete-notification-rule`

Deletes a notification rule.

**Synopsis:**
```bash
aws codestar-notifications delete-notification-rule \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the notification rule to delete |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 5.3 `describe-notification-rule`

Returns details of a notification rule.

**Synopsis:**
```bash
aws codestar-notifications describe-notification-rule \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the notification rule |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "EventTypes": [
        {
            "EventTypeId": "string",
            "ServiceName": "string",
            "EventTypeName": "string",
            "ResourceType": "string"
        }
    ],
    "Resource": "string",
    "Targets": [
        {
            "TargetAddress": "string",
            "TargetType": "SNS|AWSChatbotSlack|AWSChatbotMicrosoftTeams",
            "TargetStatus": "PENDING|ACTIVE|UNREACHABLE|INACTIVE|DEACTIVATED"
        }
    ],
    "DetailType": "BASIC|FULL",
    "CreatedBy": "string",
    "Status": "ENABLED|DISABLED",
    "CreatedTimestamp": "timestamp",
    "LastModifiedTimestamp": "timestamp",
    "Tags": {
        "string": "string"
    }
}
```

---

### 5.4 `list-notification-rules`

Lists notification rules in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codestar-notifications list-notification-rules \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=EVENT_TYPE_ID\|CREATED_BY\|RESOURCE\|TARGET_ADDRESS,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "NotificationRules": [
        {
            "Id": "string",
            "Arn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `update-notification-rule`

Updates a notification rule.

**Synopsis:**
```bash
aws codestar-notifications update-notification-rule \
    --arn <value> \
    [--name <value>] \
    [--status <value>] \
    [--event-type-ids <value>] \
    [--targets <value>] \
    [--detail-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the notification rule to update |
| `--name` | No | string | None | Updated name |
| `--status` | No | string | None | Updated status: `ENABLED`, `DISABLED` |
| `--event-type-ids` | No | list(string) | None | Updated event type IDs |
| `--targets` | No | list | None | Updated targets |
| `--detail-type` | No | string | None | Updated detail type: `BASIC`, `FULL` |

**Output Schema:**
```json
{}
```

---

### 5.6 `list-event-types`

Lists available notification event types. **Paginated operation.**

**Synopsis:**
```bash
aws codestar-notifications list-event-types \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=RESOURCE_TYPE\|SERVICE_NAME,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EventTypes": [
        {
            "EventTypeId": "string",
            "ServiceName": "string",
            "EventTypeName": "string",
            "ResourceType": "string"
        }
    ],
    "NextToken": "string"
}
```
