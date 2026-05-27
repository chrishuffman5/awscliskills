# Rules & Tags

### 10.1 `tag-resource`

Adds tags to a Kendra resource (index, data source, FAQ, thesaurus, experience, etc.). Also applies to `aws kendra-ranking tag-resource` for ranking resources.

**Synopsis:**
```bash
aws kendra tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags: `[{Key: string (1-128 chars), Value: string (0-256 chars)}]` (max 200) |

**Output:** None

---

### 10.2 `untag-resource`

Removes tags from a Kendra resource.

**Synopsis:**
```bash
aws kendra untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (max 200) |

**Output:** None

---

### 10.3 `list-tags-for-resource`

Lists tags for a Kendra resource.

**Synopsis:**
```bash
aws kendra list-tags-for-resource \
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
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
