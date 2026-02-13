# Tags

### 11.1 `tag-resource`

Adds tags to a Lambda function, event source mapping, or code signing configuration.

**Synopsis:**
```bash
aws lambda tag-resource \
    --resource <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags. Shorthand: `Key1=Value1,Key2=Value2` |

**Output:** None on success.

---

### 11.2 `untag-resource`

Removes tags from a Lambda resource.

**Synopsis:**
```bash
aws lambda untag-resource \
    --resource <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None on success.

---

### 11.3 `list-tags`

Returns the tags associated with a Lambda resource.

**Synopsis:**
```bash
aws lambda list-tags \
    --resource <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": {"string": "string"}
}
```

---
