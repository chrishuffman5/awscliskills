# Tags

### 3.1 `tag-resource`

Adds tags to a HealthLake data store.

**Synopsis:**
```bash
aws healthlake tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Data store ARN (1-1011 chars) |
| `--tags` | **Yes** | list | -- | Tags: `Key=string,Value=string ...` (max 200 tags) |

**Tag Structure:**
- `Key` — Tag key (1-128 chars, case sensitive)
- `Value` — Tag value (0-256 chars, case sensitive)

**Output:** None

---

### 3.2 `untag-resource`

Removes tags from a HealthLake data store.

**Synopsis:**
```bash
aws healthlake untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Data store ARN (1-1011 chars) |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove (max 200, each 1-128 chars) |

**Output:** None

---

### 3.3 `list-tags-for-resource`

Lists tags for a HealthLake data store.

**Synopsis:**
```bash
aws healthlake list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Data store ARN (1-1011 chars) |

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
