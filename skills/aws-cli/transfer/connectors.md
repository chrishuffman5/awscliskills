# Connectors

Commands for managing SFTP and AS2 connectors in Transfer Family.

### 4.1 `create-connector`

Creates an SFTP or AS2 connector for outbound file transfers.

**Synopsis:**
```bash
aws transfer create-connector \
    --access-role <value> \
    [--url <value>] \
    [--as2-config <value>] \
    [--sftp-config <value>] \
    [--logging-role <value>] \
    [--tags <value>] \
    [--security-policy-name <value>] \
    [--egress-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-role` | **Yes** | string | -- | IAM role ARN for connector access |
| `--url` | No | string | None | Partner endpoint URL (not needed for VPC Lattice) |
| `--as2-config` | No* | structure | None | AS2 connector configuration |
| `--sftp-config` | No* | structure | None | SFTP connector configuration |
| `--logging-role` | No | string | None | IAM role ARN for CloudWatch logging |
| `--tags` | No | list | None | Tags |
| `--security-policy-name` | No | string | None | Security policy name |
| `--egress-config` | No | structure | None | VPC Lattice egress configuration |

*Exactly one of `--as2-config` or `--sftp-config` must be provided.

**AS2 Config (JSON):**
```json
{
    "LocalProfileId": "string",
    "PartnerProfileId": "string",
    "MessageSubject": "string",
    "Compression": "ZLIB|DISABLED",
    "EncryptionAlgorithm": "AES128_CBC|AES192_CBC|AES256_CBC|DES_EDE3_CBC|NONE",
    "SigningAlgorithm": "SHA256|SHA384|SHA512|SHA1|NONE",
    "MdnSigningAlgorithm": "SHA256|SHA384|SHA512|SHA1|NONE|DEFAULT",
    "MdnResponse": "SYNC|NONE|ASYNC",
    "BasicAuthSecretId": "string",
    "PreserveContentType": "ENABLED|DISABLED"
}
```

**SFTP Config (JSON):**
```json
{
    "UserSecretId": "string",
    "TrustedHostKeys": ["string"],
    "MaxConcurrentConnections": "integer"
}
```

**Output Schema:**
```json
{
    "ConnectorId": "string"
}
```

---

### 4.2 `delete-connector`

Deletes a connector.

**Synopsis:**
```bash
aws transfer delete-connector \
    --connector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |

**Output:** None on success.

---

### 4.3 `describe-connector`

Gets details about a connector.

**Synopsis:**
```bash
aws transfer describe-connector \
    --connector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |

**Output Schema:**
```json
{
    "Connector": {
        "Arn": "string",
        "ConnectorId": "string",
        "Url": "string",
        "As2Config": {
            "LocalProfileId": "string",
            "PartnerProfileId": "string",
            "MessageSubject": "string",
            "Compression": "ZLIB|DISABLED",
            "EncryptionAlgorithm": "string",
            "SigningAlgorithm": "string",
            "MdnSigningAlgorithm": "string",
            "MdnResponse": "SYNC|NONE|ASYNC",
            "BasicAuthSecretId": "string",
            "PreserveContentType": "ENABLED|DISABLED"
        },
        "SftpConfig": {
            "UserSecretId": "string",
            "TrustedHostKeys": ["string"],
            "MaxConcurrentConnections": "integer"
        },
        "AccessRole": "string",
        "LoggingRole": "string",
        "Tags": [{"Key": "string", "Value": "string"}],
        "SecurityPolicyName": "string",
        "ServiceManagedEgressIpAddresses": ["string"]
    }
}
```

---

### 4.4 `list-connectors`

Lists all connectors. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-connectors \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "Connectors": [
        {
            "Arn": "string",
            "ConnectorId": "string",
            "Url": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-connector`

Updates connector settings.

**Synopsis:**
```bash
aws transfer update-connector \
    --connector-id <value> \
    [--url <value>] \
    [--as2-config <value>] \
    [--sftp-config <value>] \
    [--access-role <value>] \
    [--logging-role <value>] \
    [--security-policy-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "ConnectorId": "string"
}
```

---

### 4.6 `start-file-transfer`

Starts a file transfer using a connector.

**Synopsis:**
```bash
aws transfer start-file-transfer \
    --connector-id <value> \
    [--send-file-paths <value>] \
    [--retrieve-file-paths <value>] \
    [--local-directory-path <value>] \
    [--remote-directory-path <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |
| `--send-file-paths` | No* | list(string) | None | S3 paths to send (1-10) |
| `--retrieve-file-paths` | No* | list(string) | None | Remote paths to retrieve (1-10) |
| `--local-directory-path` | No | string | None | S3 path for retrieved files |
| `--remote-directory-path` | No | string | None | Remote directory for sent files |

*Provide either `--send-file-paths` or `--retrieve-file-paths`.

**Output Schema:**
```json
{
    "TransferId": "string"
}
```

---

### 4.7 `start-directory-listing`

Lists the contents of a remote directory via a connector.

**Synopsis:**
```bash
aws transfer start-directory-listing \
    --connector-id <value> \
    --remote-directory-path <value> \
    --output-directory-path <value> \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |
| `--remote-directory-path` | **Yes** | string | -- | Remote directory to list |
| `--output-directory-path` | **Yes** | string | -- | S3 path for listing output |
| `--max-items` | No | integer | None | Max items to list |

**Output Schema:**
```json
{
    "ListingId": "string",
    "OutputFileName": "string"
}
```

---

### 4.8 `start-remote-delete`

Deletes files on a remote server via a connector.

**Synopsis:**
```bash
aws transfer start-remote-delete \
    --connector-id <value> \
    --remote-file-paths <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |
| `--remote-file-paths` | **Yes** | list(string) | -- | Remote file paths to delete |

**Output Schema:**
```json
{
    "TransferId": "string"
}
```

---

### 4.9 `start-remote-move`

Moves files on a remote server via a connector.

**Synopsis:**
```bash
aws transfer start-remote-move \
    --connector-id <value> \
    --remote-file-paths <value> \
    --remote-directory-path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |
| `--remote-file-paths` | **Yes** | list(string) | -- | Remote file paths to move |
| `--remote-directory-path` | **Yes** | string | -- | Destination directory on remote server |

**Output Schema:**
```json
{
    "TransferId": "string"
}
```

---

### 4.10 `test-connection`

Tests connector connectivity to the remote server.

**Synopsis:**
```bash
aws transfer test-connection \
    --connector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |

**Output Schema:**
```json
{
    "ConnectorId": "string",
    "Status": "string",
    "StatusMessage": "string"
}
```

---

### 4.11 `list-file-transfer-results`

Lists file transfer results for a connector transfer. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-file-transfer-results \
    --connector-id <value> \
    --transfer-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |
| `--transfer-id` | **Yes** | string | -- | Transfer ID from start-file-transfer |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FileTransferResults": [
        {
            "FilePath": "string",
            "StatusCode": "QUEUED|IN_PROGRESS|COMPLETED|FAILED",
            "FailureCode": "string",
            "FailureMessage": "string"
        }
    ],
    "NextToken": "string"
}
```
