# Voice Global Settings & Validation

CLI namespace: `aws chime-sdk-voice`

### 17.1 `get-global-settings` / `update-global-settings`

Manages global settings for Voice Connectors, including the S3 bucket for call detail records (CDR).

**Synopsis:**
```bash
aws chime-sdk-voice get-global-settings

aws chime-sdk-voice update-global-settings \
    [--voice-connector <value>]
```

**VoiceConnector settings structure:**
```json
{
    "CdrBucket": "my-cdr-bucket"
}
```

**Output Schema (get):**
```json
{
    "VoiceConnector": {
        "CdrBucket": "string"
    }
}
```

---

### 17.2 `validate-e911-address`

Validates an E911 emergency address for use with emergency calling configuration.

**Synopsis:**
```bash
aws chime-sdk-voice validate-e911-address \
    --aws-account-id <value> \
    --street-number <value> \
    --street-info <value> \
    --city <value> \
    --state <value> \
    --country <value> \
    --postal-code <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--street-number` | **Yes** | string | -- | Street number (e.g., `200`) |
| `--street-info` | **Yes** | string | -- | Street info (e.g., `8th Avenue`) |
| `--city` | **Yes** | string | -- | City (e.g., `Portland`) |
| `--state` | **Yes** | string | -- | State (e.g., `ME`) |
| `--country` | **Yes** | string | -- | ISO 3166-1 alpha-2 code (e.g., `US`) |
| `--postal-code` | **Yes** | string | -- | Postal code (e.g., `04352`) |

**Output Schema:**
```json
{
    "ValidationResult": 0,
    "AddressExternalId": "string",
    "Address": {
        "streetName": "string",
        "streetSuffix": "string",
        "postDirectional": "string",
        "preDirectional": "string",
        "streetNumber": "string",
        "city": "string",
        "state": "string",
        "postalCode": "string",
        "postalCodePlus4": "string",
        "country": "string"
    },
    "CandidateAddressList": [
        {
            "streetInfo": "string",
            "streetNumber": "string",
            "city": "string",
            "state": "string",
            "postalCode": "string",
            "postalCodePlus4": "string",
            "country": "string"
        }
    ]
}
```

**ValidationResult values:**
- `0` — Address validation succeeded
- `1` — Address validation succeeded with correction (close match)
- `2` — Address validation failed (review `CandidateAddressList` for alternatives)
