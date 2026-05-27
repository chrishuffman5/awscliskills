# Tags

### 10.1 `tag-resource`

Adds tags to a resource.

**Synopsis:**
```bash
aws inspector2 tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags to add. Shorthand: `KeyName1=string,KeyName2=string` (keys 1-128 chars, values 0-256 chars) |

**Output Schema:** Empty on success.

---

### 10.2 `untag-resource`

Removes tags from a resource.

**Synopsis:**
```bash
aws inspector2 untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (1-128 chars each) |

**Output Schema:** Empty on success.

---

### 10.3 `list-tags-for-resource`

Lists tags for the specified resource.

**Synopsis:**
```bash
aws inspector2 list-tags-for-resource \
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
    "tags": {
        "key": "value"
    }
}
```
