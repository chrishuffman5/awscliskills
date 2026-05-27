# Tags

### 3.1 `tag-resource`

Adds one or more tags to a CloudWatch Synthetics resource (canary or group).

**Synopsis:**
```bash
aws synthetics tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource (canary or group) |
| `--tags` | **Yes** | map | -- | Tags to add. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{}
```

---

### 3.2 `untag-resource`

Removes one or more tags from a CloudWatch Synthetics resource.

**Synopsis:**
```bash
aws synthetics untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 3.3 `list-tags-for-resource`

Lists all tags associated with a CloudWatch Synthetics resource.

**Synopsis:**
```bash
aws synthetics list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
