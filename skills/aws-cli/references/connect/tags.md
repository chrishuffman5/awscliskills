# Tags

## Connect Tags

### 32.1 `tag-resource`

Adds tags to a Connect resource.

**Synopsis:**
```bash
aws connect tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags to add (key: 1-128 chars, value: max 256 chars, max 50 tags) |

**Output:** None

---

### 32.2 `untag-resource`

Removes tags from a Connect resource.

**Synopsis:**
```bash
aws connect untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (1-50) |

**Output:** None

---

### 32.3 `list-tags-for-resource`

Lists tags for a Connect resource.

**Synopsis:**
```bash
aws connect list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "tags": { "key": "value" }
}
```

---

## ConnectCases Tags

### 32.4 `tag-resource` (connectcases)

Adds tags to a Cases resource.

**Synopsis:**
```bash
aws connectcases tag-resource \
    --arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Resource ARN (1-500 chars) |
| `--tags` | **Yes** | map | -- | Tags to add |

**Output:** None

---

### 32.5 `untag-resource` (connectcases)

Removes tags from a Cases resource.

**Synopsis:**
```bash
aws connectcases untag-resource \
    --arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Resource ARN (1-500 chars) |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 32.6 `list-tags-for-resource` (connectcases)

Lists tags for a Cases resource.

**Synopsis:**
```bash
aws connectcases list-tags-for-resource \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Resource ARN (1-500 chars) |

**Output Schema:**
```json
{
    "tags": { "key": "value" }
}
```
