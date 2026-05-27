# Tags

### 17.1 `tag-resource`

Adds tags to a DynamoDB resource (table, backup, etc.).

**Synopsis:**
```bash
aws dynamodb tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (1-1283 chars) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` (up to 50 tags) |

**Output:** None.

---

### 17.2 `untag-resource`

Removes tags from a DynamoDB resource.

**Synopsis:**
```bash
aws dynamodb untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (1-1283 chars) |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove. List of strings |

**Output:** None.

---

### 17.3 `list-tags-of-resource`

Lists all tags on a DynamoDB resource. **Paginated operation.**

**Synopsis:**
```bash
aws dynamodb list-tags-of-resource \
    --resource-arn <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (1-1283 chars) |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```

---
