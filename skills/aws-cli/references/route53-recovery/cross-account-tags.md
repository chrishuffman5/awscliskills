# Cross-Account Authorization & Tags

Commands for managing cross-account authorization and tags across Route 53 ARC services.

## Cross-Account Authorization (route53-recovery-readiness)

### 9.1 `create-cross-account-authorization`

Creates a cross-account authorization, allowing another AWS account to check readiness status of resources in your account.

**Synopsis:**
```bash
aws route53-recovery-readiness create-cross-account-authorization \
    --cross-account-authorization <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cross-account-authorization` | **Yes** | string | -- | The AWS account ID to authorize |

**Output Schema:**
```json
{
    "CrossAccountAuthorization": "string"
}
```

---

### 9.2 `delete-cross-account-authorization`

Deletes a cross-account authorization.

**Synopsis:**
```bash
aws route53-recovery-readiness delete-cross-account-authorization \
    --cross-account-authorization <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cross-account-authorization` | **Yes** | string | -- | The cross-account authorization to delete |

**Output:** None on success.

---

### 9.3 `list-cross-account-authorizations`

Lists all cross-account authorizations. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness list-cross-account-authorizations \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CrossAccountAuthorizations": ["string"],
    "NextToken": "string"
}
```

---

## Tags (route53-recovery-control-config)

### 9.4 `tag-resource` (control-config)

Adds tags to a Route 53 ARC control configuration resource (cluster, control panel, safety rule).

**Synopsis:**
```bash
aws route53-recovery-control-config tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs |

**Output:** None on success.

---

### 9.5 `untag-resource` (control-config)

Removes tags from a Route 53 ARC control configuration resource.

**Synopsis:**
```bash
aws route53-recovery-control-config untag-resource \
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

**Output:** None on success.

---

### 9.6 `list-tags-for-resource` (control-config)

Lists tags for a Route 53 ARC control configuration resource.

**Synopsis:**
```bash
aws route53-recovery-control-config list-tags-for-resource \
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
        "string": "string"
    }
}
```

---

### 9.7 `get-resource-policy` (control-config)

Gets the resource policy for a cluster.

**Synopsis:**
```bash
aws route53-recovery-control-config get-resource-policy \
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
    "Policy": "string"
}
```

---

## Tags (route53-recovery-readiness)

### 9.8 `tag-resource` (readiness)

Adds tags to a Route 53 ARC readiness resource.

**Synopsis:**
```bash
aws route53-recovery-readiness tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs |

**Output:** None on success.

---

### 9.9 `untag-resource` (readiness)

Removes tags from a Route 53 ARC readiness resource.

**Synopsis:**
```bash
aws route53-recovery-readiness untag-resource \
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

**Output:** None on success.

---

### 9.10 `list-tags-for-resources` (readiness)

Lists tags for a Route 53 ARC readiness resource.

**Synopsis:**
```bash
aws route53-recovery-readiness list-tags-for-resources \
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
        "string": "string"
    }
}
```
