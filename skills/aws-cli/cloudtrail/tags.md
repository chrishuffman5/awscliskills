# Tags

### 7.1 `add-tags`

Adds one or more tags to a CloudTrail resource (trail, event data store, or channel).

**Synopsis:**
```bash
aws cloudtrail add-tags \
    --resource-id <value> \
    --tags-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | ARN of the resource (trail, event data store, or channel) |
| `--tags-list` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Tag Structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```

**Output:** None (HTTP 200 on success)

---

### 7.2 `remove-tags`

Removes one or more tags from a CloudTrail resource.

**Synopsis:**
```bash
aws cloudtrail remove-tags \
    --resource-id <value> \
    --tags-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | ARN of the resource |
| `--tags-list` | **Yes** | list | -- | Tags to remove. Shorthand: `Key=string,Value=string ...` |

**Output:** None (HTTP 200 on success)

---

### 7.3 `list-tags`

Lists tags for one or more CloudTrail resources. **Paginated operation.**

**Synopsis:**
```bash
aws cloudtrail list-tags \
    --resource-id-list <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id-list` | **Yes** | list(string) | -- | ARNs of resources to list tags for |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceTagList": [
        {
            "ResourceId": "string",
            "TagsList": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```
