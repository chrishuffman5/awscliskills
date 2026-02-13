# PIN Operations

### 6.1 `generate-pin-data`

Generates PIN-related data such as PIN, PVV (PIN Verification Value), or PIN Offset.

**Synopsis:**
```bash
aws payment-cryptography-data generate-pin-data \
    --generation-key-identifier <value> \
    --encryption-key-identifier <value> \
    --generation-attributes <value> \
    --pin-block-format <value> \
    [--pin-data-length <value>] \
    [--primary-account-number <value>] \
    [--encryption-wrapped-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--generation-key-identifier` | **Yes** | string | -- | KeyARN of the PEK for PIN generation |
| `--encryption-key-identifier` | **Yes** | string | -- | KeyARN of the PEK to encrypt the PIN block |
| `--generation-attributes` | **Yes** | tagged union | -- | PIN generation method (see below) |
| `--pin-block-format` | **Yes** | string | -- | PIN encoding format: `ISO_FORMAT_0`, `ISO_FORMAT_1`, `ISO_FORMAT_3`, `ISO_FORMAT_4` |
| `--pin-data-length` | No | integer | None | PIN length (4-12) |
| `--primary-account-number` | No | string | None | PAN (12-19 digits) |
| `--encryption-wrapped-key` | No | structure | None | Wrapped key for encryption |

**Generation Attributes (tagged union -- specify one):**

**VisaPin:** `{ "PinVerificationKeyIndex": integer }`

**VisaPinVerificationValue:** `{ "EncryptedPinBlock": "string", "PinVerificationKeyIndex": integer }`

**Ibm3624NaturalPin:** `{ "DecimalizationTable": "string", "PinValidationDataPadCharacter": "string", "PinValidationData": "string" }`

**Ibm3624RandomPin:** `{ "DecimalizationTable": "string", "PinValidationDataPadCharacter": "string", "PinValidationData": "string" }`

**Ibm3624PinOffset:** `{ "EncryptedPinBlock": "string", "DecimalizationTable": "string", "PinValidationDataPadCharacter": "string", "PinValidationData": "string" }`

**Ibm3624PinFromOffset:** `{ "DecimalizationTable": "string", "PinValidationDataPadCharacter": "string", "PinValidationData": "string", "PinOffset": "string" }`

**Output Schema:**
```json
{
    "GenerationKeyArn": "string",
    "GenerationKeyCheckValue": "string",
    "EncryptionKeyArn": "string",
    "EncryptionKeyCheckValue": "string",
    "EncryptedPinBlock": "string",
    "PinData": {
        "PinOffset": "string",
        "VerificationValue": "string"
    }
}
```

---

### 6.2 `verify-pin-data`

Verifies PIN data against stored verification values.

**Synopsis:**
```bash
aws payment-cryptography-data verify-pin-data \
    --verification-key-identifier <value> \
    --encryption-key-identifier <value> \
    --verification-attributes <value> \
    --encrypted-pin-block <value> \
    --pin-block-format <value> \
    [--primary-account-number <value>] \
    [--pin-data-length <value>] \
    [--dukpt-attributes <value>] \
    [--encryption-wrapped-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--verification-key-identifier` | **Yes** | string | -- | KeyARN of the PIN verification key |
| `--encryption-key-identifier` | **Yes** | string | -- | KeyARN of the encryption key (PEK or BDK) |
| `--verification-attributes` | **Yes** | tagged union | -- | Verification method (VisaPin or Ibm3624Pin) |
| `--encrypted-pin-block` | **Yes** | string | -- | Encrypted PIN block (16-32 hex chars) |
| `--pin-block-format` | **Yes** | string | -- | PIN format: `ISO_FORMAT_0`, `ISO_FORMAT_1`, `ISO_FORMAT_3`, `ISO_FORMAT_4` |
| `--primary-account-number` | No | string | None | PAN (12-19 digits) |
| `--pin-data-length` | No | integer | None | PIN length (4-12) |
| `--dukpt-attributes` | No | structure | None | DUKPT key derivation attributes |
| `--encryption-wrapped-key` | No | structure | None | Wrapped encryption key |

**Verification Attributes:**

**VisaPin:** `{ "PinVerificationKeyIndex": integer, "VerificationValue": "string" }`

**Ibm3624Pin:** `{ "DecimalizationTable": "string", "PinValidationDataPadCharacter": "string", "PinValidationData": "string", "PinOffset": "string" }`

**Output Schema:**
```json
{
    "VerificationKeyArn": "string",
    "VerificationKeyCheckValue": "string",
    "EncryptionKeyArn": "string",
    "EncryptionKeyCheckValue": "string"
}
```

---

### 6.3 `translate-pin-data`

Translates an encrypted PIN block from one format/key to another without exposing the PIN.

**Synopsis:**
```bash
aws payment-cryptography-data translate-pin-data \
    --incoming-key-identifier <value> \
    --outgoing-key-identifier <value> \
    --incoming-translation-attributes <value> \
    --outgoing-translation-attributes <value> \
    --encrypted-pin-block <value> \
    [--incoming-dukpt-attributes <value>] \
    [--outgoing-dukpt-attributes <value>] \
    [--incoming-wrapped-key <value>] \
    [--outgoing-wrapped-key <value>] \
    [--incoming-as2805-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incoming-key-identifier` | **Yes** | string | -- | KeyARN of incoming encryption key |
| `--outgoing-key-identifier` | **Yes** | string | -- | KeyARN of outgoing encryption key |
| `--incoming-translation-attributes` | **Yes** | tagged union | -- | Incoming PIN format (IsoFormat0/1/3/4, As2805Format0) |
| `--outgoing-translation-attributes` | **Yes** | tagged union | -- | Outgoing PIN format (IsoFormat0/1/3/4, As2805Format0) |
| `--encrypted-pin-block` | **Yes** | string | -- | Encrypted PIN block (16-32 hex chars) |
| `--incoming-dukpt-attributes` | No | structure | None | DUKPT attributes for incoming key |
| `--outgoing-dukpt-attributes` | No | structure | None | DUKPT attributes for outgoing key |
| `--incoming-wrapped-key` | No | structure | None | Wrapped key for incoming PIN |
| `--outgoing-wrapped-key` | No | structure | None | Wrapped key for outgoing PIN |
| `--incoming-as2805-attributes` | No | structure | None | AS2805 attributes |

**Translation Attributes:**
```json
{
    "IsoFormat0": { "PrimaryAccountNumber": "string" },
    "IsoFormat1": {},
    "IsoFormat3": { "PrimaryAccountNumber": "string" },
    "IsoFormat4": { "PrimaryAccountNumber": "string" },
    "As2805Format0": { "PrimaryAccountNumber": "string" }
}
```

**Output Schema:**
```json
{
    "PinBlock": "string",
    "KeyArn": "string",
    "KeyCheckValue": "string"
}
```

---

### 6.4 `generate-mac-emv-pin-change`

Generates a MAC for an EMV PIN change command using issuer script processing.

**Synopsis:**
```bash
aws payment-cryptography-data generate-mac-emv-pin-change \
    --new-pin-pek-identifier <value> \
    --new-encrypted-pin-block <value> \
    --pin-block-format <value> \
    --secure-messaging-integrity-key-identifier <value> \
    --secure-messaging-confidentiality-key-identifier <value> \
    --message-data <value> \
    --derivation-method-attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--new-pin-pek-identifier` | **Yes** | string | -- | KeyARN of PEK protecting new PIN block |
| `--new-encrypted-pin-block` | **Yes** | string | -- | New encrypted PIN block (16 hex chars) |
| `--pin-block-format` | **Yes** | string | -- | Format: `ISO_FORMAT_0`, `ISO_FORMAT_1`, `ISO_FORMAT_3` |
| `--secure-messaging-integrity-key-identifier` | **Yes** | string | -- | KeyARN of IMK-SMI |
| `--secure-messaging-confidentiality-key-identifier` | **Yes** | string | -- | KeyARN of IMK-SMC |
| `--message-data` | **Yes** | string | -- | APDU command data (16-1024 hex chars) |
| `--derivation-method-attributes` | **Yes** | tagged union | -- | Card-specific derivation (EmvCommon, Amex, Visa, Emv2000, Mastercard) |

**Output Schema:**
```json
{
    "NewPinPekArn": "string",
    "SecureMessagingIntegrityKeyArn": "string",
    "SecureMessagingConfidentialityKeyArn": "string",
    "Mac": "string",
    "EncryptedPinBlock": "string",
    "NewPinPekKeyCheckValue": "string",
    "SecureMessagingIntegrityKeyCheckValue": "string",
    "SecureMessagingConfidentialityKeyCheckValue": "string",
    "VisaAmexDerivationOutputs": {
        "AuthorizationRequestKeyArn": "string",
        "AuthorizationRequestKeyCheckValue": "string",
        "CurrentPinPekArn": "string",
        "CurrentPinPekKeyCheckValue": "string"
    }
}
```
