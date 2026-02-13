# Tags & Resource Policies

### 13.1 `tag-resource`

Tags a Network Manager resource.

**Synopsis:**
```bash
aws networkmanager tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 13.2 `untag-resource`

Removes tags from a Network Manager resource.

**Synopsis:**
```bash
aws networkmanager untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 13.3 `list-tags-for-resource`

Lists tags for a Network Manager resource.

**Synopsis:**
```bash
aws networkmanager list-tags-for-resource \
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
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 13.4 `get-resource-policy`

Returns the resource policy for a Network Manager resource (core network, global network).

**Synopsis:**
```bash
aws networkmanager get-resource-policy \
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
    "PolicyDocument": "string"
}
```

---

### 13.5 `put-resource-policy`

Creates or updates a resource policy for a Network Manager resource.

**Synopsis:**
```bash
aws networkmanager put-resource-policy \
    --policy-document <value> \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-document` | **Yes** | string | -- | JSON policy document |
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output:** None

---

### 13.6 `delete-resource-policy`

Deletes a resource policy from a Network Manager resource.

**Synopsis:**
```bash
aws networkmanager delete-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output:** None
