# Tags

### 2.1 `tag-resource`

Adds tags to a billing resource.

**Synopsis:**
```bash
aws billing tag-resource \
    --resource-arn <value> \
    --resource-tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the billing resource to tag |
| `--resource-tags` | **Yes** | list | -- | Tags (Key/Value pairs, max 200). Shorthand: `key=string,value=string ...` |

**Output:** None

---

### 2.2 `untag-resource`

Removes tags from a billing resource.

**Synopsis:**
```bash
aws billing untag-resource \
    --resource-arn <value> \
    --resource-tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the billing resource |
| `--resource-tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 2.3 `list-tags-for-resource`

Lists tags on a billing resource.

**Synopsis:**
```bash
aws billing list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the billing resource |

**Output Schema:**
```json
{
    "resourceTags": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```
