# Memberships

### 2.1 `create-environment-membership`

Adds an environment member to an AWS Cloud9 development environment.

**Synopsis:**
```bash
aws cloud9 create-environment-membership \
    --environment-id <value> \
    --user-arn <value> \
    --permissions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | The ID of the environment |
| `--user-arn` | **Yes** | string | -- | The ARN of the user to add |
| `--permissions` | **Yes** | string | -- | The permission level: `read-write`, `read-only` |

**Output Schema:**
```json
{
    "membership": {
        "permissions": "owner|read-write|read-only",
        "userId": "string",
        "userArn": "string",
        "environmentId": "string",
        "lastAccess": "timestamp"
    }
}
```

---

### 2.2 `delete-environment-membership`

Deletes an environment member from an AWS Cloud9 development environment.

**Synopsis:**
```bash
aws cloud9 delete-environment-membership \
    --environment-id <value> \
    --user-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | The ID of the environment |
| `--user-arn` | **Yes** | string | -- | The ARN of the user to remove |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-environment-memberships`

Gets information about environment members for an AWS Cloud9 development environment. **Paginated operation.**

**Synopsis:**
```bash
aws cloud9 describe-environment-memberships \
    [--environment-id <value>] \
    [--user-arn <value>] \
    [--permissions <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | No | string | None | The ID of the environment |
| `--user-arn` | No | string | None | The ARN of the user to filter by. If not specified with --environment-id, lists all environments the user is a member of |
| `--permissions` | No | list(string) | None | Filter by permissions: `owner`, `read-write`, `read-only` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 25) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "memberships": [
        {
            "permissions": "owner|read-write|read-only",
            "userId": "string",
            "userArn": "string",
            "environmentId": "string",
            "lastAccess": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-environment-membership`

Changes the settings of an existing environment member for an AWS Cloud9 development environment.

**Synopsis:**
```bash
aws cloud9 update-environment-membership \
    --environment-id <value> \
    --user-arn <value> \
    --permissions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | The ID of the environment |
| `--user-arn` | **Yes** | string | -- | The ARN of the user to update |
| `--permissions` | **Yes** | string | -- | New permission level: `read-write`, `read-only` |

**Output Schema:**
```json
{
    "membership": {
        "permissions": "owner|read-write|read-only",
        "userId": "string",
        "userArn": "string",
        "environmentId": "string",
        "lastAccess": "timestamp"
    }
}
```
