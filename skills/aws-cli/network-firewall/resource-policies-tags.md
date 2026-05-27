# Resource Policies & Tags

### 10.1 `describe-resource-policy`

Returns the resource-based policy attached to the specified Network Firewall resource.

**Synopsis:**
```bash
aws network-firewall describe-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the rule group or firewall policy |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 10.2 `put-resource-policy`

Creates or updates a resource-based policy on a rule group or firewall policy for cross-account sharing.

**Synopsis:**
```bash
aws network-firewall put-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the rule group or firewall policy |
| `--policy` | **Yes** | string | -- | JSON resource policy document |

**Output Schema:**

No output fields (empty response on success).

---

### 10.3 `delete-resource-policy`

Deletes the resource-based policy from the specified resource.

**Synopsis:**
```bash
aws network-firewall delete-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**

No output fields (empty response on success).

---

### 10.4 `tag-resource`

Adds tags to the specified Network Firewall resource.

**Synopsis:**
```bash
aws network-firewall tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**

No output fields (empty response on success).

---

### 10.5 `untag-resource`

Removes tags from the specified Network Firewall resource.

**Synopsis:**
```bash
aws network-firewall untag-resource \
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

**Output Schema:**

No output fields (empty response on success).

---

### 10.6 `list-tags-for-resource`

Lists tags for the specified Network Firewall resource. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-tags-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```
