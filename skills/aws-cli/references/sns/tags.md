# Tags

### 11.1 `tag-resource`

Adds tags to an SNS topic. Max 50 tags per topic. Rate limit: 10 TPS per account per region.

**Synopsis:**
```bash
aws sns tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the topic. Min 1, max 1011 chars |
| `--tags` | **Yes** | list | -- | Key-value tags. Key: 1-128 chars. Value: 0-256 chars. Shorthand: `Key=string,Value=string ...` |

**Output Schema:** None

---

### 11.2 `untag-resource`

Removes tags from an SNS topic.

**Synopsis:**
```bash
aws sns untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the topic. Min 1, max 1011 chars |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove. Each key: 1-128 chars. Space-separated |

**Output Schema:** None

---

### 11.3 `list-tags-for-resource`

Lists all tags for an SNS topic.

**Synopsis:**
```bash
aws sns list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the topic. Min 1, max 1011 chars |

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
