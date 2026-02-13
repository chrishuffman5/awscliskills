# Access

Commands for managing directory-service-based access entries for Transfer Family servers. Access entries map Active Directory groups (identified by SID) to IAM roles and directory settings.

### 3.1 `create-access`

Creates an access entry for a server using AWS Directory Service.

**Synopsis:**
```bash
aws transfer create-access \
    --role <value> \
    --server-id <value> \
    --external-id <value> \
    [--home-directory <value>] \
    [--home-directory-type <value>] \
    [--home-directory-mappings <value>] \
    [--policy <value>] \
    [--posix-profile <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role` | **Yes** | string | -- | IAM role ARN for access |
| `--server-id` | **Yes** | string | -- | Server ID |
| `--external-id` | **Yes** | string | -- | Active Directory group SID (pattern: `S-1-[\d-]+`) |
| `--home-directory` | No | string | None | Landing directory path |
| `--home-directory-type` | No | string | `PATH` | `PATH` or `LOGICAL` |
| `--home-directory-mappings` | No | list | None | Logical directory mappings |
| `--policy` | No | string | None | Session policy JSON (S3 only) |
| `--posix-profile` | No | structure | None | POSIX identity for EFS |

**Output Schema:**
```json
{
    "ServerId": "string",
    "ExternalId": "string"
}
```

---

### 3.2 `delete-access`

Deletes an access entry.

**Synopsis:**
```bash
aws transfer delete-access \
    --server-id <value> \
    --external-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--external-id` | **Yes** | string | -- | Active Directory group SID |

**Output:** None on success.

---

### 3.3 `describe-access`

Gets details about an access entry.

**Synopsis:**
```bash
aws transfer describe-access \
    --server-id <value> \
    --external-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--external-id` | **Yes** | string | -- | Active Directory group SID |

**Output Schema:**
```json
{
    "ServerId": "string",
    "Access": {
        "HomeDirectory": "string",
        "HomeDirectoryMappings": [{"Entry": "string", "Target": "string", "Type": "FILE|DIRECTORY"}],
        "HomeDirectoryType": "PATH|LOGICAL",
        "Policy": "string",
        "PosixProfile": {"Uid": "long", "Gid": "long", "SecondaryGids": ["long"]},
        "Role": "string",
        "ExternalId": "string"
    }
}
```

---

### 3.4 `list-accesses`

Lists access entries for a server. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-accesses \
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
    "Accesses": [
        {
            "HomeDirectory": "string",
            "HomeDirectoryType": "PATH|LOGICAL",
            "Role": "string",
            "ExternalId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-access`

Updates an access entry.

**Synopsis:**
```bash
aws transfer update-access \
    --server-id <value> \
    --external-id <value> \
    [--home-directory <value>] \
    [--home-directory-type <value>] \
    [--home-directory-mappings <value>] \
    [--policy <value>] \
    [--posix-profile <value>] \
    [--role <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-access` (all optional except `--server-id` and `--external-id`).

**Output Schema:**
```json
{
    "ServerId": "string",
    "ExternalId": "string"
}
```
