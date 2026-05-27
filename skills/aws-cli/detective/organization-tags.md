# Organization & Tags

### 5.1 `enable-organization-admin-account`

Designates the Detective administrator account for the organization.

**Synopsis:**
```bash
aws detective enable-organization-admin-account \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID to designate as admin |

**Output:** None (HTTP 200 on success)

---

### 5.2 `disable-organization-admin-account`

Removes the Detective administrator account designation.

**Synopsis:**
```bash
aws detective disable-organization-admin-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None (HTTP 200 on success)

---

### 5.3 `list-organization-admin-accounts`

Lists the Detective administrator accounts for the organization. **Paginated operation.**

**Synopsis:**
```bash
aws detective list-organization-admin-accounts \
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
    "Administrators": [
        {
            "AccountId": "string",
            "GraphArn": "string",
            "DelegationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `describe-organization-configuration`

Returns the configuration for automatically enabling Detective for new organization accounts.

**Synopsis:**
```bash
aws detective describe-organization-configuration \
    --graph-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |

**Output Schema:**
```json
{
    "AutoEnable": "boolean"
}
```

---

### 5.5 `update-organization-configuration`

Updates the configuration for automatically enabling Detective for new organization accounts.

**Synopsis:**
```bash
aws detective update-organization-configuration \
    --graph-arn <value> \
    --auto-enable | --no-auto-enable \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--auto-enable` / `--no-auto-enable` | **Yes** | boolean | -- | Automatically enable Detective for new accounts |

**Output:** None (HTTP 200 on success)

---

### 5.6 `tag-resource`

Adds tags to a Detective resource (behavior graph).

**Synopsis:**
```bash
aws detective tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags to add (max 50) |

**Output:** None (HTTP 200 on success)

---

### 5.7 `untag-resource`

Removes tags from a Detective resource.

**Synopsis:**
```bash
aws detective untag-resource \
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

**Output:** None (HTTP 200 on success)

---

### 5.8 `list-tags-for-resource`

Lists tags for a Detective resource.

**Synopsis:**
```bash
aws detective list-tags-for-resource \
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
