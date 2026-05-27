# Tags

### 14.1 `tag-resource`

Adds tags to a Lex V2 resource (bot, bot alias, or bot channel).

**Synopsis:**
```bash
aws lexv2-models tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag (1-1011 chars) |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs (max 200, key: 1-128 chars, value: 0-256 chars) |

**Output:** None

---

### 14.2 `untag-resource`

Removes tags from a Lex V2 resource.

**Synopsis:**
```bash
aws lexv2-models untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag (1-1011 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (max 200, each 1-128 chars) |

**Output:** None

---

### 14.3 `list-tags-for-resource`

Lists all tags for a Lex V2 resource.

**Synopsis:**
```bash
aws lexv2-models list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to query (1-1011 chars) |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
