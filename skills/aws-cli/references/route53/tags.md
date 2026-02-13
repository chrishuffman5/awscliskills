# Tags

### 9.1 `change-tags-for-resource` (`route53`)

Adds, edits, or deletes tags for a Route 53 resource (hosted zone or health check).

**Synopsis:**
```bash
aws route53 change-tags-for-resource \
    --resource-type <value> \
    --resource-id <value> \
    [--add-tags <value>] \
    [--remove-tag-keys <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | `hostedzone` or `healthcheck` |
| `--resource-id` | **Yes** | string | -- | Resource ID (max 64 chars) |
| `--add-tags` | No | list | None | Tags to add. Shorthand: `Key=string,Value=string ...` (max 10 tags) |
| `--remove-tag-keys` | No | list(string) | None | Tag keys to remove (max 10 keys) |

**Tag Constraints:**

| Field | Constraints |
|-------|-------------|
| `Key` | Max 128 chars |
| `Value` | Max 256 chars |

**Output:** None on success.

---

### 9.2 `list-tags-for-resource` (`route53`)

Lists tags for a single Route 53 resource.

**Synopsis:**
```bash
aws route53 list-tags-for-resource \
    --resource-type <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | `hostedzone` or `healthcheck` |
| `--resource-id` | **Yes** | string | -- | Resource ID (max 64 chars) |

**Output Schema:**
```json
{
    "ResourceTagSet": {
        "ResourceType": "hostedzone|healthcheck",
        "ResourceId": "string",
        "Tags": [
            {
                "Key": "string",
                "Value": "string"
            }
        ]
    }
}
```

---

### 9.3 `list-tags-for-resources` (`route53`)

Lists tags for up to 10 Route 53 resources of the same type.

**Synopsis:**
```bash
aws route53 list-tags-for-resources \
    --resource-type <value> \
    --resource-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | `hostedzone` or `healthcheck` |
| `--resource-ids` | **Yes** | list(string) | -- | Resource IDs (max 10, each max 64 chars) |

**Output Schema:**
```json
{
    "ResourceTagSets": [
        {
            "ResourceType": "hostedzone|healthcheck",
            "ResourceId": "string",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ]
        }
    ]
}
```

---

### 9.4 `list-tags-for-domain` (`route53domains`)

Lists tags for a registered domain.

**Synopsis:**
```bash
aws route53domains list-tags-for-domain \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |

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

### 9.5 `update-tags-for-domain` (`route53domains`)

Adds or updates tags for a registered domain.

**Synopsis:**
```bash
aws route53domains update-tags-for-domain \
    --domain-name <value> \
    [--tags-to-update <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |
| `--tags-to-update` | No | list | None | Tags to add/update. Shorthand: `Key=string,Value=string ...` |

**Output:** None on success.

---

### 9.6 `delete-tags-for-domain` (`route53domains`)

Deletes tags from a registered domain.

**Synopsis:**
```bash
aws route53domains delete-tags-for-domain \
    --domain-name <value> \
    --tags-to-delete <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |
| `--tags-to-delete` | **Yes** | list(string) | -- | Tag keys to delete |

**Output:** None on success.

---
