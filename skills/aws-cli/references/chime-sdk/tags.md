# Tags

Tag commands are available in all four Chime SDK services.

## chime-sdk-identity Tags

### 17.1 `tag-resource` (chime-sdk-identity)

Adds tags to a Chime SDK Identity resource.

**Synopsis:**
```bash
aws chime-sdk-identity tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | Tags (1-50) |

**Tags:**
```json
[
    { "Key": "string (1-128 chars)", "Value": "string (1-256 chars)" }
]
```

**Output:** None

---

### 17.2 `untag-resource` (chime-sdk-identity)

Removes tags from a Chime SDK Identity resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (1-50) |

**Output:** None

---

### 17.3 `list-tags-for-resource` (chime-sdk-identity)

Lists tags for a Chime SDK Identity resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": [
        { "Key": "string", "Value": "string" }
    ]
}
```

---

## chime-sdk-meetings Tags

### 17.4 `tag-resource` (chime-sdk-meetings)

Adds tags to a Chime SDK Meetings resource.

**Synopsis:**
```bash
aws chime-sdk-meetings tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Meeting ARN |
| `--tags` | **Yes** | list | -- | Tags (max 50) |

**Output:** None

---

### 17.5 `untag-resource` (chime-sdk-meetings)

Removes tags from a Chime SDK Meetings resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Meeting ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (1-50) |

**Output:** None

---

### 17.6 `list-tags-for-resource` (chime-sdk-meetings)

Lists tags for a Chime SDK Meetings resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Meeting ARN |

**Output Schema:**
```json
{
    "Tags": [
        { "Key": "string", "Value": "string" }
    ]
}
```

---

## chime-sdk-messaging Tags

### 17.7 `tag-resource` (chime-sdk-messaging)

Adds tags to a Chime SDK Messaging resource.

**Synopsis:**
```bash
aws chime-sdk-messaging tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | Tags (max 50) |

**Output:** None

---

### 17.8 `untag-resource` (chime-sdk-messaging)

Removes tags from a Chime SDK Messaging resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (1-50) |

**Output:** None

---

### 17.9 `list-tags-for-resource` (chime-sdk-messaging)

Lists tags for a Chime SDK Messaging resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": [
        { "Key": "string", "Value": "string" }
    ]
}
```

---

## chime-sdk-voice Tags

### 17.10 `tag-resource` (chime-sdk-voice)

Adds tags to a Chime SDK Voice resource.

**Synopsis:**
```bash
aws chime-sdk-voice tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | Tags (max 50) |

**Output:** None

---

### 17.11 `untag-resource` (chime-sdk-voice)

Removes tags from a Chime SDK Voice resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (1-50) |

**Output:** None

---

### 17.12 `list-tags-for-resource` (chime-sdk-voice)

Lists tags for a Chime SDK Voice resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": [
        { "Key": "string", "Value": "string" }
    ]
}
```
