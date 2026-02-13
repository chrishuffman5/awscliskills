# Import Key Material

### 8.1 `get-parameters-for-import`

Returns the public wrapping key and import token needed to import key material.

**Synopsis:**
```bash
aws kms get-parameters-for-import \
    --key-id <value> \
    --wrapping-algorithm <value> \
    --wrapping-key-spec <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN with `EXTERNAL` origin (1-2048 chars) |
| `--wrapping-algorithm` | **Yes** | string | -- | Values: `RSAES_PKCS1_V1_5` (deprecated), `RSAES_OAEP_SHA_1`, `RSAES_OAEP_SHA_256`, `RSA_AES_KEY_WRAP_SHA_1`, `RSA_AES_KEY_WRAP_SHA_256`, `SM2PKE` |
| `--wrapping-key-spec` | **Yes** | string | -- | Values: `RSA_2048`, `RSA_3072`, `RSA_4096`, `SM2` |

**Output Schema:**
```json
{
    "KeyId": "string",
    "ImportToken": "blob",
    "PublicKey": "blob",
    "ParametersValidTo": "timestamp"
}
```

---

### 8.2 `import-key-material`

Imports key material into a KMS key that was created with `EXTERNAL` origin.

**Synopsis:**
```bash
aws kms import-key-material \
    --key-id <value> \
    --import-token <value> \
    --encrypted-key-material <value> \
    [--valid-to <value>] \
    [--expiration-model <value>] \
    [--import-type <value>] \
    [--key-material-description <value>] \
    [--key-material-id <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN with `EXTERNAL` origin (1-2048 chars) |
| `--import-token` | **Yes** | blob | -- | Import token from `get-parameters-for-import` (1-6144 bytes) |
| `--encrypted-key-material` | **Yes** | blob | -- | Encrypted key material (1-6144 bytes). Use `fileb://` for binary |
| `--valid-to` | No | timestamp | -- | Expiration date. Required when `--expiration-model` is `KEY_MATERIAL_EXPIRES` |
| `--expiration-model` | No | string | `KEY_MATERIAL_EXPIRES` | Values: `KEY_MATERIAL_EXPIRES`, `KEY_MATERIAL_DOES_NOT_EXPIRE` |
| `--import-type` | No | string | auto | Values: `NEW_KEY_MATERIAL`, `EXISTING_KEY_MATERIAL` |
| `--key-material-description` | No | string | -- | Description for imported material (0-256 chars) |
| `--key-material-id` | No | string | -- | ID of key material being re-imported (64 hex chars) |

**Output Schema:**
```json
{
    "KeyId": "string",
    "KeyMaterialId": "string"
}
```

---

### 8.3 `delete-imported-key-material`

Deletes imported key material from a KMS key, making the key unusable. Key state changes to `PendingImport`.

**Synopsis:**
```bash
aws kms delete-imported-key-material --key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |

**Output:** None

---
