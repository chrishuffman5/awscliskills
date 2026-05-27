# Tags

### 4.1 `tag-resource`

Adds tags to an entity or change set in AWS Marketplace Catalog.

**Synopsis:**
```bash
aws marketplace-catalog tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag (max 255 chars) |
| `--tags` | **Yes** | list | -- | List of key-value tag objects (1-50). Shorthand: `Key=string,Value=string ...` |

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

Removes tags from an entity or change set in AWS Marketplace Catalog.

**Synopsis:**
```bash
aws marketplace-catalog untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to remove tags from (max 255 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | List of tag key names to remove (0-256 items) |

**Output:** None

---

### 4.3 `list-tags-for-resource`

Lists all tags on an entity or change set in AWS Marketplace Catalog.

**Synopsis:**
```bash
aws marketplace-catalog list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to list tags for (max 255 chars) |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
