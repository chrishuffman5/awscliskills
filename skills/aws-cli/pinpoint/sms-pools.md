# SMS v2 Pools

All commands in this section use `aws pinpoint-sms-voice-v2`.

### 13.1 `create-pool`

Creates a new pool and associates an origination identity to the pool.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-pool \
    --origination-identity <value> \
    --iso-country-code <value> \
    --message-type <value> \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origination-identity` | **Yes** | string | -- | Phone number or sender ID to associate (ID or ARN) |
| `--iso-country-code` | **Yes** | string | -- | Two-character ISO 3166-1 alpha-2 country code |
| `--message-type` | **Yes** | string | -- | `TRANSACTIONAL` or `PROMOTIONAL` (cannot change after creation) |
| `--deletion-protection-enabled` | No | boolean | false | Prevent pool from being deleted |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "PoolArn": "string",
    "PoolId": "string",
    "Status": "CREATING|ACTIVE|DELETING",
    "MessageType": "TRANSACTIONAL|PROMOTIONAL",
    "TwoWayEnabled": "boolean",
    "TwoWayChannelArn": "string",
    "TwoWayChannelRole": "string",
    "SelfManagedOptOutsEnabled": "boolean",
    "OptOutListName": "string",
    "SharedRoutesEnabled": "boolean",
    "DeletionProtectionEnabled": "boolean",
    "Tags": [{"Key": "string", "Value": "string"}],
    "CreatedTimestamp": "timestamp"
}
```

---

### 13.2 `describe-pools`

Describes existing pools.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-pools \
    [--pool-ids <value>] \
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
| `--pool-ids` | No | list | None | Pool IDs or ARNs (max 5) |
| `--filters` | No | list | None | Filters: `status`, `message-type`, `two-way-enabled`, `self-managed-opt-outs-enabled`, `opt-out-list-name`, `shared-routes-enabled`, `deletion-protection-enabled`, `two-way-channel-arn` |
| `--owner` | No | string | None | `SELF` or `SHARED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Pools": [
        {
            "PoolArn": "string",
            "PoolId": "string",
            "Status": "CREATING|ACTIVE|DELETING",
            "MessageType": "TRANSACTIONAL|PROMOTIONAL",
            "TwoWayEnabled": "boolean",
            "TwoWayChannelArn": "string",
            "TwoWayChannelRole": "string",
            "SelfManagedOptOutsEnabled": "boolean",
            "OptOutListName": "string",
            "SharedRoutesEnabled": "boolean",
            "DeletionProtectionEnabled": "boolean",
            "CreatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 13.3 `update-pool`

Updates pool properties.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 update-pool \
    --pool-id <value> \
    [--two-way-enabled | --no-two-way-enabled] \
    [--two-way-channel-arn <value>] \
    [--two-way-channel-role <value>] \
    [--self-managed-opt-outs-enabled | --no-self-managed-opt-outs-enabled] \
    [--opt-out-list-name <value>] \
    [--shared-routes-enabled | --no-shared-routes-enabled] \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | Pool ID or ARN |
| `--two-way-enabled` | No | boolean | -- | Enable/disable two-way messaging |
| `--two-way-channel-arn` | No | string | -- | ARN of two-way channel |
| `--two-way-channel-role` | No | string | -- | IAM role ARN for inbound messages |
| `--self-managed-opt-outs-enabled` | No | boolean | -- | Enable/disable self-managed opt-outs |
| `--opt-out-list-name` | No | string | -- | Opt-out list name or ARN |
| `--shared-routes-enabled` | No | boolean | -- | Enable/disable shared routes |
| `--deletion-protection-enabled` | No | boolean | -- | Enable/disable deletion protection |

**Output Schema:** Same as `create-pool` (without `Tags`).

---

### 13.4 `delete-pool`

Deletes a pool. Pool must be active and deletion protection must be disabled.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-pool \
    --pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | Pool ID or ARN |

**Output Schema:** Same as `create-pool` (without `Tags`).

---

### 13.5 `list-pool-origination-identities`

Lists origination identities associated with a pool.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 list-pool-origination-identities \
    --pool-id <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | Pool ID or ARN |
| `--filters` | No | list | None | Filters: `iso-country-code`, `number-capability` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PoolArn": "string",
    "PoolId": "string",
    "OriginationIdentities": [
        {
            "OriginationIdentityArn": "string",
            "OriginationIdentity": "string",
            "IsoCountryCode": "string",
            "NumberCapabilities": ["SMS|VOICE|MMS"],
            "PhoneNumber": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 13.6 `associate-origination-identity`

Associates an origination identity (phone number or sender ID) with a pool.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 associate-origination-identity \
    --pool-id <value> \
    --origination-identity <value> \
    --iso-country-code <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | Pool ID or ARN |
| `--origination-identity` | **Yes** | string | -- | Phone number or sender ID (ID or ARN) |
| `--iso-country-code` | **Yes** | string | -- | Two-character ISO 3166-1 alpha-2 country code |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "PoolArn": "string",
    "PoolId": "string",
    "OriginationIdentityArn": "string",
    "OriginationIdentity": "string",
    "IsoCountryCode": "string"
}
```

---

### 13.7 `disassociate-origination-identity`

Removes an origination identity from a pool.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 disassociate-origination-identity \
    --pool-id <value> \
    --origination-identity <value> \
    --iso-country-code <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | Pool ID or ARN |
| `--origination-identity` | **Yes** | string | -- | Phone number or sender ID (ID or ARN) |
| `--iso-country-code` | **Yes** | string | -- | Two-character ISO 3166-1 alpha-2 country code |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "PoolArn": "string",
    "PoolId": "string",
    "OriginationIdentityArn": "string",
    "OriginationIdentity": "string",
    "IsoCountryCode": "string"
}
```
