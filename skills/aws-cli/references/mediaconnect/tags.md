# Tags

## Regional Resources

### 11.1 `tag-resource`

Adds tags to a MediaConnect resource (flow, bridge, gateway).

**Synopsis:**
```bash
aws mediaconnect tag-resource \
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

### 11.2 `untag-resource`

Removes tags from a MediaConnect resource.

**Synopsis:**
```bash
aws mediaconnect untag-resource \
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

### 11.3 `list-tags-for-resource`

Lists tags for a MediaConnect resource.

**Synopsis:**
```bash
aws mediaconnect list-tags-for-resource \
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

## Global Resources

### 11.4 `tag-global-resource`

Adds tags to a global MediaConnect resource.

**Synopsis:**
```bash
aws mediaconnect tag-global-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the global resource |
| `--tags` | **Yes** | map | -- | Key-value tag pairs |

**Output:** None

---

### 11.5 `untag-global-resource`

Removes tags from a global MediaConnect resource.

**Synopsis:**
```bash
aws mediaconnect untag-global-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the global resource |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 11.6 `list-tags-for-global-resource`

Lists tags for a global MediaConnect resource.

**Synopsis:**
```bash
aws mediaconnect list-tags-for-global-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the global resource |

**Output Schema:**
```json
{
    "Tags": {"string": "string"}
}
```
