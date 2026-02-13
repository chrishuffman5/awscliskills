# Tags

### 9.1 `tag-resource`

Adds tags to a Cost Explorer resource (anomaly monitor or subscription).

**Synopsis:**
```bash
aws ce tag-resource \
    --resource-arn <value> \
    --resource-tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--resource-tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` (max 50 user-tags) |

**Output Schema:**
```json
{}
```

---

### 9.2 `untag-resource`

Removes tags from a Cost Explorer resource.

**Synopsis:**
```bash
aws ce untag-resource \
    --resource-arn <value> \
    --resource-tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--resource-tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 9.3 `list-tags-for-resource`

Lists tags associated with a Cost Explorer resource.

**Synopsis:**
```bash
aws ce list-tags-for-resource \
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
    "ResourceTags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
