# Tags

### 3.1 `tag-resource`

Adds tags to a Device Advisor resource.

**Synopsis:**
```bash
aws iotdeviceadvisor tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag (20-2048 chars) |
| `--tags` | **Yes** | map | -- | Key-value tag pairs (max 50; key 1-128 chars, value 1-256 chars) |

**Output:** None

---

### 3.2 `untag-resource`

Removes tags from a Device Advisor resource.

**Synopsis:**
```bash
aws iotdeviceadvisor untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (20-2048 chars) |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (max 50; key 1-128 chars) |

**Output:** None

---

### 3.3 `list-tags-for-resource`

Lists tags for a Device Advisor resource.

**Synopsis:**
```bash
aws iotdeviceadvisor list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (20-2048 chars) |

**Output Schema:**
```json
{
    "tags": {
        "key": "value"
    }
}
```
