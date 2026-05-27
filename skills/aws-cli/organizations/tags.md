# Tags

### 9.1 `tag-resource`

Adds one or more tags to an Organizations resource (account, root, OU, or policy).

**Synopsis:**
```bash
aws organizations tag-resource \
    --resource-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | ID of the resource to tag (account ID, root ID, OU ID, or policy ID) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{}
```

---

### 9.2 `untag-resource`

Removes one or more tags from an Organizations resource.

**Synopsis:**
```bash
aws organizations untag-resource \
    --resource-id <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | ID of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 9.3 `list-tags-for-resource`

Lists all tags attached to the specified resource. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-tags-for-resource \
    --resource-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--starting-token` | No | string | None | Pagination token |
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
