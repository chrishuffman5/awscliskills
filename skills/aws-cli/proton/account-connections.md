# Account Connections

### 7.1 `create-environment-account-connection`

Creates an environment account connection to allow a management account to deploy environments into a member account.

**Synopsis:**
```bash
aws proton create-environment-account-connection \
    --environment-name <value> \
    --management-account-id <value> \
    [--role-arn <value>] \
    [--component-role-arn <value>] \
    [--codebuild-role-arn <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | **Yes** | string | -- | Environment name for the connection |
| `--management-account-id` | **Yes** | string | -- | Management account ID |
| `--role-arn` | No | string | None | IAM role for Proton to provision resources |
| `--component-role-arn` | No | string | None | IAM role for components |
| `--codebuild-role-arn` | No | string | None | CodeBuild role ARN |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "environmentAccountConnection": {
        "id": "string",
        "arn": "string",
        "environmentName": "string",
        "environmentAccountId": "string",
        "managementAccountId": "string",
        "roleArn": "string",
        "componentRoleArn": "string",
        "codebuildRoleArn": "string",
        "status": "PENDING|CONNECTED|REJECTED",
        "requestedAt": "timestamp",
        "lastModifiedAt": "timestamp"
    }
}
```

---

### 7.2 `update-environment-account-connection`

Updates an environment account connection.

**Synopsis:**
```bash
aws proton update-environment-account-connection \
    --id <value> \
    [--role-arn <value>] \
    [--component-role-arn <value>] \
    [--codebuild-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Connection ID |
| `--role-arn` | No | string | None | Updated role ARN |
| `--component-role-arn` | No | string | None | Updated component role ARN |
| `--codebuild-role-arn` | No | string | None | Updated CodeBuild role ARN |

**Output Schema:** Same as `create-environment-account-connection`.

---

### 7.3 `delete-environment-account-connection`

Deletes an environment account connection.

**Synopsis:**
```bash
aws proton delete-environment-account-connection \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Connection ID |

**Output Schema:** Same as `create-environment-account-connection`.

---

### 7.4 `get-environment-account-connection`

Gets an environment account connection.

**Synopsis:**
```bash
aws proton get-environment-account-connection \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Connection ID |

**Output Schema:** Same as `create-environment-account-connection`.

---

### 7.5 `list-environment-account-connections`

Lists environment account connections. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-environment-account-connections \
    --requested-by <value> \
    [--environment-name <value>] \
    [--statuses <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--requested-by` | **Yes** | string | -- | `MANAGEMENT_ACCOUNT` or `ENVIRONMENT_ACCOUNT` |
| `--environment-name` | No | string | None | Filter by environment name |
| `--statuses` | No | list | None | Filter by status: `PENDING`, `CONNECTED`, `REJECTED` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "environmentAccountConnections": [
        {
            "id": "string",
            "arn": "string",
            "environmentName": "string",
            "environmentAccountId": "string",
            "managementAccountId": "string",
            "roleArn": "string",
            "componentRoleArn": "string",
            "status": "PENDING|CONNECTED|REJECTED",
            "requestedAt": "timestamp",
            "lastModifiedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.6 `accept-environment-account-connection`

Accepts an environment account connection request (from the management account).

**Synopsis:**
```bash
aws proton accept-environment-account-connection \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Connection ID |

**Output Schema:** Same as `create-environment-account-connection` with status `CONNECTED`.

---

### 7.7 `reject-environment-account-connection`

Rejects an environment account connection request.

**Synopsis:**
```bash
aws proton reject-environment-account-connection \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Connection ID |

**Output Schema:** Same as `create-environment-account-connection` with status `REJECTED`.
