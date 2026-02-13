# Tags

### 17.1 `tag-resource`

Adds tags to a CloudFront resource.

**Synopsis:**
```bash
aws cloudfront tag-resource \
    --resource <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--resource` | **Yes** | string | Resource ARN |
| `--tags` | **Yes** | structure | Tags to add. `Items`: list of `Key`/`Value` pairs |

**Output:** None.

---

### 17.2 `untag-resource`

Removes tags from a CloudFront resource.

**Synopsis:**
```bash
aws cloudfront untag-resource \
    --resource <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--resource` | **Yes** | string | Resource ARN |
| `--tag-keys` | **Yes** | structure | Tag keys to remove. `Items`: list of key strings |

**Output:** None.

---

### 17.3 `list-tags-for-resource`

Lists tags for a CloudFront resource.

**Synopsis:**
```bash
aws cloudfront list-tags-for-resource \
    --resource <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--resource` | **Yes** | string | Resource ARN |

**Output Schema:**
```json
{
    "Tags": {
        "Items": [
            {
                "Key": "string",
                "Value": "string"
            }
        ]
    }
}
```

---
