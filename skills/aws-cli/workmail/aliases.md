# Aliases & Email

### 5.1 `create-alias`

Creates an alias for a user or group entity.

**Synopsis:**
```bash
aws workmail create-alias \
    --organization-id <value> \
    --entity-id <value> \
    --alias <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID (user or group) |
| `--alias` | **Yes** | string | -- | Alias email address (1-254 chars) |

**Output:** None

---

### 5.2 `delete-alias`

Deletes an alias from an entity.

**Synopsis:**
```bash
aws workmail delete-alias \
    --organization-id <value> \
    --entity-id <value> \
    --alias <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID |
| `--alias` | **Yes** | string | -- | Alias email address to remove |

**Output:** None

---

### 5.3 `list-aliases`

Lists aliases for an entity. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-aliases \
    --organization-id <value> \
    --entity-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Aliases": ["string"],
    "NextToken": "string"
}
```

---

### 5.4 `update-primary-email-address`

Updates the primary email address of an entity.

**Synopsis:**
```bash
aws workmail update-primary-email-address \
    --organization-id <value> \
    --entity-id <value> \
    --email <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID (user, group, or resource) |
| `--email` | **Yes** | string | -- | New primary email address (1-254 chars) |

**Output:** None
