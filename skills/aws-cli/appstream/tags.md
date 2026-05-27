# Tags

### 10.1 `tag-resource`

Adds or overwrites tags for the specified AppStream 2.0 resource.

**Synopsis:**
```bash
aws appstream tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{}
```

---

### 10.2 `untag-resource`

Removes tags from the specified AppStream 2.0 resource.

**Synopsis:**
```bash
aws appstream untag-resource \
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

### 10.3 `list-tags-for-resource`

Lists the tags for the specified AppStream 2.0 resource.

**Synopsis:**
```bash
aws appstream list-tags-for-resource \
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
    "Tags": {
        "string": "string"
    }
}
```
