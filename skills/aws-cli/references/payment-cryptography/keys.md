# Keys

### 1.1 `create-key`

Creates a new encryption key in AWS Payment Cryptography.

**Synopsis:**
```bash
aws payment-cryptography create-key \
    --key-attributes <value> \
    --exportable | --no-exportable \
    [--key-check-value-algorithm <value>] \
    [--enabled | --no-enabled] \
    [--tags <value>] \
    [--derive-key-usage <value>] \
    [--replication-regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-attributes` | **Yes** | structure | -- | Key role, algorithm, and cryptographic operations (immutable after creation) |
| `--exportable` / `--no-exportable` | **Yes** | boolean | -- | Whether the key is exportable from the service |
| `--key-check-value-algorithm` | No | string | None | KCV algorithm: `CMAC`, `ANSI_X9_24`, `HMAC`, `SHA_1` |
| `--enabled` / `--no-enabled` | No | boolean | true | Enable the key for use |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |
| `--derive-key-usage` | No | string | None | Intended usage of keys derived via ECDH from ECC key pair |
| `--replication-regions` | No | list(string) | None | AWS Regions for key replication |

**Key Attributes Structure:**
```json
{
    "KeyUsage": "TR31_B0_BASE_DERIVATION_KEY|TR31_C0_CARD_VERIFICATION_KEY|TR31_D0_SYMMETRIC_DATA_ENCRYPTION_KEY|TR31_P0_PIN_ENCRYPTION_KEY|TR31_K0_KEY_ENCRYPTION_KEY|...",
    "KeyClass": "SYMMETRIC_KEY|ASYMMETRIC_KEY_PAIR|PRIVATE_KEY|PUBLIC_KEY",
    "KeyAlgorithm": "TDES_2KEY|TDES_3KEY|AES_128|AES_192|AES_256|RSA_2048|RSA_3072|RSA_4096|ECC_NIST_P256|ECC_NIST_P384|ECC_NIST_P521|HMAC_SHA256|HMAC_SHA384|HMAC_SHA512",
    "KeyModesOfUse": {
        "Encrypt": true|false,
        "Decrypt": true|false,
        "Wrap": true|false,
        "Unwrap": true|false,
        "Generate": true|false,
        "Sign": true|false,
        "Verify": true|false,
        "DeriveKey": true|false,
        "NoRestrictions": true|false
    }
}
```

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": {
            "KeyUsage": "string",
            "KeyClass": "string",
            "KeyAlgorithm": "string",
            "KeyModesOfUse": {
                "Encrypt": "boolean",
                "Decrypt": "boolean",
                "Wrap": "boolean",
                "Unwrap": "boolean",
                "Generate": "boolean",
                "Sign": "boolean",
                "Verify": "boolean",
                "DeriveKey": "boolean",
                "NoRestrictions": "boolean"
            }
        },
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string",
        "Enabled": "boolean",
        "Exportable": "boolean",
        "KeyState": "CREATE_IN_PROGRESS|CREATE_COMPLETE|DELETE_PENDING|DELETE_COMPLETE",
        "KeyOrigin": "AWS_PAYMENT_CRYPTOGRAPHY|EXTERNAL",
        "CreateTimestamp": "timestamp",
        "UsageStartTimestamp": "timestamp",
        "UsageStopTimestamp": "timestamp",
        "DeletePendingTimestamp": "timestamp",
        "DeleteTimestamp": "timestamp",
        "DeriveKeyUsage": "string",
        "MultiRegionKeyType": "PRIMARY|REPLICA",
        "PrimaryRegion": "string",
        "ReplicationStatus": {
            "region": {
                "Status": "IN_PROGRESS|SYNCHRONIZED|FAILED|DELETE_IN_PROGRESS",
                "StatusMessage": "string"
            }
        },
        "UsingDefaultReplicationRegions": "boolean"
    }
}
```

---

### 1.2 `delete-key`

Schedules a key for deletion after a waiting period (default 7 days). Use `restore-key` to cancel.

**Synopsis:**
```bash
aws payment-cryptography delete-key \
    --key-identifier <value> \
    [--delete-key-in-days <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the key to delete |
| `--delete-key-in-days` | No | integer | 7 | Waiting period (3-180 days) before permanent deletion |

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": { "KeyUsage": "string", "KeyClass": "string", "KeyAlgorithm": "string", "KeyModesOfUse": {} },
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string",
        "Enabled": "boolean",
        "Exportable": "boolean",
        "KeyState": "DELETE_PENDING",
        "KeyOrigin": "string",
        "CreateTimestamp": "timestamp",
        "DeletePendingTimestamp": "timestamp"
    }
}
```

---

### 1.3 `get-key`

Retrieves detailed information about a key.

**Synopsis:**
```bash
aws payment-cryptography get-key \
    --key-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the key |

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": {
            "KeyUsage": "string",
            "KeyClass": "string",
            "KeyAlgorithm": "string",
            "KeyModesOfUse": {}
        },
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string",
        "Enabled": "boolean",
        "Exportable": "boolean",
        "KeyState": "string",
        "KeyOrigin": "string",
        "CreateTimestamp": "timestamp",
        "UsageStartTimestamp": "timestamp",
        "UsageStopTimestamp": "timestamp",
        "DeletePendingTimestamp": "timestamp",
        "DeleteTimestamp": "timestamp",
        "DeriveKeyUsage": "string",
        "MultiRegionKeyType": "string",
        "PrimaryRegion": "string",
        "ReplicationStatus": {},
        "UsingDefaultReplicationRegions": "boolean"
    }
}
```

---

### 1.4 `list-keys`

Lists all keys in the account. **Paginated operation.**

**Synopsis:**
```bash
aws payment-cryptography list-keys \
    [--key-state <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-state` | No | string | None | Filter by state: `CREATE_IN_PROGRESS`, `CREATE_COMPLETE`, `DELETE_PENDING`, `DELETE_COMPLETE` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Keys": [
        {
            "KeyArn": "string",
            "KeyState": "string",
            "KeyAttributes": {
                "KeyUsage": "string",
                "KeyClass": "string",
                "KeyAlgorithm": "string",
                "KeyModesOfUse": {}
            },
            "KeyCheckValue": "string",
            "Exportable": "boolean",
            "Enabled": "boolean",
            "MultiRegionKeyType": "PRIMARY|REPLICA",
            "PrimaryRegion": "string",
            "CreateTimestamp": "timestamp",
            "UsageStopTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `start-key-usage`

Enables a key that was previously disabled, allowing it to be used for cryptographic operations.

**Synopsis:**
```bash
aws payment-cryptography start-key-usage \
    --key-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the key to enable |

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": {},
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string",
        "Enabled": true,
        "Exportable": "boolean",
        "KeyState": "string",
        "KeyOrigin": "string",
        "CreateTimestamp": "timestamp",
        "UsageStartTimestamp": "timestamp"
    }
}
```

---

### 1.6 `stop-key-usage`

Disables a key, preventing it from being used for cryptographic operations. Reversible via `start-key-usage`.

**Synopsis:**
```bash
aws payment-cryptography stop-key-usage \
    --key-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the key to disable |

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": {},
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string",
        "Enabled": false,
        "Exportable": "boolean",
        "KeyState": "string",
        "KeyOrigin": "string",
        "CreateTimestamp": "timestamp",
        "UsageStopTimestamp": "timestamp"
    }
}
```

---

### 1.7 `restore-key`

Cancels a scheduled key deletion, returning the key to `CREATE_COMPLETE` state.

**Synopsis:**
```bash
aws payment-cryptography restore-key \
    --key-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the key to restore |

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": {},
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string",
        "Enabled": "boolean",
        "Exportable": "boolean",
        "KeyState": "CREATE_COMPLETE",
        "KeyOrigin": "string",
        "CreateTimestamp": "timestamp"
    }
}
```

---

### 1.8 `get-public-key-certificate`

Gets the public key certificate for an asymmetric key pair in PEM format.

**Synopsis:**
```bash
aws payment-cryptography get-public-key-certificate \
    --key-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the asymmetric key pair |

**Output Schema:**
```json
{
    "KeyCertificate": "string",
    "KeyCertificateChain": "string"
}
```

---

### 1.9 `get-certificate-signing-request`

Generates a Certificate Signing Request (CSR) for an asymmetric key.

**Synopsis:**
```bash
aws payment-cryptography get-certificate-signing-request \
    --key-identifier <value> \
    --signing-algorithm <value> \
    --certificate-subject <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the asymmetric key |
| `--signing-algorithm` | **Yes** | string | -- | Signing algorithm: `SHA224`, `SHA256`, `SHA384`, `SHA512` |
| `--certificate-subject` | **Yes** | structure | -- | CSR metadata (see below) |

**Certificate Subject Structure:**
```json
{
    "CommonName": "string",
    "OrganizationUnit": "string",
    "Organization": "string",
    "City": "string",
    "Country": "string",
    "StateOrProvince": "string",
    "EmailAddress": "string"
}
```

**Output Schema:**
```json
{
    "CertificateSigningRequest": "string"
}
```
