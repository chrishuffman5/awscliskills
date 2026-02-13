# Cryptographic Operations

### 2.1 `encrypt`

Encrypts plaintext using a KMS key.

**Synopsis:**
```bash
aws kms encrypt \
    --key-id <value> \
    --plaintext <value> \
    [--encryption-context <value>] \
    [--grant-tokens <value>] \
    [--encryption-algorithm <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID, key ARN, alias name, or alias ARN (1-2048 chars) |
| `--plaintext` | **Yes** | blob | -- | Data to encrypt. Max 4096 bytes for symmetric; varies for asymmetric. Use `fileb://` for binary files |
| `--encryption-context` | No | map | None | Key-value pairs for additional authenticated data (symmetric keys only). Shorthand: `Key1=string,Key2=string` |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--encryption-algorithm` | No | string | `SYMMETRIC_DEFAULT` | Values: `SYMMETRIC_DEFAULT`, `RSAES_OAEP_SHA_1`, `RSAES_OAEP_SHA_256`, `SM2PKE`. Required for asymmetric keys |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "CiphertextBlob": "blob",
    "KeyId": "string",
    "EncryptionAlgorithm": "SYMMETRIC_DEFAULT|RSAES_OAEP_SHA_1|RSAES_OAEP_SHA_256|SM2PKE"
}
```

---

### 2.2 `decrypt`

Decrypts ciphertext that was encrypted by a KMS key.

**Synopsis:**
```bash
aws kms decrypt \
    --ciphertext-blob <value> \
    [--key-id <value>] \
    [--encryption-context <value>] \
    [--grant-tokens <value>] \
    [--encryption-algorithm <value>] \
    [--recipient <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ciphertext-blob` | **Yes** | blob | -- | Ciphertext to decrypt (1-6144 bytes). Use `fileb://` for binary files |
| `--key-id` | No | string | auto-detected | Key ID, ARN, alias name, or alias ARN. Required for asymmetric keys; recommended for symmetric |
| `--encryption-context` | No | map | None | Must match the context used during encryption (symmetric keys only) |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--encryption-algorithm` | No | string | `SYMMETRIC_DEFAULT` | Required for asymmetric keys. Must match encryption algorithm |
| `--recipient` | No | structure | None | Nitro Enclave attestation document |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "KeyId": "string",
    "Plaintext": "blob",
    "EncryptionAlgorithm": "SYMMETRIC_DEFAULT|RSAES_OAEP_SHA_1|RSAES_OAEP_SHA_256|SM2PKE",
    "CiphertextForRecipient": "blob",
    "KeyMaterialId": "string"
}
```

---

### 2.3 `re-encrypt`

Decrypts ciphertext and re-encrypts under a different KMS key entirely within KMS.

**Synopsis:**
```bash
aws kms re-encrypt \
    --ciphertext-blob <value> \
    --destination-key-id <value> \
    [--source-key-id <value>] \
    [--source-encryption-context <value>] \
    [--destination-encryption-context <value>] \
    [--source-encryption-algorithm <value>] \
    [--destination-encryption-algorithm <value>] \
    [--grant-tokens <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ciphertext-blob` | **Yes** | blob | -- | Ciphertext to re-encrypt (1-6144 bytes) |
| `--destination-key-id` | **Yes** | string | -- | Destination key ID, ARN, alias name, or alias ARN (1-2048 chars) |
| `--source-key-id` | No | string | auto-detected | Source key. Required for asymmetric source keys |
| `--source-encryption-context` | No | map | None | Encryption context used with the source key |
| `--destination-encryption-context` | No | map | None | Encryption context for the destination key (symmetric only) |
| `--source-encryption-algorithm` | No | string | `SYMMETRIC_DEFAULT` | Algorithm used for source encryption |
| `--destination-encryption-algorithm` | No | string | `SYMMETRIC_DEFAULT` | Algorithm for destination encryption |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "CiphertextBlob": "blob",
    "SourceKeyId": "string",
    "KeyId": "string",
    "SourceEncryptionAlgorithm": "SYMMETRIC_DEFAULT|RSAES_OAEP_SHA_1|RSAES_OAEP_SHA_256|SM2PKE",
    "DestinationEncryptionAlgorithm": "SYMMETRIC_DEFAULT|RSAES_OAEP_SHA_1|RSAES_OAEP_SHA_256|SM2PKE",
    "SourceKeyMaterialId": "string",
    "DestinationKeyMaterialId": "string"
}
```

---

### 2.4 `generate-data-key`

Returns a unique symmetric data key with both plaintext and encrypted copies for envelope encryption.

**Synopsis:**
```bash
aws kms generate-data-key \
    --key-id <value> \
    [--encryption-context <value>] \
    [--number-of-bytes <value>] \
    [--key-spec <value>] \
    [--grant-tokens <value>] \
    [--recipient <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Symmetric encryption key ID, ARN, alias name, or alias ARN (1-2048 chars) |
| `--encryption-context` | No | map | None | Additional authenticated data key-value pairs |
| `--number-of-bytes` | No | integer | -- | Data key length in bytes (1-1024). Use `--key-spec` or `--number-of-bytes`, not both |
| `--key-spec` | No | string | -- | Data key length: `AES_128` or `AES_256`. Use `--key-spec` or `--number-of-bytes`, not both |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--recipient` | No | structure | None | Nitro Enclave attestation document |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "CiphertextBlob": "blob",
    "Plaintext": "blob",
    "KeyId": "string",
    "CiphertextForRecipient": "blob",
    "KeyMaterialId": "string"
}
```

---

### 2.5 `generate-data-key-without-plaintext`

Returns an encrypted data key (no plaintext copy). Use when you only need the encrypted key for later decryption.

**Synopsis:**
```bash
aws kms generate-data-key-without-plaintext \
    --key-id <value> \
    [--encryption-context <value>] \
    [--key-spec <value>] \
    [--number-of-bytes <value>] \
    [--grant-tokens <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Symmetric encryption key ID, ARN, alias name, or alias ARN (1-2048 chars) |
| `--encryption-context` | No | map | None | Additional authenticated data |
| `--key-spec` | No | string | -- | `AES_128` or `AES_256` |
| `--number-of-bytes` | No | integer | -- | Data key length (1-1024 bytes) |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "CiphertextBlob": "blob",
    "KeyId": "string",
    "KeyMaterialId": "string"
}
```

---

### 2.6 `generate-data-key-pair`

Generates an asymmetric data key pair. Returns plaintext public key, plaintext private key, and encrypted private key.

**Synopsis:**
```bash
aws kms generate-data-key-pair \
    --key-id <value> \
    --key-pair-spec <value> \
    [--encryption-context <value>] \
    [--grant-tokens <value>] \
    [--recipient <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Symmetric encryption key (1-2048 chars) |
| `--key-pair-spec` | **Yes** | string | -- | Values: `RSA_2048`, `RSA_3072`, `RSA_4096`, `ECC_NIST_P256`, `ECC_NIST_P384`, `ECC_NIST_P521`, `ECC_SECG_P256K1`, `ECC_NIST_EDWARDS25519`, `SM2` |
| `--encryption-context` | No | map | None | Additional authenticated data |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--recipient` | No | structure | None | Nitro Enclave attestation document |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "PrivateKeyCiphertextBlob": "blob",
    "PrivateKeyPlaintext": "blob",
    "PublicKey": "blob",
    "KeyId": "string",
    "KeyPairSpec": "string",
    "CiphertextForRecipient": "blob",
    "KeyMaterialId": "string"
}
```

---

### 2.7 `generate-data-key-pair-without-plaintext`

Generates an asymmetric data key pair returning only the encrypted private key and plaintext public key.

**Synopsis:**
```bash
aws kms generate-data-key-pair-without-plaintext \
    --key-id <value> \
    --key-pair-spec <value> \
    [--encryption-context <value>] \
    [--grant-tokens <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Symmetric encryption key (1-2048 chars) |
| `--key-pair-spec` | **Yes** | string | -- | Values: `RSA_2048`, `RSA_3072`, `RSA_4096`, `ECC_NIST_P256`, `ECC_NIST_P384`, `ECC_NIST_P521`, `ECC_SECG_P256K1`, `ECC_NIST_EDWARDS25519`, `SM2` |
| `--encryption-context` | No | map | None | Additional authenticated data |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "PrivateKeyCiphertextBlob": "blob",
    "PublicKey": "blob",
    "KeyId": "string",
    "KeyPairSpec": "string",
    "KeyMaterialId": "string"
}
```

---

### 2.8 `generate-random`

Returns a random byte string. Does not use a KMS key.

**Synopsis:**
```bash
aws kms generate-random \
    [--number-of-bytes <value>] \
    [--custom-key-store-id <value>] \
    [--recipient <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--number-of-bytes` | No | integer | -- | Length of random byte string (1-1024 bytes) |
| `--custom-key-store-id` | No | string | -- | Generate random bytes from a CloudHSM cluster |
| `--recipient` | No | structure | None | Nitro Enclave attestation document |

**Output Schema:**
```json
{
    "Plaintext": "blob",
    "CiphertextForRecipient": "blob"
}
```

---

### 2.9 `sign`

Creates a digital signature for a message using an asymmetric KMS key.

**Synopsis:**
```bash
aws kms sign \
    --key-id <value> \
    --message <value> \
    --signing-algorithm <value> \
    [--message-type <value>] \
    [--grant-tokens <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Asymmetric key ID, ARN, alias name, or alias ARN with `SIGN_VERIFY` usage (1-2048 chars) |
| `--message` | **Yes** | blob | -- | Message or digest to sign (1-4096 bytes). Use `fileb://` for binary |
| `--signing-algorithm` | **Yes** | string | -- | Values: `RSASSA_PSS_SHA_256`, `RSASSA_PSS_SHA_384`, `RSASSA_PSS_SHA_512`, `RSASSA_PKCS1_V1_5_SHA_256`, `RSASSA_PKCS1_V1_5_SHA_384`, `RSASSA_PKCS1_V1_5_SHA_512`, `ECDSA_SHA_256`, `ECDSA_SHA_384`, `ECDSA_SHA_512`, `SM2DSA`, `ML_DSA_SHAKE_256`, `ED25519_SHA_512`, `ED25519_PH_SHA_512` |
| `--message-type` | No | string | `RAW` | Values: `RAW`, `DIGEST`, `EXTERNAL_MU` |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "KeyId": "string",
    "Signature": "blob",
    "SigningAlgorithm": "string"
}
```

---

### 2.10 `verify`

Verifies a digital signature created by the Sign operation.

**Synopsis:**
```bash
aws kms verify \
    --key-id <value> \
    --message <value> \
    --signature <value> \
    --signing-algorithm <value> \
    [--message-type <value>] \
    [--grant-tokens <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Asymmetric key ID, ARN, alias name, or alias ARN (1-2048 chars) |
| `--message` | **Yes** | blob | -- | Original message or digest (1-4096 bytes) |
| `--signature` | **Yes** | blob | -- | Signature to verify (1-6144 bytes). Use `fileb://` for binary |
| `--signing-algorithm` | **Yes** | string | -- | Must match algorithm used to sign. Same values as `sign` |
| `--message-type` | No | string | `RAW` | Values: `RAW`, `DIGEST`, `EXTERNAL_MU` |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "KeyId": "string",
    "SignatureValid": true|false,
    "SigningAlgorithm": "string"
}
```

---

### 2.11 `generate-mac`

Generates an HMAC for a message using an HMAC KMS key.

**Synopsis:**
```bash
aws kms generate-mac \
    --message <value> \
    --key-id <value> \
    --mac-algorithm <value> \
    [--grant-tokens <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--message` | **Yes** | blob | -- | Message to hash (1-4096 bytes). Use `fileb://` for binary |
| `--key-id` | **Yes** | string | -- | HMAC key ID, ARN, alias name, or alias ARN with `GENERATE_VERIFY_MAC` usage (1-2048 chars) |
| `--mac-algorithm` | **Yes** | string | -- | Values: `HMAC_SHA_224`, `HMAC_SHA_256`, `HMAC_SHA_384`, `HMAC_SHA_512` |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "Mac": "blob",
    "MacAlgorithm": "HMAC_SHA_224|HMAC_SHA_256|HMAC_SHA_384|HMAC_SHA_512",
    "KeyId": "string"
}
```

---

### 2.12 `verify-mac`

Verifies an HMAC for a message using an HMAC KMS key.

**Synopsis:**
```bash
aws kms verify-mac \
    --message <value> \
    --key-id <value> \
    --mac-algorithm <value> \
    --mac <value> \
    [--grant-tokens <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--message` | **Yes** | blob | -- | Original message (1-4096 bytes) |
| `--key-id` | **Yes** | string | -- | HMAC key ID, ARN, alias name, or alias ARN (1-2048 chars) |
| `--mac-algorithm` | **Yes** | string | -- | Values: `HMAC_SHA_224`, `HMAC_SHA_256`, `HMAC_SHA_384`, `HMAC_SHA_512` |
| `--mac` | **Yes** | blob | -- | HMAC to verify (1-6144 bytes). Use `fileb://` for binary |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "KeyId": "string",
    "MacValid": true|false,
    "MacAlgorithm": "HMAC_SHA_224|HMAC_SHA_256|HMAC_SHA_384|HMAC_SHA_512"
}
```

---

### 2.13 `derive-shared-secret`

Derives a shared secret using ECDH key agreement with an asymmetric KMS key pair.

**Synopsis:**
```bash
aws kms derive-shared-secret \
    --key-id <value> \
    --key-agreement-algorithm <value> \
    --public-key <value> \
    [--grant-tokens <value>] \
    [--recipient <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Asymmetric ECC/SM2 key with `KEY_AGREEMENT` usage (1-2048 chars) |
| `--key-agreement-algorithm` | **Yes** | string | -- | Only valid value: `ECDH` |
| `--public-key` | **Yes** | blob | -- | Peer's public key in DER-encoded X.509 format (1-8192 bytes) |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--recipient` | No | structure | None | Nitro Enclave attestation document |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "KeyId": "string",
    "SharedSecret": "blob",
    "CiphertextForRecipient": "blob",
    "KeyAgreementAlgorithm": "ECDH",
    "KeyOrigin": "AWS_KMS|EXTERNAL"
}
```

---
