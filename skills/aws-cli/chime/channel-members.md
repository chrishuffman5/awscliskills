# Channel Members & Moderators

CLI namespace: `aws chime-sdk-messaging`

All commands require `--chime-bearer`.

### 7.1 `create-channel-membership`

Adds a member to a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel-membership \
    --channel-arn <value> \
    --member-arn <value> \
    --type <value> \
    --chime-bearer <value> \
    [--sub-channel-id <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | Member ARN |
| `--type` | **Yes** | string | -- | `DEFAULT` or `HIDDEN` |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--sub-channel-id` | No | string | None | Sub-channel ID for elastic channels |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "Member": {"Arn": "string", "Name": "string"},
    "SubChannelId": "string"
}
```

---

### 7.2 `batch-create-channel-membership`

Adds up to 100 members to a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging batch-create-channel-membership \
    --channel-arn <value> \
    --member-arns <value> \
    --chime-bearer <value> \
    [--type <value>] \
    [--sub-channel-id <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arns` | **Yes** | list | -- | Member ARNs (1-100) |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--type` | No | string | None | `DEFAULT` or `HIDDEN` |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "BatchChannelMemberships": {
        "InvitedBy": {},
        "Type": "string",
        "Members": [],
        "ChannelArn": "string",
        "SubChannelId": "string"
    },
    "Errors": [{"MemberArn": "string", "ErrorCode": "string", "ErrorMessage": "string"}]
}
```

---

### 7.3 `describe-channel-membership` / `list-channel-memberships`

Get or list memberships. List is paginated.

**Synopsis:**
```bash
aws chime-sdk-messaging describe-channel-membership \
    --channel-arn <value> --member-arn <value> --chime-bearer <value> [--sub-channel-id <value>]

aws chime-sdk-messaging list-channel-memberships \
    --channel-arn <value> --chime-bearer <value> [--type <value>] [--max-results <value>] [--next-token <value>] [--sub-channel-id <value>]
```

---

### 7.4 `delete-channel-membership`

Removes a member from a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging delete-channel-membership \
    --channel-arn <value> --member-arn <value> --chime-bearer <value> [--sub-channel-id <value>]
```

**Output:** None

---

### 7.5 `list-channel-memberships-for-app-instance-user`

Lists all channels an AppInstanceUser is a member of. **Paginated.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-channel-memberships-for-app-instance-user \
    --chime-bearer <value> [--app-instance-user-arn <value>] [--max-results <value>] [--next-token <value>]
```

---

### 7.6 `get-channel-membership-preferences` / `put-channel-membership-preferences`

Get or set notification preferences for a channel member.

**Synopsis:**
```bash
aws chime-sdk-messaging get-channel-membership-preferences \
    --channel-arn <value> --member-arn <value> --chime-bearer <value>

aws chime-sdk-messaging put-channel-membership-preferences \
    --channel-arn <value> --member-arn <value> --chime-bearer <value> \
    --preferences '{"PushNotifications":{"FilterRule":"string","AllowNotifications":"ALL|NONE|FILTERED"}}'
```

---

### 7.7 `create-channel-moderator`

Designates a channel moderator.

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel-moderator \
    --channel-arn <value> \
    --channel-moderator-arn <value> \
    --chime-bearer <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--channel-moderator-arn` | **Yes** | string | -- | Moderator user ARN |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ChannelModerator": {"Arn": "string", "Name": "string"}
}
```

---

### 7.8 `describe-channel-moderator` / `list-channel-moderators` / `delete-channel-moderator`

Describe, list, or delete channel moderators. List is paginated.

**Synopsis:**
```bash
aws chime-sdk-messaging describe-channel-moderator \
    --channel-arn <value> --channel-moderator-arn <value> --chime-bearer <value>

aws chime-sdk-messaging list-channel-moderators \
    --channel-arn <value> --chime-bearer <value> [--max-results <value>] [--next-token <value>]

aws chime-sdk-messaging delete-channel-moderator \
    --channel-arn <value> --channel-moderator-arn <value> --chime-bearer <value>
```

---

### 7.9 `create-channel-ban` / `describe-channel-ban` / `list-channel-bans` / `delete-channel-ban`

Manage channel bans. List is paginated.

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel-ban \
    --channel-arn <value> --member-arn <value> --chime-bearer <value>

aws chime-sdk-messaging describe-channel-ban \
    --channel-arn <value> --member-arn <value> --chime-bearer <value>

aws chime-sdk-messaging list-channel-bans \
    --channel-arn <value> --chime-bearer <value> [--max-results <value>] [--next-token <value>]

aws chime-sdk-messaging delete-channel-ban \
    --channel-arn <value> --member-arn <value> --chime-bearer <value>
```
