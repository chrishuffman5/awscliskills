# Resource Servers

Resource servers define custom OAuth 2.0 scopes for your user pool.

### 9.1 `create-resource-server`

Creates a resource server with custom scopes.

**Synopsis:**
```bash
aws cognito-idp create-resource-server \
    --user-pool-id <value> \
    --identifier <value> \
    --name <value> \
    [--scopes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--identifier` | **Yes** | string | -- | Unique resource server identifier (1-256 chars, e.g., `https://api.example.com`) |
| `--name` | **Yes** | string | -- | Display name (1-256 chars) |
| `--scopes` | No | list | None | Custom scopes. Shorthand: `ScopeName=read,ScopeDescription="Read access" ScopeName=write,ScopeDescription="Write access"` |

**Output Schema:**
```json
{
    "ResourceServer": {
        "UserPoolId": "string",
        "Identifier": "string",
        "Name": "string",
        "Scopes": [
            {
                "ScopeName": "string",
                "ScopeDescription": "string"
            }
        ]
    }
}
```

Custom scopes are referenced as `<identifier>/<scope-name>` (e.g., `https://api.example.com/read`).

---

### 9.2 `delete-resource-server`

Deletes a resource server.

**Synopsis:**
```bash
aws cognito-idp delete-resource-server \
    --user-pool-id <value> \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--identifier` | **Yes** | string | -- | Resource server identifier |

**Output:** None

---

### 9.3 `describe-resource-server`

Gets information about a resource server.

**Synopsis:**
```bash
aws cognito-idp describe-resource-server \
    --user-pool-id <value> \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--identifier` | **Yes** | string | -- | Resource server identifier |

**Output Schema:** Same as `create-resource-server`.

---

### 9.4 `list-resource-servers`

Lists resource servers for a user pool. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-idp list-resource-servers \
    --user-pool-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--max-results` | No | integer | 50 | Maximum items (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ResourceServers": [
        {
            "UserPoolId": "string",
            "Identifier": "string",
            "Name": "string",
            "Scopes": [
                {
                    "ScopeName": "string",
                    "ScopeDescription": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `update-resource-server`

Updates a resource server and its scopes.

**Synopsis:**
```bash
aws cognito-idp update-resource-server \
    --user-pool-id <value> \
    --identifier <value> \
    --name <value> \
    [--scopes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--identifier` | **Yes** | string | -- | Resource server identifier |
| `--name` | **Yes** | string | -- | Display name |
| `--scopes` | No | list | None | Updated scopes (replaces existing scopes) |

**Output Schema:** Same as `create-resource-server`.
