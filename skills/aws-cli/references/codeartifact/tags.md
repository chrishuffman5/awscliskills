# Tags

### 6.1 `tag-resource`

Adds or updates tags for a CodeArtifact resource (domain, repository, or package group).

**Synopsis:**
```bash
aws codeartifact tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{}
```

---

### 6.2 `untag-resource`

Removes tags from a CodeArtifact resource.

**Synopsis:**
```bash
aws codeartifact untag-resource \
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

### 6.3 `list-tags-for-resource`

Returns a list of tags for a CodeArtifact resource.

**Synopsis:**
```bash
aws codeartifact list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```
