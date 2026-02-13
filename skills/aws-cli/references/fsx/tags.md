# Tags

### 9.1 `tag-resource`

Adds tags to an FSx resource.

**Synopsis:**
```bash
aws fsx tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | Tags (Key/Value pairs, max 50) |

**Tag Structure:**
```json
[
    {
        "Key": "string (1-128 chars)",
        "Value": "string (0-256 chars)"
    }
]
```

**Output:** None

---

### 9.2 `untag-resource`

Removes tags from an FSx resource.

**Synopsis:**
```bash
aws fsx untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (max 50) |

**Output:** None

---

### 9.3 `list-tags-for-resource`

Lists tags for an FSx resource. **Paginated operation.**

**Synopsis:**
```bash
aws fsx list-tags-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```
