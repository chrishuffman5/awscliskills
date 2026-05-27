# Tags

### 13.1 `tag-resource`

Adds tags to an IoT Wireless resource.

**Synopsis:**
```bash
aws iotwireless tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags to add (max 200) |

**Tag structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```

**Output:** None

---

### 13.2 `untag-resource`

Removes tags from an IoT Wireless resource.

**Synopsis:**
```bash
aws iotwireless untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (max 200) |

**Output:** None

---

### 13.3 `list-tags-for-resource`

Lists tags for an IoT Wireless resource.

**Synopsis:**
```bash
aws iotwireless list-tags-for-resource \
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
