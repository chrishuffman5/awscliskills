# Card Validation

### 8.1 `generate-card-validation-data`

Generates card validation data (CVV, CVV2, CSC) for a payment card.

**Synopsis:**
```bash
aws payment-cryptography-data generate-card-validation-data \
    --key-identifier <value> \
    --primary-account-number <value> \
    --generation-attributes <value> \
    [--validation-data-length <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN of the CVK encryption key |
| `--primary-account-number` | **Yes** | string | -- | PAN (12-19 digits) |
| `--generation-attributes` | **Yes** | tagged union | -- | Card validation algorithm (see below) |
| `--validation-data-length` | No | integer | 3 | CVV/CSC length (3-5) |

**Generation Attributes (tagged union -- specify one):**

**AmexCardSecurityCodeVersion1:** `{ "CardExpiryDate": "string" }`

**AmexCardSecurityCodeVersion2:** `{ "CardExpiryDate": "string", "ServiceCode": "string" }`

**CardVerificationValue1:** `{ "CardExpiryDate": "string", "ServiceCode": "string" }`

**CardVerificationValue2:** `{ "CardExpiryDate": "string" }`

**CardHolderVerificationValue:** `{ "UnpredictableNumber": "string", "PanSequenceNumber": "string", "ApplicationTransactionCounter": "string" }`

**DynamicCardVerificationCode:** `{ "UnpredictableNumber": "string", "PanSequenceNumber": "string", "ApplicationTransactionCounter": "string", "TrackData": "string" }`

**DynamicCardVerificationValue:** `{ "PanSequenceNumber": "string", "CardExpiryDate": "string", "ServiceCode": "string", "ApplicationTransactionCounter": "string" }`

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string",
    "ValidationData": "string"
}
```

---

### 8.2 `verify-card-validation-data`

Verifies card validation data (CVV, CVV2, CSC) for a payment card.

**Synopsis:**
```bash
aws payment-cryptography-data verify-card-validation-data \
    --key-identifier <value> \
    --primary-account-number <value> \
    --verification-attributes <value> \
    --validation-data <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN of the CVK encryption key |
| `--primary-account-number` | **Yes** | string | -- | PAN (12-19 digits) |
| `--verification-attributes` | **Yes** | tagged union | -- | Card validation algorithm (same options as generate + DiscoverDynamicCardVerificationCode) |
| `--validation-data` | **Yes** | string | -- | CVV/CSC value to verify (3-5 digits) |

**Additional Verification Attribute:**

**DiscoverDynamicCardVerificationCode:** `{ "CardExpiryDate": "string", "UnpredictableNumber": "string", "ApplicationTransactionCounter": "string" }`

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string"
}
```

---

### 8.3 `verify-auth-request-cryptogram`

Verifies an Authorization Request Cryptogram (ARQC) and optionally generates an Authorization Response Cryptogram (ARPC).

**Synopsis:**
```bash
aws payment-cryptography-data verify-auth-request-cryptogram \
    --key-identifier <value> \
    --transaction-data <value> \
    --auth-request-cryptogram <value> \
    --major-key-derivation-mode <value> \
    --session-key-derivation-attributes <value> \
    [--auth-response-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN of the major encryption key |
| `--transaction-data` | **Yes** | string | -- | Transaction data (hex-encoded, 2-1024 chars) |
| `--auth-request-cryptogram` | **Yes** | string | -- | ARQC to verify (16 hex chars) |
| `--major-key-derivation-mode` | **Yes** | string | -- | `EMV_OPTION_A` or `EMV_OPTION_B` |
| `--session-key-derivation-attributes` | **Yes** | tagged union | -- | Session key params (see below) |
| `--auth-response-attributes` | No | tagged union | None | ARPC generation params |

**Session Key Derivation Attributes (tagged union):**

**EmvCommon / Emv2000:** `{ "PrimaryAccountNumber": "string", "PanSequenceNumber": "string", "ApplicationTransactionCounter": "string" }`

**Mastercard:** `{ "PrimaryAccountNumber": "string", "PanSequenceNumber": "string", "ApplicationTransactionCounter": "string", "UnpredictableNumber": "string" }`

**Amex / Visa:** `{ "PrimaryAccountNumber": "string", "PanSequenceNumber": "string" }`

**Auth Response Attributes:**

**ArpcMethod1:** `{ "AuthResponseCode": "string" }` (4 hex chars)

**ArpcMethod2:** `{ "CardStatusUpdate": "string", "ProprietaryAuthenticationData": "string" }`

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string",
    "AuthResponseValue": "string"
}
```

---

### 8.4 `generate-as2805-kek-validation`

Generates random key data for AS2805 KEK node-to-node initialization validation.

**Synopsis:**
```bash
aws payment-cryptography-data generate-as2805-kek-validation \
    --key-identifier <value> \
    --kek-validation-type <value> \
    --random-key-send-variant-mask <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN of the sending KEK |
| `--kek-validation-type` | **Yes** | tagged union | -- | Validation type (KekValidationRequest or KekValidationResponse) |
| `--random-key-send-variant-mask` | **Yes** | string | -- | Key variant: `VARIANT_MASK_82C0` or `VARIANT_MASK_82` |

**KEK Validation Type:**

**KekValidationRequest:** `{ "DeriveKeyAlgorithm": "TDES_2KEY|TDES_3KEY|AES_128|..." }`

**KekValidationResponse:** `{ "RandomKeySend": "string" }`

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string",
    "RandomKeySend": "string",
    "RandomKeyReceive": "string"
}
```

---

### 8.5 `translate-key-material`

Translates key material from an ECDH-derived wrapping to a TR-31 wrapping.

**Synopsis:**
```bash
aws payment-cryptography-data translate-key-material \
    --incoming-key-material <value> \
    --outgoing-key-material <value> \
    [--key-check-value-algorithm <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incoming-key-material` | **Yes** | tagged union | -- | DiffieHellmanTr31KeyBlock with ECDH-derived wrapping parameters |
| `--outgoing-key-material` | **Yes** | tagged union | -- | Tr31KeyBlock with target wrapping key identifier |
| `--key-check-value-algorithm` | No | string | None | KCV algorithm: `CMAC`, `ANSI_X9_24`, `HMAC`, `SHA_1` |

**Incoming Key Material (DiffieHellmanTr31KeyBlock):**
```json
{
    "DiffieHellmanTr31KeyBlock": {
        "PrivateKeyIdentifier": "string",
        "CertificateAuthorityPublicKeyIdentifier": "string",
        "PublicKeyCertificate": "string",
        "DeriveKeyAlgorithm": "string",
        "KeyDerivationFunction": "NIST_SP800|ANSI_X963",
        "KeyDerivationHashAlgorithm": "SHA_256|SHA_384|SHA_512",
        "DerivationData": { "SharedInformation": "string" },
        "WrappedKeyBlock": "string"
    }
}
```

**Outgoing Key Material (Tr31KeyBlock):**
```json
{
    "Tr31KeyBlock": {
        "WrappingKeyIdentifier": "string"
    }
}
```

**Output Schema:**
```json
{
    "WrappedKey": {
        "WrappedKeyMaterial": "string",
        "KeyCheckValue": "string",
        "WrappedKeyMaterialFormat": "KEY_CRYPTOGRAM|TR31_KEY_BLOCK|TR34_KEY_BLOCK"
    }
}
```
