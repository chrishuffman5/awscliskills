# Phone Numbers

CLI namespace: `aws chime-sdk-voice`

### 13.1 `search-available-phone-numbers`

Searches for available phone numbers.

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
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--area-code` | No | string | None | Area code filter |
| `--city` | No | string | None | City filter |
| `--country` | No | string | None | Country code (e.g., `US`) |
| `--state` | No | string | None | State filter |
| `--toll-free-prefix` | No | string | None | Toll-free prefix (`800`, `833`, `844`, etc.) |
| `--phone-number-type` | No | string | None | `Local` or `TollFree` |
| `--max-results` | No | integer | None | Max results (1-500) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "E164PhoneNumbers": ["+12025551234"],
    "NextToken": "string"
}
```

---

### 13.2 `create-phone-number-order`

Creates an order for phone numbers to be provisioned.

**Synopsis:**
```bash
aws chime-sdk-voice create-phone-number-order \
    --product-type <value> \
    --e164-phone-numbers <value> \
    [--name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-type` | **Yes** | string | -- | `VoiceConnector` or `SipMediaApplicationDialIn` |
| `--e164-phone-numbers` | **Yes** | list | -- | Phone numbers in E.164 format |
| `--name` | No | string | None | Name for the order (0-256 chars) |

**Output Schema:**
```json
{
    "PhoneNumberOrder": {
        "PhoneNumberOrderId": "string",
        "ProductType": "VoiceConnector|SipMediaApplicationDialIn",
        "Status": "Processing|Successful|Failed|Partial|PendingDocuments|Submitted|FOC|ChangeRequested|Exception|CancelRequested|Cancelled",
        "OrderType": "New|Porting",
        "OrderedPhoneNumbers": [
            {
                "E164PhoneNumber": "string",
                "Status": "Processing|Acquired|Failed"
            }
        ],
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp"
    }
}
```

---

### 13.3 `get-phone-number-order` / `list-phone-number-orders` / `delete-phone-number-order`

```bash
aws chime-sdk-voice get-phone-number-order --phone-number-order-id <value>

aws chime-sdk-voice list-phone-number-orders [--next-token <value>] [--max-results <value>]

aws chime-sdk-voice delete-phone-number-order --phone-number-order-id <value>
```

---

### 13.4 `get-phone-number` / `list-phone-numbers`

```bash
aws chime-sdk-voice get-phone-number --phone-number-id <value>

aws chime-sdk-voice list-phone-numbers \
    [--status <value>] \
    [--product-type <value>] \
    [--filter-name <value>] \
    [--filter-value <value>] \
    [--max-results <value>] \
    [--next-token <value>]
```

**list-phone-numbers Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | Phone number status filter |
| `--product-type` | No | string | None | `VoiceConnector` or `SipMediaApplicationDialIn` |
| `--filter-name` | No | string | None | `VoiceConnectorId`, `VoiceConnectorGroupId`, or `SipRuleId` |
| `--filter-value` | No | string | None | Filter value |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema (get-phone-number):**
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
            {
                "Value": "string",
                "Name": "VoiceConnectorId|VoiceConnectorGroupId|SipRuleId",
                "AssociatedTimestamp": "timestamp"
            }
        ],
        "CallingName": "string",
        "CallingNameStatus": "Unassigned|UpdateInProgress|UpdateSucceeded|UpdateFailed",
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "Name": "string"
    }
}
```

---

### 13.5 `update-phone-number` / `delete-phone-number` / `restore-phone-number`

```bash
aws chime-sdk-voice update-phone-number \
    --phone-number-id <value> \
    [--product-type <value>] \
    [--calling-name <value>] \
    [--name <value>]

aws chime-sdk-voice delete-phone-number --phone-number-id <value>

aws chime-sdk-voice restore-phone-number --phone-number-id <value>
```

---

### 13.6 `batch-delete-phone-number` / `batch-update-phone-number`

```bash
aws chime-sdk-voice batch-delete-phone-number \
    --phone-number-ids id1 id2 id3

aws chime-sdk-voice batch-update-phone-number \
    --update-phone-number-request-items <value>
```

**UpdatePhoneNumberRequestItems structure:**
```json
[
    {
        "PhoneNumberId": "string",
        "ProductType": "VoiceConnector|SipMediaApplicationDialIn",
        "CallingName": "string",
        "Name": "string"
    }
]
```

**Output Schema (both):**
```json
{
    "PhoneNumberErrors": [
        {
            "PhoneNumberId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 13.7 `associate-phone-numbers-with-voice-connector` / `disassociate-phone-numbers-from-voice-connector`

```bash
aws chime-sdk-voice associate-phone-numbers-with-voice-connector \
    --voice-connector-id <value> \
    --e164-phone-numbers +12025551234 +12025555678 \
    [--force-associate | --no-force-associate]

aws chime-sdk-voice disassociate-phone-numbers-from-voice-connector \
    --voice-connector-id <value> \
    --e164-phone-numbers +12025551234 +12025555678
```

---

### 13.8 `associate-phone-numbers-with-voice-connector-group` / `disassociate-phone-numbers-from-voice-connector-group`

```bash
aws chime-sdk-voice associate-phone-numbers-with-voice-connector-group \
    --voice-connector-group-id <value> \
    --e164-phone-numbers +12025551234 +12025555678 \
    [--force-associate | --no-force-associate]

aws chime-sdk-voice disassociate-phone-numbers-from-voice-connector-group \
    --voice-connector-group-id <value> \
    --e164-phone-numbers +12025551234 +12025555678
```

---

### 13.9 `get-phone-number-settings` / `update-phone-number-settings`

Manages the default outbound calling name for the account.

```bash
aws chime-sdk-voice get-phone-number-settings

aws chime-sdk-voice update-phone-number-settings \
    --calling-name <value>
```

**Output Schema (get):**
```json
{
    "CallingName": "string",
    "CallingNameUpdatedTimestamp": "timestamp"
}
```
