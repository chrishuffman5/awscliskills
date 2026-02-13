# Connection Aliases

### 5.1 `create-connection-alias`

Creates a connection alias for use with cross-region redirection. A connection alias associates a connection string (FQDN) with a directory.

**Synopsis:**
```bash
aws workspaces create-connection-alias \
    --connection-string <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-string` | **Yes** | string | -- | The connection string (FQDN) for the alias (max 255 chars) |
| `--tags` | No | list | None | Tags to associate. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "AliasId": "string"
}
```

---

### 5.2 `delete-connection-alias`

Deletes the specified connection alias. If any resource associations exist for the alias, you must first disassociate them.

**Synopsis:**
```bash
aws workspaces delete-connection-alias \
    --alias-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-id` | **Yes** | string | -- | The connection alias ID to delete |

**Output Schema:**
```json
{}
```

---

### 5.3 `describe-connection-aliases`

Describes the specified connection aliases or all aliases. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-connection-aliases \
    [--alias-ids <value>] \
    [--resource-id <value>] \
    [--limit <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-ids` | No | list(string) | None | One or more connection alias IDs |
| `--resource-id` | No | string | None | Filter by associated directory ID |
| `--limit` | No | integer | None | Maximum number of items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConnectionAliases": [
        {
            "ConnectionString": "string",
            "AliasId": "string",
            "State": "CREATING|CREATED|DELETING",
            "OwnerAccountId": "string",
            "Associations": [
                {
                    "AssociationStatus": "NOT_ASSOCIATED|ASSOCIATED_WITH_OWNER_ACCOUNT|ASSOCIATED_WITH_SHARED_ACCOUNT|PENDING_ASSOCIATION|PENDING_DISASSOCIATION",
                    "AssociatedAccountId": "string",
                    "ResourceId": "string",
                    "ConnectionIdentifier": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `associate-connection-alias`

Associates the specified connection alias with the specified directory to enable cross-region redirection.

**Synopsis:**
```bash
aws workspaces associate-connection-alias \
    --alias-id <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-id` | **Yes** | string | -- | The connection alias ID |
| `--resource-id` | **Yes** | string | -- | The directory ID to associate with |

**Output Schema:**
```json
{
    "ConnectionIdentifier": "string"
}
```

---

### 5.5 `disassociate-connection-alias`

Disassociates a connection alias from a directory.

**Synopsis:**
```bash
aws workspaces disassociate-connection-alias \
    --alias-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-id` | **Yes** | string | -- | The connection alias ID to disassociate |

**Output Schema:**
```json
{}
```
