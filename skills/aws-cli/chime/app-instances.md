# App Instances

CLI namespace: `aws chime-sdk-identity`

### 1.1 `create-app-instance`

Creates an AppInstance. Only SDK messaging customers use this API.

**Synopsis:**
```bash
aws chime-sdk-identity create-app-instance \
    --name <value> \
    [--metadata <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App instance name (1-256 chars) |
| `--metadata` | No | string | None | Metadata (0-1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token (2-64 chars) |
| `--tags` | No | list | None | Tags (1-50) |

**Output Schema:**
```json
{
    "AppInstanceArn": "string"
}
```

---

### 1.2 `describe-app-instance`

Describes an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-identity describe-app-instance \
    --app-instance-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output Schema:**
```json
{
    "AppInstance": {
        "AppInstanceArn": "string",
        "Name": "string",
        "Metadata": "string",
        "CreatedTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp"
    }
}
```

---

### 1.3 `list-app-instances`

Lists all AppInstances. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-identity list-app-instances \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "AppInstances": [
        {
            "AppInstanceArn": "string",
            "Name": "string",
            "Metadata": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-app-instance`

Updates an AppInstance name and metadata.

**Synopsis:**
```bash
aws chime-sdk-identity update-app-instance \
    --app-instance-arn <value> \
    --name <value> \
    --metadata <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--name` | **Yes** | string | -- | Updated name (1-256 chars) |
| `--metadata` | **Yes** | string | -- | Updated metadata (0-1024 chars) |

**Output Schema:**
```json
{
    "AppInstanceArn": "string"
}
```

---

### 1.5 `delete-app-instance`

Deletes an AppInstance and all associated data.

**Synopsis:**
```bash
aws chime-sdk-identity delete-app-instance \
    --app-instance-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output:** None

---

### 1.6 `get-app-instance-retention-settings`

Gets the retention settings for an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-identity get-app-instance-retention-settings \
    --app-instance-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output Schema:**
```json
{
    "AppInstanceRetentionSettings": {
        "ChannelRetentionSettings": {
            "RetentionDays": "integer"
        }
    },
    "InitiateDeletionTimestamp": "timestamp"
}
```

---

### 1.7 `put-app-instance-retention-settings`

Sets the retention settings for an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-identity put-app-instance-retention-settings \
    --app-instance-arn <value> \
    --app-instance-retention-settings <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--app-instance-retention-settings` | **Yes** | structure | -- | Retention settings |

**RetentionSettings structure:**
```json
{
    "ChannelRetentionSettings": {
        "RetentionDays": 30
    }
}
```

`RetentionDays` range: 1-5475 (about 15 years).

**Output Schema:**
```json
{
    "AppInstanceRetentionSettings": {
        "ChannelRetentionSettings": {
            "RetentionDays": "integer"
        }
    },
    "InitiateDeletionTimestamp": "timestamp"
}
```
