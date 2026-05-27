# MAC Operations

### 7.1 `generate-mac`

Generates a Message Authentication Code (MAC) using various algorithms.

**Synopsis:**
```bash
aws payment-cryptography-data generate-mac \
    --key-identifier <value> \
    --message-data <value> \
    --generation-attributes <value> \
    [--mac-length <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN of the MAC generation key |
| `--message-data` | **Yes** | string | -- | Data for MAC generation (hex-encoded, 2-8192 chars) |
| `--generation-attributes` | **Yes** | tagged union | -- | MAC algorithm and parameters (see below) |
| `--mac-length` | No | integer | None | MAC length (4-16) |

**Generation Attributes (tagged union -- specify one):**

**Algorithm (string):** `ISO9797_ALGORITHM1`, `ISO9797_ALGORITHM3`, `CMAC`, `HMAC`, `HMAC_SHA224`, `HMAC_SHA256`, `HMAC_SHA384`, `HMAC_SHA512`, `AS2805_4_1`

**EmvMac:**
```json
{
    "EmvMac": {
        "MajorKeyDerivationMode": "EMV_OPTION_A|EMV_OPTION_B",
        "PrimaryAccountNumber": "string",
        "PanSequenceNumber": "string",
        "SessionKeyDerivationMode": "EMV_COMMON_SESSION_KEY|EMV2000|AMEX|MASTERCARD_SESSION_KEY|VISA",
        "SessionKeyDerivationValue": {
            "ApplicationCryptogram": "string",
            "ApplicationTransactionCounter": "string"
        }
    }
}
```

**DukptIso9797Algorithm1 / DukptIso9797Algorithm3 / DukptCmac:**
```json
{
    "DukptIso9797Algorithm1": {
        "KeySerialNumber": "string",
        "DukptKeyVariant": "BIDIRECTIONAL|REQUEST|RESPONSE",
        "DukptDerivationType": "TDES_2KEY|TDES_3KEY|AES_128|AES_192|AES_256"
    }
}
```

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string",
    "Mac": "string"
}
```

---

### 7.2 `verify-mac`

Verifies a Message Authentication Code (MAC).

**Synopsis:**
```bash
aws payment-cryptography-data verify-mac \
    --key-identifier <value> \
    --message-data <value> \
    --mac <value> \
    --verification-attributes <value> \
    [--mac-length <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN of the MAC verification key |
| `--message-data` | **Yes** | string | -- | Data for MAC verification (hex-encoded, 2-8192 chars) |
| `--mac` | **Yes** | string | -- | MAC to verify (hex-encoded, 4-128 chars) |
| `--verification-attributes` | **Yes** | tagged union | -- | MAC algorithm and parameters (same structure as generate-mac) |
| `--mac-length` | No | integer | None | MAC length (4-16) |

**Output Schema:**
```json
{
    "KeyArn": "string",
    "KeyCheckValue": "string"
}
```
