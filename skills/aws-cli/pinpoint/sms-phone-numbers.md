# SMS v2 Phone Numbers

All commands in this section use `aws pinpoint-sms-voice-v2`.

### 14.1 `request-phone-number`

Requests a new phone number from the available inventory.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 request-phone-number \
    --iso-country-code <value> \
    --message-type <value> \
    --number-capabilities <value> \
    --number-type <value> \
    [--opt-out-list-name <value>] \
    [--pool-id <value>] \
    [--registration-id <value>] \
    [--international-sending-enabled | --no-international-sending-enabled] \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--iso-country-code` | **Yes** | string | -- | Two-character ISO 3166-1 alpha-2 country code |
| `--message-type` | **Yes** | string | -- | `TRANSACTIONAL` or `PROMOTIONAL` |
| `--number-capabilities` | **Yes** | list | -- | `SMS`, `VOICE`, `MMS` (1-3 values) |
| `--number-type` | **Yes** | string | -- | `LONG_CODE`, `TOLL_FREE`, `TEN_DLC`, or `SIMULATOR` |
| `--opt-out-list-name` | No | string | None | Opt-out list name or ARN |
| `--pool-id` | No | string | None | Pool ID or ARN to associate |
| `--registration-id` | No | string | None | Registration ID to associate |
| `--international-sending-enabled` | No | boolean | false | Enable international sending |
| `--deletion-protection-enabled` | No | boolean | false | Enable deletion protection |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "PhoneNumberArn": "string",
    "PhoneNumberId": "string",
    "PhoneNumber": "string",
    "Status": "PENDING|ACTIVE|ASSOCIATING|DISASSOCIATING|DELETED",
    "IsoCountryCode": "string",
    "MessageType": "TRANSACTIONAL|PROMOTIONAL",
    "NumberCapabilities": ["SMS|VOICE|MMS"],
    "NumberType": "LONG_CODE|TOLL_FREE|TEN_DLC|SIMULATOR",
    "MonthlyLeasingPrice": "string",
    "TwoWayEnabled": "boolean",
    "TwoWayChannelArn": "string",
    "TwoWayChannelRole": "string",
    "SelfManagedOptOutsEnabled": "boolean",
    "OptOutListName": "string",
    "InternationalSendingEnabled": "boolean",
    "DeletionProtectionEnabled": "boolean",
    "PoolId": "string",
    "RegistrationId": "string",
    "Tags": [{"Key": "string", "Value": "string"}],
    "CreatedTimestamp": "timestamp"
}
```

---

### 14.2 `describe-phone-numbers`

Describes phone numbers in your account.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-phone-numbers \
    [--phone-number-ids <value>] \
    [--filters <value>] \
    [--owner <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-ids` | No | list | None | Phone number IDs or ARNs (max 5) |
| `--filters` | No | list | None | Filters: `status`, `iso-country-code`, `message-type`, `number-capability`, `number-type`, `two-way-enabled`, `self-managed-opt-outs-enabled`, `opt-out-list-name`, `deletion-protection-enabled`, `two-way-channel-arn` |
| `--owner` | No | string | None | `SELF` or `SHARED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PhoneNumbers": [
        {
            "PhoneNumberArn": "string",
            "PhoneNumberId": "string",
            "PhoneNumber": "string",
            "Status": "PENDING|ACTIVE|ASSOCIATING|DISASSOCIATING|DELETED",
            "IsoCountryCode": "string",
            "MessageType": "TRANSACTIONAL|PROMOTIONAL",
            "NumberCapabilities": ["SMS|VOICE|MMS"],
            "NumberType": "SHORT_CODE|LONG_CODE|TOLL_FREE|TEN_DLC|SIMULATOR",
            "MonthlyLeasingPrice": "string",
            "TwoWayEnabled": "boolean",
            "TwoWayChannelArn": "string",
            "TwoWayChannelRole": "string",
            "SelfManagedOptOutsEnabled": "boolean",
            "OptOutListName": "string",
            "InternationalSendingEnabled": "boolean",
            "DeletionProtectionEnabled": "boolean",
            "PoolId": "string",
            "RegistrationId": "string",
            "CreatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 14.3 `update-phone-number`

Updates phone number settings.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 update-phone-number \
    --phone-number-id <value> \
    [--two-way-enabled | --no-two-way-enabled] \
    [--two-way-channel-arn <value>] \
    [--two-way-channel-role <value>] \
    [--self-managed-opt-outs-enabled | --no-self-managed-opt-outs-enabled] \
    [--opt-out-list-name <value>] \
    [--international-sending-enabled | --no-international-sending-enabled] \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or ARN |
| `--two-way-enabled` | No | boolean | -- | Enable/disable two-way messaging |
| `--two-way-channel-arn` | No | string | -- | ARN of two-way channel |
| `--two-way-channel-role` | No | string | -- | IAM role ARN for inbound messages |
| `--self-managed-opt-outs-enabled` | No | boolean | -- | Enable/disable self-managed opt-outs |
| `--opt-out-list-name` | No | string | -- | Opt-out list name or ARN |
| `--international-sending-enabled` | No | boolean | -- | Enable/disable international sending |
| `--deletion-protection-enabled` | No | boolean | -- | Enable/disable deletion protection |

**Output Schema:** Same as single `PhoneNumbers` entry from `describe-phone-numbers`.

---

### 14.4 `release-phone-number`

Releases a phone number from your account. Deletion protection must be disabled and phone number must not be associated with a pool.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 release-phone-number \
    --phone-number-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number-id` | **Yes** | string | -- | Phone number ID or ARN |

**Output Schema:** Same as single `PhoneNumbers` entry from `describe-phone-numbers`.
