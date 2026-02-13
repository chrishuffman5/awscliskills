# Key Management

### 1.1 `create-key`

Creates a customer-managed KMS key for cryptographic operations.

**Synopsis:**
```bash
aws kms create-key \
    [--policy <value>] \
    [--description <value>] \
    [--key-usage <value>] \
    [--key-spec <value>] \
    [--origin <value>] \
    [--custom-key-store-id <value>] \
    [--xks-key-id <value>] \
    [--multi-region | --no-multi-region] \
    [--bypass-policy-lockout-safety-check | --no-bypass-policy-lockout-safety-check] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy` | No | string | Default key policy | Key policy JSON document (1-131072 chars) |
| `--description` | No | string | `""` | Key description (0-8192 chars) |
| `--key-usage` | No | string | `ENCRYPT_DECRYPT` | Values: `ENCRYPT_DECRYPT`, `SIGN_VERIFY`, `GENERATE_VERIFY_MAC`, `KEY_AGREEMENT` |
| `--key-spec` | No | string | `SYMMETRIC_DEFAULT` | Key type. Symmetric: `SYMMETRIC_DEFAULT`. HMAC: `HMAC_224`, `HMAC_256`, `HMAC_384`, `HMAC_512`. RSA: `RSA_2048`, `RSA_3072`, `RSA_4096`. ECC: `ECC_NIST_P256`, `ECC_NIST_P384`, `ECC_NIST_P521`, `ECC_NIST_EDWARDS25519`, `ECC_SECG_P256K1`. ML-DSA: `ML_DSA_44`, `ML_DSA_65`, `ML_DSA_87`. China: `SM2` |
| `--origin` | No | string | `AWS_KMS` | Key material source: `AWS_KMS`, `EXTERNAL`, `AWS_CLOUDHSM`, `EXTERNAL_KEY_STORE` |
| `--custom-key-store-id` | No | string | -- | Custom key store ID (1-64 chars) for CloudHSM or external key stores |
| `--xks-key-id` | No | string | -- | External key ID in external key manager (1-128 chars) |
| `--multi-region` | No | boolean | `false` | Create a multi-region primary key |
| `--bypass-policy-lockout-safety-check` | No | boolean | `false` | Skip key policy lockout safety check |
| `--tags` | No | list | None | Tags as key-value pairs. Shorthand: `TagKey=string,TagValue=string ...` |

**Output Schema:**
```json
{
    "KeyMetadata": {
        "AWSAccountId": "string",
        "KeyId": "string",
        "Arn": "string",
        "CreationDate": "timestamp",
        "Enabled": true|false,
        "Description": "string",
        "KeyUsage": "ENCRYPT_DECRYPT|SIGN_VERIFY|GENERATE_VERIFY_MAC|KEY_AGREEMENT",
        "KeyState": "Creating|Enabled|Disabled|PendingDeletion|PendingImport|PendingReplicaDeletion|Unavailable|Updating",
        "Origin": "AWS_KMS|EXTERNAL|AWS_CLOUDHSM|EXTERNAL_KEY_STORE",
        "CustomKeyStoreId": "string",
        "CloudHsmClusterId": "string",
        "KeyManager": "AWS|CUSTOMER",
        "KeySpec": "SYMMETRIC_DEFAULT|RSA_2048|RSA_3072|RSA_4096|ECC_NIST_P256|ECC_NIST_P384|ECC_NIST_P521|ECC_NIST_EDWARDS25519|ECC_SECG_P256K1|HMAC_224|HMAC_256|HMAC_384|HMAC_512|SM2|ML_DSA_44|ML_DSA_65|ML_DSA_87",
        "EncryptionAlgorithms": ["SYMMETRIC_DEFAULT|RSAES_OAEP_SHA_1|RSAES_OAEP_SHA_256|SM2PKE"],
        "SigningAlgorithms": ["RSASSA_PSS_SHA_256|..."],
        "KeyAgreementAlgorithms": ["ECDH"],
        "MultiRegion": true|false,
        "MultiRegionConfiguration": {
            "MultiRegionKeyType": "PRIMARY|REPLICA",
            "PrimaryKey": { "Arn": "string", "Region": "string" },
            "ReplicaKeys": [{ "Arn": "string", "Region": "string" }]
        },
        "MacAlgorithms": ["HMAC_SHA_224|HMAC_SHA_256|HMAC_SHA_384|HMAC_SHA_512"],
        "XksKeyConfiguration": { "Id": "string" },
        "CurrentKeyMaterialId": "string"
    }
}
```

---

### 1.2 `describe-key`

Returns detailed metadata about a KMS key.

**Synopsis:**
```bash
aws kms describe-key \
    --key-id <value> \
    [--grant-tokens <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID, key ARN, alias name (`alias/...`), or alias ARN (1-2048 chars) |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items, each 1-8192 chars) |

**Output Schema:**
```json
{
    "KeyMetadata": {
        "AWSAccountId": "string",
        "KeyId": "string",
        "Arn": "string",
        "CreationDate": "timestamp",
        "Enabled": true|false,
        "Description": "string",
        "KeyUsage": "ENCRYPT_DECRYPT|SIGN_VERIFY|GENERATE_VERIFY_MAC|KEY_AGREEMENT",
        "KeyState": "Creating|Enabled|Disabled|PendingDeletion|PendingImport|PendingReplicaDeletion|Unavailable|Updating",
        "DeletionDate": "timestamp",
        "ValidTo": "timestamp",
        "Origin": "AWS_KMS|EXTERNAL|AWS_CLOUDHSM|EXTERNAL_KEY_STORE",
        "CustomKeyStoreId": "string",
        "CloudHsmClusterId": "string",
        "ExpirationModel": "KEY_MATERIAL_EXPIRES|KEY_MATERIAL_DOES_NOT_EXPIRE",
        "KeyManager": "AWS|CUSTOMER",
        "KeySpec": "SYMMETRIC_DEFAULT|RSA_2048|RSA_3072|RSA_4096|ECC_NIST_P256|ECC_NIST_P384|ECC_NIST_P521|ECC_NIST_EDWARDS25519|ECC_SECG_P256K1|HMAC_224|HMAC_256|HMAC_384|HMAC_512|SM2|ML_DSA_44|ML_DSA_65|ML_DSA_87",
        "EncryptionAlgorithms": ["string"],
        "SigningAlgorithms": ["string"],
        "KeyAgreementAlgorithms": ["ECDH"],
        "MultiRegion": true|false,
        "MultiRegionConfiguration": {
            "MultiRegionKeyType": "PRIMARY|REPLICA",
            "PrimaryKey": { "Arn": "string", "Region": "string" },
            "ReplicaKeys": [{ "Arn": "string", "Region": "string" }]
        },
        "PendingDeletionWindowInDays": "integer",
        "MacAlgorithms": ["string"],
        "XksKeyConfiguration": { "Id": "string" },
        "CurrentKeyMaterialId": "string"
    }
}
```

---

### 1.3 `list-keys`

Lists all KMS keys in the caller's account and region. **Paginated.**

**Synopsis:**
```bash
aws kms list-keys \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Keys": [
        {
            "KeyId": "string",
            "KeyArn": "string"
        }
    ],
    "NextMarker": "string",
    "Truncated": true|false
}
```

---

### 1.4 `enable-key`

Sets the key state to Enabled, allowing it to be used for cryptographic operations.

**Synopsis:**
```bash
aws kms enable-key --key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |

**Output:** None

---

### 1.5 `disable-key`

Sets the key state to Disabled, preventing cryptographic operations.

**Synopsis:**
```bash
aws kms disable-key --key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |

**Output:** None

---

### 1.6 `schedule-key-deletion`

Schedules a KMS key for deletion after a waiting period.

**Synopsis:**
```bash
aws kms schedule-key-deletion \
    --key-id <value> \
    [--pending-window-in-days <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--pending-window-in-days` | No | integer | `30` | Waiting period before deletion (7-30 days) |

**Output Schema:**
```json
{
    "KeyId": "string",
    "DeletionDate": "timestamp",
    "KeyState": "PendingDeletion",
    "PendingWindowInDays": "integer"
}
```

---

### 1.7 `cancel-key-deletion`

Cancels scheduled deletion of a KMS key. After cancellation, the key state is Disabled.

**Synopsis:**
```bash
aws kms cancel-key-deletion --key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |

**Output Schema:**
```json
{
    "KeyId": "string"
}
```

---

### 1.8 `update-key-description`

Updates the description of a KMS key.

**Synopsis:**
```bash
aws kms update-key-description \
    --key-id <value> \
    --description <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--description` | **Yes** | string | -- | New description (0-8192 chars) |

**Output:** None

---

### 1.9 `get-key-policy`

Gets the key policy for a KMS key.

**Synopsis:**
```bash
aws kms get-key-policy \
    --key-id <value> \
    [--policy-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--policy-name` | No | string | `default` | Policy name. Only valid value is `default` (1-128 chars) |

**Output Schema:**
```json
{
    "Policy": "string",
    "PolicyName": "string"
}
```

---

### 1.10 `put-key-policy`

Sets the key policy for a KMS key.

**Synopsis:**
```bash
aws kms put-key-policy \
    --key-id <value> \
    --policy <value> \
    [--policy-name <value>] \
    [--bypass-policy-lockout-safety-check | --no-bypass-policy-lockout-safety-check]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--policy` | **Yes** | string | -- | Key policy JSON document (1-131072 chars) |
| `--policy-name` | No | string | `default` | Policy name (1-128 chars) |
| `--bypass-policy-lockout-safety-check` | No | boolean | `false` | Skip lockout safety check |

**Output:** None

---

### 1.11 `list-key-policies`

Lists the names of key policies for a KMS key. **Paginated.**

**Synopsis:**
```bash
aws kms list-key-policies \
    --key-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PolicyNames": ["string"],
    "NextMarker": "string",
    "Truncated": true|false
}
```

---

### 1.12 `get-public-key`

Returns the public key of an asymmetric KMS key.

**Synopsis:**
```bash
aws kms get-public-key \
    --key-id <value> \
    [--grant-tokens <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID, key ARN, alias name, or alias ARN (1-2048 chars) |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |

**Output Schema:**
```json
{
    "KeyId": "string",
    "PublicKey": "blob",
    "KeySpec": "RSA_2048|RSA_3072|RSA_4096|ECC_NIST_P256|ECC_NIST_P384|ECC_NIST_P521|ECC_NIST_EDWARDS25519|ECC_SECG_P256K1|SM2|ML_DSA_44|ML_DSA_65|ML_DSA_87",
    "KeyUsage": "ENCRYPT_DECRYPT|SIGN_VERIFY|KEY_AGREEMENT",
    "EncryptionAlgorithms": ["string"],
    "SigningAlgorithms": ["string"],
    "KeyAgreementAlgorithms": ["ECDH"]
}
```

---
