# SMB Settings

### 3.1 `describe-smb-settings`

Returns SMB-related settings for a gateway including Active Directory status, security strategy, and local groups.

**Synopsis:**
```bash
aws storagegateway describe-smb-settings \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN (50-500 chars) |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "DomainName": "string",
    "ActiveDirectoryStatus": "ACCESS_DENIED|DETACHED|JOINED|JOINING|NETWORK_ERROR|TIMEOUT|UNKNOWN_ERROR|INSUFFICIENT_PERMISSIONS",
    "SMBGuestPasswordSet": "boolean",
    "SMBSecurityStrategy": "ClientSpecified|MandatorySigning|MandatoryEncryption|MandatoryEncryptionNoAes128",
    "FileSharesVisible": "boolean",
    "SMBLocalGroups": {
        "GatewayAdmins": ["string"]
    }
}
```

---

### 3.2 `join-domain`

Joins a gateway to an Active Directory domain. Required for SMB file shares with AD authentication.

**Synopsis:**
```bash
aws storagegateway join-domain \
    --gateway-arn <value> \
    --domain-name <value> \
    --user-name <value> \
    --password <value> \
    [--organizational-unit <value>] \
    [--domain-controllers <value>] \
    [--timeout-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--domain-name` | **Yes** | string | -- | AD domain name (1-1024 chars) |
| `--user-name` | **Yes** | string | -- | AD user with domain join privileges (1-1024 chars) |
| `--password` | **Yes** | string | -- | AD user password (1-1024 chars) |
| `--organizational-unit` | No | string | None | OU for the gateway computer object (1-1024 chars) |
| `--domain-controllers` | No | list(string) | None | IP addresses of domain controllers |
| `--timeout-in-seconds` | No | integer | None | Timeout for join operation (0-3600) |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "ActiveDirectoryStatus": "ACCESS_DENIED|DETACHED|JOINED|JOINING|NETWORK_ERROR|TIMEOUT|UNKNOWN_ERROR|INSUFFICIENT_PERMISSIONS"
}
```

---

### 3.3 `set-smb-guest-password`

Sets the SMB guest access password for an S3 File Gateway. Used when authentication is set to `GuestAccess`.

**Synopsis:**
```bash
aws storagegateway set-smb-guest-password \
    --gateway-arn <value> \
    --password <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--password` | **Yes** | string | -- | Guest password (6-512 chars) |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 3.4 `update-smb-security-strategy`

Updates the SMB security strategy for a gateway. Controls the minimum SMB protocol version and encryption requirements.

**Synopsis:**
```bash
aws storagegateway update-smb-security-strategy \
    --gateway-arn <value> \
    --smb-security-strategy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--smb-security-strategy` | **Yes** | string | -- | Strategy: `ClientSpecified`, `MandatorySigning`, `MandatoryEncryption`, `MandatoryEncryptionNoAes128` |

**SMB Security Strategies:**

| Strategy | Description |
|----------|-------------|
| `ClientSpecified` | SMB 2.1+ clients may negotiate any settings |
| `MandatorySigning` | SMB 2.1+ with packet signing required |
| `MandatoryEncryption` | SMB 3.0+ with AES-128-CCM encryption required |
| `MandatoryEncryptionNoAes128` | SMB 3.1.1+ with AES-128-GCM encryption, no AES-128-CCM |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 3.5 `update-smb-file-share-visibility`

Controls whether SMB file shares on a gateway are visible when listing shares.

**Synopsis:**
```bash
aws storagegateway update-smb-file-share-visibility \
    --gateway-arn <value> \
    --file-shares-visible | --no-file-shares-visible \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--file-shares-visible` | **Yes** | boolean | -- | Whether file shares are visible in share listing |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 3.6 `update-smb-local-groups`

Updates the list of Active Directory users and groups that have special permissions for SMB file shares.

**Synopsis:**
```bash
aws storagegateway update-smb-local-groups \
    --gateway-arn <value> \
    --smb-local-groups <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--smb-local-groups` | **Yes** | structure | -- | Local groups: `GatewayAdmins=["DOMAIN\\User1","@DOMAIN\\Group1"]` |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```
