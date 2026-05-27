# Channel Groups

### 1.1 `create-channel-group`

Creates a channel group to organize channels for content distribution.

**Synopsis:**
```bash
aws mediapackagev2 create-channel-group \
    --channel-group-name <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Unique name for the channel group (1-256 chars, `[a-zA-Z0-9_-]+`) |
| `--client-token` | No | string | Auto | Idempotency token (1-256 chars) |
| `--description` | No | string | None | Descriptive text (0-1024 chars) |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "ChannelGroupName": "string",
    "Arn": "string",
    "EgressDomain": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "ETag": "string",
    "Description": "string",
    "Tags": {"string": "string"}
}
```

---

### 1.2 `get-channel-group`

Retrieves details for a channel group.

**Synopsis:**
```bash
aws mediapackagev2 get-channel-group \
    --channel-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |

**Output Schema:**
```json
{
    "ChannelGroupName": "string",
    "Arn": "string",
    "EgressDomain": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "ETag": "string",
    "Description": "string",
    "Tags": {"string": "string"}
}
```

---

### 1.3 `list-channel-groups`

Lists all channel groups in the account. **Paginated operation.**

**Synopsis:**
```bash
aws mediapackagev2 list-channel-groups \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Number of items per API call |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "Items": [
        {
            "ChannelGroupName": "string",
            "Arn": "string",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-channel-group`

Updates a channel group's description.

**Synopsis:**
```bash
aws mediapackagev2 update-channel-group \
    --channel-group-name <value> \
    [--e-tag <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--e-tag` | No | string | None | Expected ETag for concurrent update safety |
| `--description` | No | string | None | Updated description (0-1024 chars) |

**Output Schema:**
```json
{
    "ChannelGroupName": "string",
    "Arn": "string",
    "EgressDomain": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "ETag": "string",
    "Description": "string",
    "Tags": {"string": "string"}
}
```

---

### 1.5 `delete-channel-group`

Deletes a channel group. All channels and endpoints within must be deleted first.

**Synopsis:**
```bash
aws mediapackagev2 delete-channel-group \
    --channel-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group to delete |

**Output:** None
