# Tags

### 9.1 `tag-resource`

Adds or updates tags on a key.

**Synopsis:**
```bash
aws payment-cryptography tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | KeyARN of the key to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**

None (no output on success).

---

### 9.2 `untag-resource`

Removes tags from a key.

**Synopsis:**
```bash
aws payment-cryptography untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | KeyARN of the key to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

None (no output on success).

---

### 9.3 `list-tags-for-resource`

Lists all tags on a key. **Paginated operation.**

**Synopsis:**
```bash
aws payment-cryptography list-tags-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | KeyARN of the key |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

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
