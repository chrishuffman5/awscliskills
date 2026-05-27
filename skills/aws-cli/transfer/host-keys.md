# Host Keys

Commands for managing SFTP host keys in Transfer Family.

### 8.1 `import-host-key`

Imports a host key for an SFTP-enabled server.

**Synopsis:**
```bash
aws transfer import-host-key \
    --server-id <value> \
    --host-key-body <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--host-key-body` | **Yes** | string | -- | SSH private key (RSA/ECDSA/ED25519, max 4096 chars) |
| `--description` | No | string | None | Description (max 200 chars) |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "ServerId": "string",
    "HostKeyId": "string"
}
```

---

### 8.2 `delete-host-key`

Deletes a host key from a server.

**Synopsis:**
```bash
aws transfer delete-host-key \
    --server-id <value> \
    --host-key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--host-key-id` | **Yes** | string | -- | Host key ID |

**Output:** None on success.

---

### 8.3 `describe-host-key`

Gets details about a host key.

**Synopsis:**
```bash
aws transfer describe-host-key \
    --server-id <value> \
    --host-key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--host-key-id` | **Yes** | string | -- | Host key ID |

**Output Schema:**
```json
{
    "HostKey": {
        "Arn": "string",
        "HostKeyId": "string",
        "HostKeyFingerprint": "string",
        "Description": "string",
        "Type": "string",
        "DateImported": "timestamp",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 8.4 `list-host-keys`

Lists host keys for a server.

**Synopsis:**
```bash
aws transfer list-host-keys \
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
    "HostKeys": [
        {
            "Arn": "string",
            "HostKeyId": "string",
            "HostKeyFingerprint": "string",
            "Description": "string",
            "Type": "string",
            "DateImported": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-host-key`

Updates a host key description.

**Synopsis:**
```bash
aws transfer update-host-key \
    --server-id <value> \
    --host-key-id <value> \
    --description <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--host-key-id` | **Yes** | string | -- | Host key ID |
| `--description` | **Yes** | string | -- | New description (max 200 chars) |

**Output Schema:**
```json
{
    "ServerId": "string",
    "HostKeyId": "string"
}
```
