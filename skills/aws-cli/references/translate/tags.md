# Tags

### 4.1 `tag-resource`

Associates tags with an Amazon Translate resource. Each tag is a key-value pair.

**Synopsis:**
```bash
aws translate tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Amazon Translate resource to tag (1-512 chars) |
| `--tags` | **Yes** | list | -- | Tags to associate. Shorthand: `Key=string,Value=string ...` (max 50 per resource) |

**Tag Structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```

**Output:** None

---

### 4.2 `untag-resource`

Removes tags from an Amazon Translate resource.

**Synopsis:**
```bash
aws translate untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Amazon Translate resource to untag (1-512 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (max 200 keys, each 1-128 chars) |

**Output:** None

---

### 4.3 `list-tags-for-resource`

Lists all tags associated with an Amazon Translate resource.

**Synopsis:**
```bash
aws translate list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Amazon Translate resource to query (1-512 chars) |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
