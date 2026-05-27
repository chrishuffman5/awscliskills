# Monitoring & Policies

### 12.1 `put-email-monitoring-configuration`

Sets email monitoring configuration to route email events to CloudWatch Logs.

**Synopsis:**
```bash
aws workmail put-email-monitoring-configuration \
    --organization-id <value> \
    --log-group-arn <value> \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--log-group-arn` | **Yes** | string | -- | CloudWatch Log group ARN |
| `--role-arn` | No | string | Service-linked role | IAM role ARN for email monitoring |

**Output:** None

---

### 12.2 `describe-email-monitoring-configuration`

Describes email monitoring configuration for an organization.

**Synopsis:**
```bash
aws workmail describe-email-monitoring-configuration \
    --organization-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |

**Output Schema:**
```json
{
    "RoleArn": "string",
    "LogGroupArn": "string"
}
```

---

### 12.3 `delete-email-monitoring-configuration`

Deletes email monitoring configuration for an organization.

**Synopsis:**
```bash
aws workmail delete-email-monitoring-configuration \
    --organization-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |

**Output:** None

---

### 12.4 `put-retention-policy`

Creates or updates a retention policy with per-folder configurations.

**Synopsis:**
```bash
aws workmail put-retention-policy \
    --organization-id <value> \
    --name <value> \
    --folder-configurations <value> \
    [--id <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--name` | **Yes** | string | -- | Policy name (1-64 chars) |
| `--folder-configurations` | **Yes** | list | -- | Per-folder retention actions |
| `--id` | No | string | None | Policy ID (for updates) |
| `--description` | No | string | None | Policy description (max 256 chars) |

**Folder configuration structure:**
```json
[
    {
        "Name": "INBOX|DELETED_ITEMS|SENT_ITEMS|DRAFTS|JUNK_EMAIL",
        "Action": "NONE|DELETE|PERMANENTLY_DELETE",
        "Period": 30
    }
]
```

**Output:** None

---

### 12.5 `get-default-retention-policy`

Gets the default retention policy for an organization.

**Synopsis:**
```bash
aws workmail get-default-retention-policy \
    --organization-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "FolderConfigurations": [
        {
            "Name": "INBOX|DELETED_ITEMS|SENT_ITEMS|DRAFTS|JUNK_EMAIL",
            "Action": "NONE|DELETE|PERMANENTLY_DELETE",
            "Period": "integer"
        }
    ]
}
```

---

### 12.6 `delete-retention-policy`

Deletes a retention policy.

**Synopsis:**
```bash
aws workmail delete-retention-policy \
    --organization-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--id` | **Yes** | string | -- | Retention policy ID to delete |

**Output:** None
