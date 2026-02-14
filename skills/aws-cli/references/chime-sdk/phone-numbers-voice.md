# Phone Numbers (Voice)

Commands from the `aws chime-sdk-voice` service.

### 13.1 `create-phone-number-order`

Orders phone numbers.

**Synopsis:**
```bash
aws chime-sdk-voice create-phone-number-order \
    --product-type <value> \
    --e164-phone-numbers <value> \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-type` | **Yes** | string | -- | `VoiceConnector` or `SipMediaApplicationDialIn` |
| `--e164-phone-numbers` | **Yes** | list | -- | E.164 phone numbers to order |
| `--name` | No | string | None | Order name |

**Output Schema:**
```json
{
    "PhoneNumberOrder": {
        "PhoneNumberOrderId": "string",
        "PhoneNumberOrderType": "New|Porting",
        "Status": "Processing|Successful|Partial|Failed|Action Required|FOC|Change Requested|Exception|Submitted",
        "OrderType": "string",
        "OrderedPhoneNumbers": [
            { "E164PhoneNumber": "string", "Status": "Processing|Acquired|Failed" }
        ],
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp"
    }
}
```

---

### 13.2 `get-phone-number`

Gets phone number details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or E.164 |

**Output Schema:**
```json
{
    "PhoneNumber": {
        "PhoneNumberId": "string",
        "E164PhoneNumber": "string",
        "Country": "string",
        "Type": "Local|TollFree",
        "ProductType": "VoiceConnector|SipMediaApplicationDialIn",
        "Status": "Cancelled|PortinCancelRequested|PortinInProgress|AcquireInProgress|AcquireFailed|Unassigned|Assigned|ReleaseInProgress|DeleteInProgress|ReleaseFailed|DeleteFailed",
        "Capabilities": {
            "InboundCall": "boolean",
            "OutboundCall": "boolean",
            "InboundSMS": "boolean",
            "OutboundSMS": "boolean",
            "InboundMMS": "boolean",
            "OutboundMMS": "boolean"
        },
        "Associations": [
            { "Value": "string", "Name": "VoiceConnectorId|VoiceConnectorGroupId|SipRuleId", "AssociatedTimestamp": "timestamp" }
        ],
        "CallingName": "string",
        "CallingNameStatus": "Unassigned|UpdateInProgress|UpdateSucceeded|UpdateFailed",
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "DeletionTimestamp": "timestamp",
        "OrderId": "string",
        "Name": "string"
    }
}
```

---

### 13.3 `get-phone-number-order`

Gets phone number order details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-order-id` | **Yes** | string | -- | Order ID (UUID) |

---

### 13.4 `list-phone-numbers`

Lists phone numbers. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | Filter by status |
| `--product-type` | No | string | None | Filter by product type |
| `--filter-name` | No | string | None | `VoiceConnectorId`, `VoiceConnectorGroupId`, `SipRuleId` |
| `--filter-value` | No | string | None | Filter value |
| `--max-results` | No | integer | None | Max results (1-99) |
| `--next-token` | No | string | None | Pagination token |

---

### 13.5 `list-phone-number-orders`

Lists phone number orders. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-99) |

---

### 13.6 `update-phone-number`

Updates a phone number.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID |
| `--product-type` | No | string | None | Updated product type |
| `--calling-name` | No | string | None | Calling name |
| `--name` | No | string | None | Phone number name |

---

### 13.7 `delete-phone-number`

Moves a phone number to the deletion queue.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID |

**Output:** None

---

### 13.8 `batch-delete-phone-number`

Batch deletes phone numbers.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-ids` | **Yes** | list | -- | Phone number IDs (min 1) |

**Output Schema:**
```json
{
    "PhoneNumberErrors": [
        { "PhoneNumberId": "string", "ErrorCode": "string", "ErrorMessage": "string" }
    ]
}
```

---

### 13.9 `batch-update-phone-number`

Batch updates phone numbers.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--update-phone-number-request-items` | **Yes** | list | -- | Update items |

---

### 13.10 `restore-phone-number`

Restores a deleted phone number.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID |

---

### 13.11 `get-phone-number-settings`

Gets the calling name for outbound calls.

**Parameters:** None required.

**Output Schema:**
```json
{
    "CallingName": "string",
    "CallingNameUpdatedTimestamp": "timestamp"
}
```

---

### 13.12 `update-phone-number-settings`

Updates the default calling name for outbound calls.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--calling-name` | **Yes** | string | -- | Default calling name |

**Output:** None

---

### 13.13 `search-available-phone-numbers`

Searches available phone numbers.

**Synopsis:**
```bash
aws chime-sdk-voice search-available-phone-numbers \
    [--area-code <value>] \
    [--city <value>] \
    [--country <value>] \
    [--state <value>] \
    [--toll-free-prefix <value>] \
    [--phone-number-type <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--area-code` | No | string | None | Area code filter |
| `--city` | No | string | None | City filter |
| `--country` | No | string | None | Country code (ISO 3166-1 alpha-2) |
| `--state` | No | string | None | State/province filter |
| `--toll-free-prefix` | No | string | None | Toll-free prefix (e.g., 800, 888) |
| `--phone-number-type` | No | string | None | `Local` or `TollFree` |
| `--max-results` | No | integer | None | Max results (1-500) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "E164PhoneNumbers": ["string"],
    "NextToken": "string"
}
```

---

### 13.14 `list-supported-phone-number-countries`

Lists countries that support the specified phone number type.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-type` | **Yes** | string | -- | `VoiceConnector` or `SipMediaApplicationDialIn` |

---

### 13.15 `associate-phone-numbers-with-voice-connector`

Associates phone numbers with a voice connector.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--e164-phone-numbers` | **Yes** | list | -- | E.164 phone numbers |
| `--force-associate` | No | boolean | None | Force association |

---

### 13.16 `disassociate-phone-numbers-from-voice-connector`

Removes phone number associations from a voice connector.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--e164-phone-numbers` | **Yes** | list | -- | E.164 phone numbers |

---

### 13.17 `associate-phone-numbers-with-voice-connector-group`

Associates phone numbers with a voice connector group.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-group-id` | **Yes** | string | -- | Group ID |
| `--e164-phone-numbers` | **Yes** | list | -- | E.164 phone numbers |
| `--force-associate` | No | boolean | None | Force association |

---

### 13.18 `disassociate-phone-numbers-from-voice-connector-group`

Removes phone number associations from a voice connector group.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-group-id` | **Yes** | string | -- | Group ID |
| `--e164-phone-numbers` | **Yes** | list | -- | E.164 phone numbers |

---

### 13.19 `list-available-voice-connector-regions`

Lists available regions for voice connectors.

**Parameters:** None required.

**Output Schema:**
```json
{
    "VoiceConnectorRegions": ["string"]
}
```

---

### 13.20 `get-global-settings`

Gets global settings (voice connector CDR S3 bucket).

**Parameters:** None required.

**Output Schema:**
```json
{
    "VoiceConnector": {
        "CdrBucket": "string"
    }
}
```

---

### 13.21 `update-global-settings`

Updates global settings.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector` | No | structure | None | Voice connector settings |

---

### 13.22 `validate-e911-address`

Validates an E911 address.

**Synopsis:**
```bash
aws chime-sdk-voice validate-e911-address \
    --aws-account-id <value> \
    --street-number <value> \
    --street-info <value> \
    --city <value> \
    --state <value> \
    --country <value> \
    --postal-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--street-number` | **Yes** | string | -- | Street number |
| `--street-info` | **Yes** | string | -- | Street info |
| `--city` | **Yes** | string | -- | City |
| `--state` | **Yes** | string | -- | State |
| `--country` | **Yes** | string | -- | Country (ISO 3166-1 alpha-2) |
| `--postal-code` | **Yes** | string | -- | Postal code |

**Output Schema:**
```json
{
    "ValidationResult": "integer (0=valid, 1=not validated, 2=multiple matches)",
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
    "CandidateAddressList": [{ "..." }]
}
```
