# Tags

### 8.1 `tag-resource`

Adds tags to an App Mesh resource. Each resource can have a maximum of 50 tags.

**Synopsis:**
```bash
aws appmesh tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the App Mesh resource |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `key=string,value=string ...` (key: 1-128 chars, value: 0-256 chars) |

**Output Schema:**

No output on success.

---

### 8.2 `untag-resource`

Removes tags from an App Mesh resource.

**Synopsis:**
```bash
aws appmesh untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the App Mesh resource |
| `--tag-keys` | **Yes** | list(string) | -- | The tag keys to remove |

**Output Schema:**

No output on success.

---

### 8.3 `list-tags-for-resource`

Lists the tags for an App Mesh resource. **Paginated.**

**Synopsis:**
```bash
aws appmesh list-tags-for-resource \
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
| `--resource-arn` | **Yes** | string | -- | The ARN of the App Mesh resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ],
    "nextToken": "string"
}
```
