# Tags

### 6.1 `tag-resource`

Associates tags with a WAF v2 resource (web ACL, rule group, IP set, or regex pattern set).

**Synopsis:**
```bash
aws wafv2 tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output:** None on success.

---

### 6.2 `untag-resource`

Removes tags from a WAF v2 resource.

**Synopsis:**
```bash
aws wafv2 untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None on success.

---

### 6.3 `list-tags-for-resource`

Lists the tags for a WAF v2 resource. **Paginated operation.**

**Synopsis:**
```bash
aws wafv2 list-tags-for-resource \
    --resource-arn <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum results |

**Output Schema:**
```json
{
    "NextMarker": "string",
    "TagInfoForResource": {
        "ResourceARN": "string",
        "TagList": [
            {
                "Key": "string",
                "Value": "string"
            }
        ]
    }
}
```
