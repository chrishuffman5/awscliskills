# Tags

### 9.1 `tag-resource`

Adds tags to an IoT FleetWise resource.

**Synopsis:**
```bash
aws iotfleetwise tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags to add (max 50) |

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

### 9.2 `untag-resource`

Removes tags from an IoT FleetWise resource.

**Synopsis:**
```bash
aws iotfleetwise untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (0-50) |

**Output:** None

---

### 9.3 `list-tags-for-resource`

Lists tags for an IoT FleetWise resource.

**Synopsis:**
```bash
aws iotfleetwise list-tags-for-resource \
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
