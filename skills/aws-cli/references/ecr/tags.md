# Tags

### 7.1 `tag-resource`

Adds metadata tags to an ECR resource. Currently only supports repositories.

**Synopsis:**
```bash
aws ecr tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (currently ECR repositories only) |
| `--tags` | **Yes** | list | -- | Key-value pairs. Key max 128 chars, Value max 256 chars. Shorthand: `Key=string,Value=string ...` |

**Output:** None on success.

---

### 7.2 `untag-resource`

Removes tags from an ECR resource.

**Synopsis:**
```bash
aws ecr untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove. Syntax: `"key1" "key2" ...` |

**Output:** None on success.

---

### 7.3 `list-tags-for-resource`

Lists the tags for an ECR resource.

**Synopsis:**
```bash
aws ecr list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (currently ECR repositories only) |

**Output Schema:**
```json
{
    "tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

