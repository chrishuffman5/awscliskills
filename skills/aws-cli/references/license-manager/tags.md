# Tags

> Tag commands are available in all three namespaces. Use the correct namespace prefix for your resource type.

## license-manager

### 10.1 `tag-resource`

Adds tags to a License Manager resource.

**Synopsis:**
```bash
aws license-manager tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags (Key/Value pairs). Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 10.2 `untag-resource`

Removes tags from a License Manager resource.

**Synopsis:**
```bash
aws license-manager untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 10.3 `list-tags-for-resource`

Lists tags on a License Manager resource.

**Synopsis:**
```bash
aws license-manager list-tags-for-resource \
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

---

## license-manager-linux-subscriptions

### 10.4 `tag-resource`

Adds tags to a Linux subscriptions resource.

**Synopsis:**
```bash
aws license-manager-linux-subscriptions tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags. Format: `KeyName1=string,KeyName2=string` |

**Output:** None

---

### 10.5 `untag-resource`

Removes tags from a Linux subscriptions resource.

**Synopsis:**
```bash
aws license-manager-linux-subscriptions untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 10.6 `list-tags-for-resource`

Lists tags on a Linux subscriptions resource.

**Synopsis:**
```bash
aws license-manager-linux-subscriptions list-tags-for-resource \
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
        "KeyName": "string"
    }
}
```

---

## license-manager-user-subscriptions

### 10.7 `tag-resource`

Adds tags to a user subscriptions resource.

**Synopsis:**
```bash
aws license-manager-user-subscriptions tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags. Format: `KeyName1=string,KeyName2=string` |

**Output:** None

---

### 10.8 `untag-resource`

Removes tags from a user subscriptions resource.

**Synopsis:**
```bash
aws license-manager-user-subscriptions untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 10.9 `list-tags-for-resource`

Lists tags on a user subscriptions resource.

**Synopsis:**
```bash
aws license-manager-user-subscriptions list-tags-for-resource \
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
        "KeyName": "string"
    }
}
```
