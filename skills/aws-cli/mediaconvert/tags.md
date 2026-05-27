# Tags

### 9.1 `tag-resource`

Adds tags to a MediaConvert resource (queue, preset, or job template).

**Synopsis:**
```bash
aws mediaconvert tag-resource \
    --arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Key-value pairs for tags |

**Output:** None

---

### 9.2 `untag-resource`

Removes tags from a MediaConvert resource.

**Synopsis:**
```bash
aws mediaconvert untag-resource \
    --arn <value> \
    [--tag-keys <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | No | list | None | List of tag keys to remove |

**Output:** None

---

### 9.3 `list-tags-for-resource`

Lists tags for a MediaConvert resource.

**Synopsis:**
```bash
aws mediaconvert list-tags-for-resource \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "ResourceTags": {
        "Arn": "string",
        "Tags": {
            "key": "value"
        }
    }
}
```
