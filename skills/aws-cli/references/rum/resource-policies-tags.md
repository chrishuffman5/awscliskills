# Resource Policies & Tags

### 3.1 `put-resource-policy`

Creates or updates a resource-based policy for an app monitor, enabling cross-account access.

**Synopsis:**
```bash
aws rum put-resource-policy \
    --name <value> \
    --policy-document <value> \
    [--policy-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--policy-document` | **Yes** | string | -- | JSON resource policy document |
| `--policy-revision-id` | No | string | None | Revision ID for optimistic locking |

**Output Schema:**
```json
{
    "PolicyDocument": "string",
    "PolicyRevisionId": "string"
}
```

---

### 3.2 `get-resource-policy`

Retrieves the resource-based policy for an app monitor.

**Synopsis:**
```bash
aws rum get-resource-policy \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App monitor name (1-255 chars) |

**Output Schema:**
```json
{
    "PolicyDocument": "string",
    "PolicyRevisionId": "string"
}
```

---

### 3.3 `delete-resource-policy`

Deletes the resource-based policy from an app monitor.

**Synopsis:**
```bash
aws rum delete-resource-policy \
    --name <value> \
    [--policy-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--policy-revision-id` | No | string | None | Revision ID for optimistic locking |

**Output:** None

---

### 3.4 `tag-resource`

Assigns tags to a RUM resource.

**Synopsis:**
```bash
aws rum tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Key-value tag pairs (max 50, key: 1-128 chars, value: 0-256 chars) |

**Output:** None

---

### 3.5 `untag-resource`

Removes tags from a RUM resource.

**Synopsis:**
```bash
aws rum untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 3.6 `list-tags-for-resource`

Lists tags for a RUM resource.

**Synopsis:**
```bash
aws rum list-tags-for-resource \
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
    "ResourceArn": "string",
    "Tags": {
        "string": "string"
    }
}
```
