# Channel Moderation

Commands from the `aws chime-sdk-messaging` service.

### 10.1 `create-channel-ban`

Bans a user from a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel-ban \
    --channel-arn <value> \
    --member-arn <value> \
    --chime-bearer <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | ARN of the member to ban |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "Member": {
        "Arn": "string",
        "Name": "string"
    }
}
```

---

### 10.2 `describe-channel-ban`

Describes a channel ban.

**Synopsis:**
```bash
aws chime-sdk-messaging describe-channel-ban \
    --channel-arn <value> \
    --member-arn <value> \
    --chime-bearer <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | Banned member ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output Schema:**
```json
{
    "ChannelBan": {
        "Member": { "Arn": "string", "Name": "string" },
        "ChannelArn": "string",
        "CreatedTimestamp": "timestamp",
        "CreatedBy": { "Arn": "string", "Name": "string" }
    }
}
```

---

### 10.3 `list-channel-bans`

Lists channel bans. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-channel-bans \
    --channel-arn <value> \
    --chime-bearer <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ChannelBans": [
        {
            "Member": { "Arn": "string", "Name": "string" }
        }
    ],
    "NextToken": "string"
}
```

---

### 10.4 `delete-channel-ban`

Removes a ban from a channel.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--member-arn` | **Yes** | string | -- | Banned member ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output:** None

---

### 10.5 `create-channel-moderator`

Creates a moderator for a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel-moderator \
    --channel-arn <value> \
    --channel-moderator-arn <value> \
    --chime-bearer <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--channel-moderator-arn` | **Yes** | string | -- | ARN of the user to make moderator |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ChannelModerator": {
        "Arn": "string",
        "Name": "string"
    }
}
```

---

### 10.6 `describe-channel-moderator`

Describes a channel moderator.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--channel-moderator-arn` | **Yes** | string | -- | Moderator ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output Schema:**
```json
{
    "ChannelModerator": {
        "Moderator": { "Arn": "string", "Name": "string" },
        "ChannelArn": "string",
        "CreatedTimestamp": "timestamp",
        "CreatedBy": { "Arn": "string", "Name": "string" }
    }
}
```

---

### 10.7 `list-channel-moderators`

Lists channel moderators. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ChannelModerators": [
        {
            "Moderator": { "Arn": "string", "Name": "string" }
        }
    ],
    "NextToken": "string"
}
```

---

### 10.8 `delete-channel-moderator`

Removes a moderator from a channel.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--channel-moderator-arn` | **Yes** | string | -- | Moderator ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output:** None
