# Tags

### 12.1 `tag-resource`

Adds tags to a Personalize resource.

**Synopsis:**
```bash
aws personalize tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 200 per resource) |

**Tag Structure:**
```json
[
    {
        "tagKey": "string",
        "tagValue": "string"
    }
]
```

**Output:** None (returns empty object on success)

---

### 12.2 `untag-resource`

Removes tags from a Personalize resource.

**Synopsis:**
```bash
aws personalize untag-resource \
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

**Output:** None (returns empty object on success)

---

### 12.3 `list-tags-for-resource`

Lists tags for a Personalize resource.

**Synopsis:**
```bash
aws personalize list-tags-for-resource \
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
    "tags": [
        {
            "tagKey": "string",
            "tagValue": "string"
        }
    ]
}
```
