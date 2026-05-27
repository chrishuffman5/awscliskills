# Tags

### 5.1 `tag-resource`

Adds tags to a Budgets resource (budget or budget action).

**Synopsis:**
```bash
aws budgets tag-resource \
    --resource-arn <value> \
    --resource-tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--resource-tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` (max 200) |

**Output Schema:**
```json
{}
```

---

### 5.2 `untag-resource`

Removes tags from a Budgets resource.

**Synopsis:**
```bash
aws budgets untag-resource \
    --resource-arn <value> \
    --resource-tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--resource-tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 5.3 `list-tags-for-resource`

Lists tags associated with a Budgets resource.

**Synopsis:**
```bash
aws budgets list-tags-for-resource \
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
    "ResourceTags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
