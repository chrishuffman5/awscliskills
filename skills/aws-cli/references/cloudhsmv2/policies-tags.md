# Policies & Tags

### 4.1 `get-resource-policy`

Gets the resource policy for a CloudHSM backup. Used for cross-account backup sharing.

**Synopsis:**
```bash
aws cloudhsmv2 get-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the backup resource |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 4.2 `put-resource-policy`

Creates or updates a resource policy on a CloudHSM backup for cross-account sharing.

**Synopsis:**
```bash
aws cloudhsmv2 put-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the backup resource |
| `--policy` | **Yes** | string | -- | JSON resource policy document |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "Policy": "string"
}
```

---

### 4.3 `delete-resource-policy`

Deletes the resource policy from a CloudHSM backup.

**Synopsis:**
```bash
aws cloudhsmv2 delete-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the backup resource |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "Policy": "string"
}
```

---

### 4.4 `tag-resource`

Adds tags to a CloudHSM resource (cluster or backup).

**Synopsis:**
```bash
aws cloudhsmv2 tag-resource \
    --resource-id <value> \
    --tag-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Cluster ID, backup ID, or ARN of the resource |
| `--tag-list` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**

No output fields (empty response on success).

---

### 4.5 `untag-resource`

Removes tags from a CloudHSM resource.

**Synopsis:**
```bash
aws cloudhsmv2 untag-resource \
    --resource-id <value> \
    --tag-key-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Cluster ID, backup ID, or ARN of the resource |
| `--tag-key-list` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

No output fields (empty response on success).

---

### 4.6 `list-tags`

Lists tags for a CloudHSM resource. **Paginated operation.**

**Synopsis:**
```bash
aws cloudhsmv2 list-tags \
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
| `--resource-id` | **Yes** | string | -- | Cluster ID, backup ID, or ARN of the resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```
