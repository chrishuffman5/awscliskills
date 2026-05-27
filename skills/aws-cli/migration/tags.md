# Tags & Service Management

## Tags (mgn)

### 14.1 `tag-resource`

Adds or overwrites tags on an MGN resource. Each resource supports up to 50 tags.

**Synopsis:**
```bash
aws mgn tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags (max 50, keys/values max 256 chars) |

**Output:** None

---

### 14.2 `untag-resource`

Removes tags from an MGN resource.

**Synopsis:**
```bash
aws mgn untag-resource \
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

### 14.3 `list-tags-for-resource`

Lists all tags for an MGN resource.

**Synopsis:**
```bash
aws mgn list-tags-for-resource \
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
    "tags": {"key": "value"}
}
```

---

## Service Management

### 14.4 `initialize-service`

Initializes AWS Application Migration Service (MGN) for use in your account. Must be called before using MGN.

**Synopsis:**
```bash
aws mgn initialize-service \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output:** None

---

### 14.5 `list-managed-accounts`

Lists AWS accounts managed by the MGN service. **Paginated.**

**Synopsis:**
```bash
aws mgn list-managed-accounts \
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
    "items": [
        {
            "accountId": "string"
        }
    ],
    "nextToken": "string"
}
```
