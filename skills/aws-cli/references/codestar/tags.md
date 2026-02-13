# Tags

> Tag operations are available in both `aws codestar-connections` and `aws codestar-notifications`. Use the appropriate CLI service based on the resource type being tagged.

### 7.1 `tag-resource`

Adds or updates tags for a CodeStar Connections or Notifications resource.

**Synopsis (codestar-connections):**
```bash
aws codestar-connections tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Synopsis (codestar-notifications):**
```bash
aws codestar-notifications tag-resource \
    --arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters (codestar-connections):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Parameters (codestar-notifications):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags. JSON: `{"key":"value"}` |

**Output Schema (codestar-connections):**
```json
{}
```

**Output Schema (codestar-notifications):**
```json
{
    "Tags": {
        "string": "string"
    }
}
```

---

### 7.2 `untag-resource`

Removes tags from a resource.

**Synopsis (codestar-connections):**
```bash
aws codestar-connections untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Synopsis (codestar-notifications):**
```bash
aws codestar-notifications untag-resource \
    --arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters (codestar-connections):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Parameters (codestar-notifications):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 7.3 `list-tags-for-resource`

Lists tags for a resource.

**Synopsis (codestar-connections):**
```bash
aws codestar-connections list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Synopsis (codestar-notifications):**
```bash
aws codestar-notifications list-tags-for-resource \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters (codestar-connections):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Parameters (codestar-notifications):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema (codestar-connections):**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

**Output Schema (codestar-notifications):**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
