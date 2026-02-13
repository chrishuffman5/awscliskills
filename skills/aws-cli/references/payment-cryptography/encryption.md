# Encryption

### 5.1 `encrypt-data`

Encrypts plaintext data using a symmetric or asymmetric key, DUKPT, or EMV session key.

**Synopsis:**
```bash
aws payment-cryptography-data encrypt-data \
    --key-identifier <value> \
    --plain-text <value> \
    --encryption-attributes <value> \
    [--wrapped-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN of the encryption key (or wrapping key if `--wrapped-key` is provided) |
| `--plain-text` | **Yes** | string | -- | Plaintext to encrypt (hex-encoded, 2-4096 chars) |
| `--encryption-attributes` | **Yes** | tagged union | -- | Encryption type and parameters (one of below) |
| `--wrapped-key` | No | structure | None | WrappedKeyBlock containing the encryption key |

**Encryption Attributes (tagged union -- specify one):**

**Symmetric:**
```json
{
    "Symmetric": {
        "Mode": "ECB|CBC|CFB|CFB1|CFB8|CFB64|CFB128|OFB",
        "InitializationVector": "string",
        "PaddingType": "PKCS1|OAEP_SHA1|OAEP_SHA256|OAEP_SHA512"
    }
}
```

**Asymmetric:**
```json
{
    "Asymmetric": {
        "PaddingType": "PKCS1|OAEP_SHA1|OAEP_SHA256|OAEP_SHA512"
    }
}
```

**Dukpt:**
```json
{
    "Dukpt": {
        "KeySerialNumber": "string",
        "Mode": "ECB|CBC",
        "DukptKeyDerivationType": "TDES_2KEY|TDES_3KEY|AES_128|AES_192|AES_256",
        "DukptKeyVariant": "BIDIRECTIONAL|REQUEST|RESPONSE",
        "InitializationVector": "string"
    }
}
```

**Emv:**
```json
{
    "Emv": {
        "MajorKeyDerivationMode": "EMV_OPTION_A|EMV_OPTION_B",
        "PrimaryAccountNumber": "string",
        "PanSequenceNumber": "string",
        "SessionDerivationData": "string",
        "Mode": "ECB|CBC",
        "InitializationVector": "string"
    }
}
```

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string",
    "CipherText": "string"
}
```

---

### 5.2 `decrypt-data`

Decrypts ciphertext data using a symmetric or asymmetric key, DUKPT, or EMV session key.

**Synopsis:**
```bash
aws payment-cryptography-data decrypt-data \
    --key-identifier <value> \
    --cipher-text <value> \
    --decryption-attributes <value> \
    [--wrapped-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN of the decryption key |
| `--cipher-text` | **Yes** | string | -- | Ciphertext to decrypt (hex-encoded, 2-4224 chars) |
| `--decryption-attributes` | **Yes** | tagged union | -- | Decryption type and parameters (Symmetric, Asymmetric, Dukpt, or Emv) |
| `--wrapped-key` | No | structure | None | WrappedKeyBlock containing the decryption key |

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string",
    "PlainText": "string"
}
```

---

### 5.3 `re-encrypt-data`

Re-encrypts ciphertext from one key to another without exposing the plaintext.

**Synopsis:**
```bash
aws payment-cryptography-data re-encrypt-data \
    --incoming-key-identifier <value> \
    --outgoing-key-identifier <value> \
    --cipher-text <value> \
    --incoming-encryption-attributes <value> \
    --outgoing-encryption-attributes <value> \
    [--incoming-wrapped-key <value>] \
    [--outgoing-wrapped-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incoming-key-identifier` | **Yes** | string | -- | KeyARN of the incoming encryption key |
| `--outgoing-key-identifier` | **Yes** | string | -- | KeyARN of the outgoing encryption key |
| `--cipher-text` | **Yes** | string | -- | Ciphertext to re-encrypt (hex-encoded, 2-4224 chars) |
| `--incoming-encryption-attributes` | **Yes** | tagged union | -- | Incoming encryption params (Symmetric or Dukpt) |
| `--outgoing-encryption-attributes` | **Yes** | tagged union | -- | Outgoing encryption params (Symmetric or Dukpt) |
| `--incoming-wrapped-key` | No | structure | None | Wrapped key for incoming decryption |
| `--outgoing-wrapped-key` | No | structure | None | Wrapped key for outgoing encryption |

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string",
    "CipherText": "string"
}
```
