# Tags

### 7.1 `tag-resource`

Adds tags to a DataSync resource (agent, task, or location).

**Synopsis:**
```bash
aws datasync tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 50 total per resource) |

**Tags Structure (shorthand):**
```
Key=string,Value=string ...
```

**Output:** None on success.

---

### 7.2 `untag-resource`

Removes tags from a DataSync resource.

**Synopsis:**
```bash
aws datasync untag-resource \
    --resource-arn <value> \
    --keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--keys` | **Yes** | list(string) | -- | Tag keys to remove (max 50) |

**Output:** None on success.

---

### 7.3 `list-tags-for-resource`

Lists tags for a DataSync resource. **Paginated operation.**

**Synopsis:**
```bash
aws datasync list-tags-for-resource \
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
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
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
