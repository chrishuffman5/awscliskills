# Channel Memberships

Commands from the `aws chime-sdk-messaging` service.

### 7.1 `create-channel-membership`

Adds a member to a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel-membership \
    --channel-arn <value> \
    --member-arn <value> \
    --type <value> \
    --chime-bearer <value> \
    [--sub-channel-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | ARN of the member to add |
| `--type` | **Yes** | string | -- | `DEFAULT` or `HIDDEN` |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sub-channel-id` | No | string | None | Sub-channel ID for elastic channels |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "Member": {
        "Arn": "string",
        "Name": "string"
    },
    "SubChannelId": "string"
}
```

---

### 7.2 `batch-create-channel-membership`

Adds multiple members to a channel in a single call.

**Synopsis:**
```bash
aws chime-sdk-messaging batch-create-channel-membership \
    --channel-arn <value> \
    --member-arns <value> \
    --chime-bearer <value> \
    [--type <value>] \
    [--sub-channel-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arns` | **Yes** | list | -- | Member ARNs (1-100) |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--type` | No | string | None | `DEFAULT` or `HIDDEN` |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "BatchChannelMemberships": {
        "InvitedBy": { "Arn": "string", "Name": "string" },
        "Type": "DEFAULT|HIDDEN",
        "Members": [
            { "Arn": "string", "Name": "string" }
        ],
        "ChannelArn": "string",
        "SubChannelId": "string"
    },
    "Errors": [
        {
            "MemberArn": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 7.3 `describe-channel-membership`

Describes a channel membership.

**Synopsis:**
```bash
aws chime-sdk-messaging describe-channel-membership \
    --channel-arn <value> \
    --member-arn <value> \
    --chime-bearer <value> \
    [--sub-channel-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | Member ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "ChannelMembership": {
        "InvitedBy": { "Arn": "string", "Name": "string" },
        "Type": "DEFAULT|HIDDEN",
        "Member": { "Arn": "string", "Name": "string" },
        "ChannelArn": "string",
        "CreatedTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "SubChannelId": "string"
    }
}
```

---

### 7.4 `list-channel-memberships`

Lists members of a channel. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-channel-memberships \
    --channel-arn <value> \
    --chime-bearer <value> \
    [--type <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--sub-channel-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--type` | No | string | None | `DEFAULT` or `HIDDEN` |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ChannelMemberships": [
        {
            "Member": { "Arn": "string", "Name": "string" },
            "Type": "DEFAULT|HIDDEN"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `delete-channel-membership`

Removes a member from a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging delete-channel-membership \
    --channel-arn <value> \
    --member-arn <value> \
    --chime-bearer <value> \
    [--sub-channel-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | Member ARN to remove |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output:** None

---

### 7.6 `describe-channel-membership-for-app-instance-user`

Describes a channel membership for a specific user.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

---

### 7.7 `list-channel-memberships-for-app-instance-user`

Lists channels a user belongs to. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | No | string | None | User ARN (defaults to chime-bearer) |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

---

### 7.8 `get-channel-membership-preferences`

Gets a member's push notification preferences for a channel.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | Member ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "Member": { "Arn": "string", "Name": "string" },
    "Preferences": {
        "PushNotifications": {
            "AllowNotifications": "ALL|NONE|FILTERED",
            "FilterRule": "string"
        }
    }
}
```

---

### 7.9 `put-channel-membership-preferences`

Sets a member's push notification preferences for a channel.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | Member ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--preferences` | **Yes** | structure | -- | Notification preferences |

**Preferences:**
```json
{
    "PushNotifications": {
        "AllowNotifications": "ALL|NONE|FILTERED (required)",
        "FilterRule": "string (optional)"
    }
}
```

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "Member": { "Arn": "string", "Name": "string" },
    "Preferences": {
        "PushNotifications": {
            "AllowNotifications": "ALL|NONE|FILTERED",
            "FilterRule": "string"
        }
    }
}
```
