# DNSSEC

### 5.1 `enable-hosted-zone-dnssec`

Enables DNSSEC signing in a hosted zone. A key signing key (KSK) must exist first.

**Synopsis:**
```bash
aws route53 enable-hosted-zone-dnssec \
    --hosted-zone-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    }
}
```

---

### 5.2 `disable-hosted-zone-dnssec`

Disables DNSSEC signing in a hosted zone. Remove the DS record from the parent zone first to avoid a DNSSEC validation failure.

**Synopsis:**
```bash
aws route53 disable-hosted-zone-dnssec \
    --hosted-zone-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    }
}
```

---

### 5.3 `get-dnssec`

Gets information about DNSSEC for a hosted zone, including key signing keys.

**Synopsis:**
```bash
aws route53 get-dnssec \
    --hosted-zone-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |

**Output Schema:**
```json
{
    "Status": {
        "ServeSignature": "string",
        "StatusMessage": "string"
    },
    "KeySigningKeys": [
        {
            "Name": "string",
            "KmsArn": "string",
            "Flag": "integer",
            "SigningAlgorithmMnemonic": "string",
            "SigningAlgorithmType": "integer",
            "DigestAlgorithmMnemonic": "string",
            "DigestAlgorithmType": "integer",
            "KeyTag": "integer",
            "DigestValue": "string",
            "PublicKey": "string",
            "DSRecord": "string",
            "DNSKEYRecord": "string",
            "Status": "ACTIVE|INACTIVE|DELETING|ACTION_NEEDED|INTERNAL_FAILURE",
            "StatusMessage": "string",
            "CreatedDate": "timestamp",
            "LastModifiedDate": "timestamp"
        }
    ]
}
```

---

### 5.4 `create-key-signing-key`

Creates a new key signing key (KSK) for DNSSEC in a hosted zone. Maximum 2 KSKs per hosted zone.

**Synopsis:**
```bash
aws route53 create-key-signing-key \
    --caller-reference <value> \
    --hosted-zone-id <value> \
    --key-management-service-arn <value> \
    --name <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--caller-reference` | **Yes** | string | -- | Unique string for retry safety (1-128 chars) |
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--key-management-service-arn` | **Yes** | string | -- | KMS key ARN. Must be ECC_NIST_P256, Sign and Verify usage |
| `--name` | **Yes** | string | -- | KSK name (3-128 chars): letters, numbers, underscores |
| `--status` | **Yes** | string | -- | `ACTIVE` or `INACTIVE` |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    },
    "KeySigningKey": {
        "Name": "string",
        "KmsArn": "string",
        "Flag": "integer",
        "SigningAlgorithmMnemonic": "string",
        "SigningAlgorithmType": "integer",
        "DigestAlgorithmMnemonic": "string",
        "DigestAlgorithmType": "integer",
        "KeyTag": "integer",
        "DigestValue": "string",
        "PublicKey": "string",
        "DSRecord": "string",
        "DNSKEYRecord": "string",
        "Status": "ACTIVE|INACTIVE|DELETING|ACTION_NEEDED|INTERNAL_FAILURE",
        "StatusMessage": "string",
        "CreatedDate": "timestamp",
        "LastModifiedDate": "timestamp"
    },
    "Location": "string"
}
```

---

### 5.5 `delete-key-signing-key`

Deletes a key signing key. Must be deactivated first.

**Synopsis:**
```bash
aws route53 delete-key-signing-key \
    --hosted-zone-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--name` | **Yes** | string | -- | KSK name (3-128 chars) |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    }
}
```

---

### 5.6 `activate-key-signing-key`

Activates a key signing key so it can be used for DNSSEC signing.

**Synopsis:**
```bash
aws route53 activate-key-signing-key \
    --hosted-zone-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--name` | **Yes** | string | -- | KSK name (3-128 chars) |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    }
}
```

---

### 5.7 `deactivate-key-signing-key`

Deactivates a key signing key. Must deactivate before deleting.

**Synopsis:**
```bash
aws route53 deactivate-key-signing-key \
    --hosted-zone-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--name` | **Yes** | string | -- | KSK name (3-128 chars) |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    }
}
```

---
