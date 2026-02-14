# Phone Numbers

### 14.1 `claim-phone-number`

Claims an available phone number for an instance.

**Synopsis:**
```bash
aws connect claim-phone-number \
    --phone-number <value> \
    [--target-arn <value>] \
    [--instance-id <value>] \
    [--phone-number-description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number` | **Yes** | string | -- | Phone number in E.164 format |
| `--target-arn` | No | string | None | Instance or TDG ARN |
| `--instance-id` | No | string | None | Instance ID (alternative to target-arn) |
| `--phone-number-description` | No | string | None | Description (0-500 chars) |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | None | Idempotency token (UUID) |

**Output Schema:**
```json
{
    "PhoneNumberId": "string",
    "PhoneNumberArn": "string"
}
```

---

### 14.2 `describe-phone-number`

Describes a phone number.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or ARN |

**Output Schema:**
```json
{
    "ClaimedPhoneNumberSummary": {
        "PhoneNumberId": "string",
        "PhoneNumberArn": "string",
        "PhoneNumber": "string",
        "PhoneNumberCountryCode": "string",
        "PhoneNumberType": "TOLL_FREE|DID|UIFN|SHARED|THIRD_PARTY_TF|THIRD_PARTY_DID|SHORT_CODE",
        "PhoneNumberDescription": "string",
        "TargetArn": "string",
        "InstanceId": "string",
        "Tags": { "key": "value" },
        "PhoneNumberStatus": { "Status": "CLAIMED|IN_PROGRESS|FAILED", "Message": "string" },
        "SourcePhoneNumberArn": "string"
    }
}
```

---

### 14.3 `list-phone-numbers`

Lists phone numbers for an instance. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--phone-number-types` | No | list | None | Filter by types |
| `--phone-number-country-codes` | No | list | None | Filter by country codes |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

---

### 14.4 `list-phone-numbers-v2`

Lists phone numbers (v2 with enhanced filters). **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | No | string | None | Instance or TDG ARN |
| `--instance-id` | No | string | None | Instance ID |
| `--phone-number-country-codes` | No | list | None | Filter by country codes |
| `--phone-number-types` | No | list | None | Filter by types |
| `--phone-number-prefix` | No | string | None | Filter by prefix |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "ListPhoneNumbersSummaryList": [ { "PhoneNumberId": "string", "PhoneNumberArn": "string", "PhoneNumber": "string", "PhoneNumberCountryCode": "string", "PhoneNumberType": "string", "TargetArn": "string", "InstanceId": "string", "PhoneNumberDescription": "string", "SourcePhoneNumberArn": "string" } ],
    "NextToken": "string"
}
```

---

### 14.5 `update-phone-number`

Updates the target for a phone number.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or ARN |
| `--target-arn` | No | string | None | New instance or TDG ARN |
| `--instance-id` | No | string | None | New instance ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "PhoneNumberId": "string",
    "PhoneNumberArn": "string"
}
```

---

### 14.6 `update-phone-number-metadata`

Updates phone number metadata (description, flow association).

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or ARN |
| `--phone-number-description` | No | string | None | Updated description |
| `--contact-flow-id` | No | string | None | Associated flow ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 14.7 `release-phone-number`

Releases a phone number.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or ARN |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 14.8 `import-phone-number`

Imports a phone number from an external source.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--source-phone-number-arn` | **Yes** | string | -- | Source phone number ARN |
| `--phone-number-description` | No | string | None | Description |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "PhoneNumberId": "string",
    "PhoneNumberArn": "string"
}
```

---

### 14.9 `search-available-phone-numbers`

Searches available phone numbers to claim. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | No | string | None | Instance or TDG ARN |
| `--instance-id` | No | string | None | Instance ID |
| `--phone-number-country-code` | **Yes** | string | -- | Country code (e.g., `US`) |
| `--phone-number-type` | **Yes** | string | -- | `TOLL_FREE` or `DID` |
| `--phone-number-prefix` | No | string | None | Number prefix filter |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-10) |

**Output Schema:**
```json
{
    "AvailableNumbersList": [ { "PhoneNumber": "string", "PhoneNumberCountryCode": "string", "PhoneNumberType": "string" } ],
    "NextToken": "string"
}
```

---

### 14.10 `associate-phone-number-contact-flow`

Associates a phone number with a contact flow.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or ARN |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |

**Output:** None

---

### 14.11 `disassociate-phone-number-contact-flow`

Removes a phone number from a contact flow.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or ARN |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output:** None
