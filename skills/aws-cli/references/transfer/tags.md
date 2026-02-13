# Tags

### 11.1 `tag-resource`

Adds tags to a Transfer Family resource (server, user, workflow, connector, agreement, profile, certificate, host key, web app).

**Synopsis:**
```bash
aws transfer tag-resource \
    --arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Tag Constraints:**
- Maximum 50 tags per resource
- Key: 0-128 characters
- Value: 0-256 characters

**Output:** None on success.

---

### 11.2 `untag-resource`

Removes tags from a Transfer Family resource.

**Synopsis:**
```bash
aws transfer untag-resource \
    --arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None on success.

---

### 11.3 `list-tags-for-resource`

Lists tags for a Transfer Family resource. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-tags-for-resource \
    --arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Arn": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```
