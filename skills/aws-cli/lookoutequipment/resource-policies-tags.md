# Resource Policies & Tags

### 7.1 `put-resource-policy`

Creates or updates a resource control policy for cross-account access to a resource.

**Synopsis:**
```bash
aws lookoutequipment put-resource-policy \
    --resource-arn <value> \
    --resource-policy <value> \
    [--policy-revision-id <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--resource-policy` | **Yes** | string | -- | JSON resource policy (max 20000 chars) |
| `--policy-revision-id` | No | string | None | Revision ID for conditional updates |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "PolicyRevisionId": "string"
}
```

---

### 7.2 `describe-resource-policy`

Describes a resource policy attached to a resource.

**Synopsis:**
```bash
aws lookoutequipment describe-resource-policy \
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
    "PolicyRevisionId": "string",
    "ResourcePolicy": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 7.3 `delete-resource-policy`

Deletes a resource policy from a resource.

**Synopsis:**
```bash
aws lookoutequipment delete-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output:** None

---

### 7.4 `tag-resource`

Adds tags to a Lookout for Equipment resource.

**Synopsis:**
```bash
aws lookoutequipment tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 200 per resource) |

**Tag Structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```

**Output:** None (returns empty object on success)

---

### 7.5 `untag-resource`

Removes tags from a Lookout for Equipment resource.

**Synopsis:**
```bash
aws lookoutequipment untag-resource \
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

### 7.6 `list-tags-for-resource`

Lists tags for a Lookout for Equipment resource.

**Synopsis:**
```bash
aws lookoutequipment list-tags-for-resource \
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
