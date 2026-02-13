# Policies & Tags

### 6.1 `put-policy`

Creates or replaces a resource policy for an Entity Resolution resource.

**Synopsis:**
```bash
aws entityresolution put-policy \
    --arn <value> \
    --policy <value> \
    [--token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource |
| `--policy` | **Yes** | string | -- | JSON resource policy (max 40960 chars) |
| `--token` | No | string | None | Policy revision token for conditional updates |

**Output Schema:**
```json
{
    "arn": "string",
    "policy": "string",
    "token": "string"
}
```

---

### 6.2 `get-policy`

Gets the resource policy for an Entity Resolution resource.

**Synopsis:**
```bash
aws entityresolution get-policy \
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
    "arn": "string",
    "policy": "string",
    "token": "string"
}
```

---

### 6.3 `add-policy-statement`

Adds a policy statement to an existing resource policy.

**Synopsis:**
```bash
aws entityresolution add-policy-statement \
    --arn <value> \
    --statement-id <value> \
    --effect <value> \
    --principal <value> \
    --action <value> \
    [--condition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource |
| `--statement-id` | **Yes** | string | -- | Statement identifier (1-64 chars) |
| `--effect` | **Yes** | string | -- | `Allow` or `Deny` |
| `--principal` | **Yes** | list(string) | -- | AWS principals to grant/deny access |
| `--action` | **Yes** | list(string) | -- | Actions to allow/deny |
| `--condition` | No | string | None | JSON condition expression |

**Output Schema:**
```json
{
    "arn": "string",
    "policy": "string",
    "token": "string"
}
```

---

### 6.4 `delete-policy-statement`

Removes a policy statement from a resource policy.

**Synopsis:**
```bash
aws entityresolution delete-policy-statement \
    --arn <value> \
    --statement-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource |
| `--statement-id` | **Yes** | string | -- | Statement ID to remove |

**Output Schema:**
```json
{
    "arn": "string",
    "policy": "string",
    "token": "string"
}
```

---

### 6.5 `tag-resource`

Adds tags to an Entity Resolution resource.

**Synopsis:**
```bash
aws entityresolution tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags to add (max 200 per resource) |

**Output:** None (returns empty object on success)

---

### 6.6 `untag-resource`

Removes tags from an Entity Resolution resource.

**Synopsis:**
```bash
aws entityresolution untag-resource \
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

**Output:** None (returns empty object on success)

---

### 6.7 `list-tags-for-resource`

Lists tags for an Entity Resolution resource.

**Synopsis:**
```bash
aws entityresolution list-tags-for-resource \
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
    "tags": {"string": "string"}
}
```
