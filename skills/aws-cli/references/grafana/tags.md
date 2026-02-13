# Tags

### 6.1 `tag-resource`

Adds tags to an Amazon Managed Grafana resource (workspace).

**Synopsis:**
```bash
aws grafana tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource (workspace ARN) |
| `--tags` | **Yes** | map | -- | Tags to add. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{}
```

---

### 6.2 `untag-resource`

Removes tags from an Amazon Managed Grafana resource.

**Synopsis:**
```bash
aws grafana untag-resource \
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

### 6.3 `list-tags-for-resource`

Lists tags for an Amazon Managed Grafana resource.

**Synopsis:**
```bash
aws grafana list-tags-for-resource \
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
    "tags": {
        "string": "string"
    }
}
```
