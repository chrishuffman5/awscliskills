# Tags

## MediaPackage v2 (Live)

### 8.1 `tag-resource` (mediapackagev2)

Adds tags to a MediaPackage v2 resource.

**Synopsis:**
```bash
aws mediapackagev2 tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Key-value tag pairs |

**Output:** None

---

### 8.2 `untag-resource` (mediapackagev2)

Removes tags from a MediaPackage v2 resource.

**Synopsis:**
```bash
aws mediapackagev2 untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 8.3 `list-tags-for-resource` (mediapackagev2)

Lists tags for a MediaPackage v2 resource.

**Synopsis:**
```bash
aws mediapackagev2 list-tags-for-resource \
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
    "Tags": {"string": "string"}
}
```

---

## MediaPackage VOD

### 8.4 `tag-resource` (mediapackage-vod)

Adds tags to a MediaPackage VOD resource.

**Synopsis:**
```bash
aws mediapackage-vod tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Key-value tag pairs |

**Output:** None

---

### 8.5 `untag-resource` (mediapackage-vod)

Removes tags from a MediaPackage VOD resource.

**Synopsis:**
```bash
aws mediapackage-vod untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 8.6 `list-tags-for-resource` (mediapackage-vod)

Lists tags for a MediaPackage VOD resource.

**Synopsis:**
```bash
aws mediapackage-vod list-tags-for-resource \
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
    "Tags": {"string": "string"}
}
```
