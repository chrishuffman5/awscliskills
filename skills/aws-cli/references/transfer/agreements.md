# Agreements

Commands for managing AS2 agreements in Transfer Family. An agreement links a local profile, partner profile, and server for B2B file exchange.

### 5.1 `create-agreement`

Creates an AS2 agreement between a local profile and partner profile on a server.

**Synopsis:**
```bash
aws transfer create-agreement \
    --server-id <value> \
    --local-profile-id <value> \
    --partner-profile-id <value> \
    --access-role <value> \
    [--description <value>] \
    [--base-directory <value>] \
    [--status <value>] \
    [--tags <value>] \
    [--preserve-filename <value>] \
    [--enforce-message-signing <value>] \
    [--custom-directories <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--local-profile-id` | **Yes** | string | -- | Local AS2 profile ID |
| `--partner-profile-id` | **Yes** | string | -- | Partner AS2 profile ID |
| `--access-role` | **Yes** | string | -- | IAM role ARN for agreement access |
| `--description` | No | string | None | Description (1-200 chars) |
| `--base-directory` | No* | string | None | Landing directory for AS2 files |
| `--status` | No | string | `ACTIVE` | `ACTIVE` or `INACTIVE` |
| `--tags` | No | list | None | Tags |
| `--preserve-filename` | No | string | `DISABLED` | `ENABLED` or `DISABLED` |
| `--enforce-message-signing` | No | string | `DISABLED` | `ENABLED` or `DISABLED` |
| `--custom-directories` | No* | structure | None | Custom AS2 directories |

*Use either `--base-directory` or `--custom-directories`, not both.

**Custom Directories (JSON):**
```json
{
    "FailedFilesDirectory": "string",
    "MdnFilesDirectory": "string",
    "PayloadFilesDirectory": "string",
    "StatusFilesDirectory": "string",
    "TemporaryFilesDirectory": "string"
}
```

**Output Schema:**
```json
{
    "AgreementId": "string"
}
```

---

### 5.2 `delete-agreement`

Deletes an agreement.

**Synopsis:**
```bash
aws transfer delete-agreement \
    --agreement-id <value> \
    --server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agreement-id` | **Yes** | string | -- | Agreement ID |
| `--server-id` | **Yes** | string | -- | Server ID |

**Output:** None on success.

---

### 5.3 `describe-agreement`

Gets details about an agreement.

**Synopsis:**
```bash
aws transfer describe-agreement \
    --agreement-id <value> \
    --server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agreement-id` | **Yes** | string | -- | Agreement ID |
| `--server-id` | **Yes** | string | -- | Server ID |

**Output Schema:**
```json
{
    "Agreement": {
        "Arn": "string",
        "AgreementId": "string",
        "Description": "string",
        "Status": "ACTIVE|INACTIVE",
        "ServerId": "string",
        "LocalProfileId": "string",
        "PartnerProfileId": "string",
        "BaseDirectory": "string",
        "AccessRole": "string",
        "Tags": [{"Key": "string", "Value": "string"}],
        "PreserveFilename": "ENABLED|DISABLED",
        "EnforceMessageSigning": "ENABLED|DISABLED",
        "CustomDirectories": {
            "FailedFilesDirectory": "string",
            "MdnFilesDirectory": "string",
            "PayloadFilesDirectory": "string",
            "StatusFilesDirectory": "string",
            "TemporaryFilesDirectory": "string"
        }
    }
}
```

---

### 5.4 `list-agreements`

Lists agreements for a server. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-agreements \
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
    "Agreements": [
        {
            "Arn": "string",
            "AgreementId": "string",
            "Description": "string",
            "Status": "ACTIVE|INACTIVE",
            "ServerId": "string",
            "LocalProfileId": "string",
            "PartnerProfileId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `update-agreement`

Updates an agreement.

**Synopsis:**
```bash
aws transfer update-agreement \
    --agreement-id <value> \
    --server-id <value> \
    [--description <value>] \
    [--status <value>] \
    [--local-profile-id <value>] \
    [--partner-profile-id <value>] \
    [--base-directory <value>] \
    [--access-role <value>] \
    [--preserve-filename <value>] \
    [--enforce-message-signing <value>] \
    [--custom-directories <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "AgreementId": "string"
}
```
