# Users

### 2.1 `create-user`

Creates a user on a Transfer Family server.

**Synopsis:**
```bash
aws transfer create-user \
    --role <value> \
    --server-id <value> \
    --user-name <value> \
    [--home-directory <value>] \
    [--home-directory-type <value>] \
    [--home-directory-mappings <value>] \
    [--policy <value>] \
    [--posix-profile <value>] \
    [--ssh-public-key-body <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role` | **Yes** | string | -- | IAM role ARN for user access |
| `--server-id` | **Yes** | string | -- | Server ID |
| `--user-name` | **Yes** | string | -- | Username (3-100 chars, alphanumeric/underscores/hyphens/periods/@) |
| `--home-directory` | No | string | None | Landing directory (e.g., `/bucket/home/user`) |
| `--home-directory-type` | No | string | `PATH` | `PATH` or `LOGICAL` |
| `--home-directory-mappings` | No | list | None | Logical directory mappings (required if type is LOGICAL) |
| `--policy` | No | string | None | Session policy JSON (S3 only, max 2048 chars) |
| `--posix-profile` | No | structure | None | POSIX identity for EFS: `Uid=long,Gid=long` |
| `--ssh-public-key-body` | No | string | None | SSH public key (RSA/ECDSA/ED25519) |
| `--tags` | No | list | None | Tags (max 50) |

**Home Directory Mapping (shorthand):**
```
Entry=string,Target=string,Type=string ...
```

**Output Schema:**
```json
{
    "ServerId": "string",
    "UserName": "string"
}
```

---

### 2.2 `delete-user`

Deletes a user from a server.

**Synopsis:**
```bash
aws transfer delete-user \
    --server-id <value> \
    --user-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--user-name` | **Yes** | string | -- | Username to delete |

**Output:** None on success.

---

### 2.3 `describe-user`

Gets details about a user.

**Synopsis:**
```bash
aws transfer describe-user \
    --server-id <value> \
    --user-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--user-name` | **Yes** | string | -- | Username |

**Output Schema:**
```json
{
    "ServerId": "string",
    "User": {
        "Arn": "string",
        "HomeDirectory": "string",
        "HomeDirectoryMappings": [
            {"Entry": "string", "Target": "string", "Type": "FILE|DIRECTORY"}
        ],
        "HomeDirectoryType": "PATH|LOGICAL",
        "Policy": "string",
        "PosixProfile": {"Uid": "long", "Gid": "long", "SecondaryGids": ["long"]},
        "Role": "string",
        "SshPublicKeys": [
            {
                "DateImported": "timestamp",
                "SshPublicKeyBody": "string",
                "SshPublicKeyId": "string"
            }
        ],
        "Tags": [{"Key": "string", "Value": "string"}],
        "UserName": "string"
    }
}
```

---

### 2.4 `list-users`

Lists users for a server. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-users \
    --server-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ServerId": "string",
    "Users": [
        {
            "Arn": "string",
            "HomeDirectory": "string",
            "HomeDirectoryType": "PATH|LOGICAL",
            "Role": "string",
            "SshPublicKeyCount": "integer",
            "UserName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-user`

Updates user settings.

**Synopsis:**
```bash
aws transfer update-user \
    --server-id <value> \
    --user-name <value> \
    [--home-directory <value>] \
    [--home-directory-type <value>] \
    [--home-directory-mappings <value>] \
    [--policy <value>] \
    [--posix-profile <value>] \
    [--role <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-user` (except `--ssh-public-key-body` and `--tags`).

**Output Schema:**
```json
{
    "ServerId": "string",
    "UserName": "string"
}
```

---

### 2.6 `import-ssh-public-key`

Imports an SSH public key for a user.

**Synopsis:**
```bash
aws transfer import-ssh-public-key \
    --server-id <value> \
    --ssh-public-key-body <value> \
    --user-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--ssh-public-key-body` | **Yes** | string | -- | SSH public key content |
| `--user-name` | **Yes** | string | -- | Username |

**Output Schema:**
```json
{
    "ServerId": "string",
    "SshPublicKeyId": "string",
    "UserName": "string"
}
```

---

### 2.7 `delete-ssh-public-key`

Deletes an SSH public key from a user.

**Synopsis:**
```bash
aws transfer delete-ssh-public-key \
    --server-id <value> \
    --ssh-public-key-id <value> \
    --user-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--ssh-public-key-id` | **Yes** | string | -- | SSH public key ID |
| `--user-name` | **Yes** | string | -- | Username |

**Output:** None on success.
