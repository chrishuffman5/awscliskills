# Tags

### 9.1 `tag-resource`

Adds or updates tags for a CodeCommit resource (repository).

**Synopsis:**
```bash
aws codecommit tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{}
```

---

### 9.2 `untag-resource`

Removes tags from a CodeCommit resource.

**Synopsis:**
```bash
aws codecommit untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 9.3 `list-tags-for-resource`

Lists tags for a CodeCommit resource.

**Synopsis:**
```bash
aws codecommit list-tags-for-resource \
    --resource-arn <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    },
    "nextToken": "string"
}
```
