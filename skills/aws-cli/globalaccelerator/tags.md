# Tags

### 7.1 `tag-resource`

Adds tags to a Global Accelerator resource (accelerator, listener, endpoint group, or cross-account attachment).

**Synopsis:**
```bash
aws globalaccelerator tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Tag Constraints:**
- Key: 1-128 characters
- Value: 0-256 characters
- Maximum 50 tags per resource

**Output:** None on success.

---

### 7.2 `untag-resource`

Removes tags from a Global Accelerator resource.

**Synopsis:**
```bash
aws globalaccelerator untag-resource \
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

### 7.3 `list-tags-for-resource`

Lists tags for a Global Accelerator resource.

**Synopsis:**
```bash
aws globalaccelerator list-tags-for-resource \
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
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
