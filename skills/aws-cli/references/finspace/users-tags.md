# Users & Tags

## Users

### 8.1 `create-kx-user`

Creates a user in a KX environment. A KX user is linked to an IAM role that defines what actions the user can perform.

**Synopsis:**
```bash
aws finspace create-kx-user \
    --environment-id <value> \
    --user-name <value> \
    --iam-role <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--user-name` | **Yes** | string | -- | User name (unique per environment) |
| `--iam-role` | **Yes** | string | -- | IAM role ARN for the user |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "userName": "string",
    "userArn": "string",
    "environmentId": "string",
    "iamRole": "string"
}
```

---

### 8.2 `delete-kx-user`

Deletes a KX user from the specified environment.

**Synopsis:**
```bash
aws finspace delete-kx-user \
    --environment-id <value> \
    --user-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--user-name` | **Yes** | string | -- | User name to delete |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 8.3 `get-kx-user`

Returns details of a specific KX user.

**Synopsis:**
```bash
aws finspace get-kx-user \
    --environment-id <value> \
    --user-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--user-name` | **Yes** | string | -- | User name |

**Output Schema:**
```json
{
    "userName": "string",
    "userArn": "string",
    "environmentId": "string",
    "iamRole": "string"
}
```

---

### 8.4 `list-kx-users`

Returns a list of all KX users in the specified environment. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-users \
    --environment-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results per page |

**Output Schema:**
```json
{
    "users": [
        {
            "userArn": "string",
            "userName": "string",
            "iamRole": "string",
            "createTimestamp": "timestamp",
            "updateTimestamp": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.5 `update-kx-user`

Updates the IAM role for a KX user.

**Synopsis:**
```bash
aws finspace update-kx-user \
    --environment-id <value> \
    --user-name <value> \
    --iam-role <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--user-name` | **Yes** | string | -- | User name |
| `--iam-role` | **Yes** | string | -- | New IAM role ARN |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "userName": "string",
    "userArn": "string",
    "environmentId": "string",
    "iamRole": "string"
}
```

---

## Tags

### 8.6 `tag-resource`

Adds one or more tags to a FinSpace resource.

**Synopsis:**
```bash
aws finspace tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | map | -- | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output:** None (HTTP 200 on success)

---

### 8.7 `untag-resource`

Removes one or more tags from a FinSpace resource.

**Synopsis:**
```bash
aws finspace untag-resource \
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

**Output:** None (HTTP 200 on success)

---

### 8.8 `list-tags-for-resource`

Lists all tags on a FinSpace resource.

**Synopsis:**
```bash
aws finspace list-tags-for-resource \
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
    "tags": {
        "string": "string"
    }
}
```
