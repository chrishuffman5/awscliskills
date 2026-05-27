# Notifications & Tags

### 6.1 `put-notification-channel`

Designates the IAM role and Amazon SNS topic for Firewall Manager to use to record SNS logs.

**Synopsis:**
```bash
aws fms put-notification-channel \
    --sns-topic-arn <value> \
    --sns-role-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sns-topic-arn` | **Yes** | string | -- | ARN of the SNS topic to receive notifications |
| `--sns-role-name` | **Yes** | string | -- | ARN of the IAM role to publish to the SNS topic |

**Output Schema:** Empty on success.

---

### 6.2 `get-notification-channel`

Returns the SNS topic and IAM role used for notifications.

**Synopsis:**
```bash
aws fms get-notification-channel \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "SnsTopicArn": "string",
    "SnsRoleName": "string"
}
```

---

### 6.3 `delete-notification-channel`

Deletes the Firewall Manager notification channel.

**Synopsis:**
```bash
aws fms delete-notification-channel \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:** Empty on success.

---

### 6.4 `tag-resource`

Adds tags to a Firewall Manager resource.

**Synopsis:**
```bash
aws fms tag-resource \
    --resource-arn <value> \
    --tag-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tag-list` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` (max 200 tags, keys 1-128 chars, values 0-256 chars) |

**Output Schema:** Empty on success.

---

### 6.5 `untag-resource`

Removes tags from a Firewall Manager resource.

**Synopsis:**
```bash
aws fms untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:** Empty on success.

---

### 6.6 `list-tags-for-resource`

Lists the tags on a Firewall Manager resource.

**Synopsis:**
```bash
aws fms list-tags-for-resource \
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
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
