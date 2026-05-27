# Tags

### 10.1 `tag-resource`

Adds tags to a Forecast resource (dataset, dataset group, predictor, forecast, etc.).

**Synopsis:**
```bash
aws forecast tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (max 256 chars) |
| `--tags` | **Yes** | list | -- | Tags: `Key=string,Value=string ...` (max 200 tags) |

**Tag Constraints:**
- Key: 1-128 chars, case sensitive
- Value: 0-256 chars, case sensitive
- Cannot use `aws:` prefix for keys
- Max 50 tags per resource

**Output:** None

---

### 10.2 `untag-resource`

Removes tags from a Forecast resource.

**Synopsis:**
```bash
aws forecast untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (max 256 chars) |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (max 200) |

**Output:** None

---

### 10.3 `list-tags-for-resource`

Lists tags for a Forecast resource.

**Synopsis:**
```bash
aws forecast list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (max 256 chars) |

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
