# SMS v2 Opt-Out Lists & Keywords

All commands in this section use `aws pinpoint-sms-voice-v2`.

## Opt-Out Lists

### 17.1 `create-opt-out-list`

Creates a new opt-out list for phone numbers that should not receive messages.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-opt-out-list \
    --opt-out-list-name <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--opt-out-list-name` | **Yes** | string | -- | Opt-out list name (1-64 alphanumeric chars) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "OptOutListArn": "string",
    "OptOutListName": "string",
    "Tags": [{"Key": "string", "Value": "string"}],
    "CreatedTimestamp": "timestamp"
}
```

---

### 17.2 `describe-opt-out-lists`

Describes opt-out lists in your account.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-opt-out-lists \
    [--opt-out-list-names <value>] \
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
| `--opt-out-list-names` | No | list | None | Opt-out list names or ARNs (max 5) |
| `--owner` | No | string | None | `SELF` or `SHARED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OptOutLists": [
        {
            "OptOutListArn": "string",
            "OptOutListName": "string",
            "CreatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 17.3 `delete-opt-out-list`

Deletes an opt-out list and all opted-out numbers within it.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-opt-out-list \
    --opt-out-list-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--opt-out-list-name` | **Yes** | string | -- | Opt-out list name or ARN |

**Output Schema:**
```json
{
    "OptOutListArn": "string",
    "OptOutListName": "string",
    "CreatedTimestamp": "timestamp"
}
```

---

### 17.4 `put-opted-out-number`

Adds a phone number to an opt-out list.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 put-opted-out-number \
    --opt-out-list-name <value> \
    --opted-out-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--opt-out-list-name` | **Yes** | string | -- | Opt-out list name or ARN |
| `--opted-out-number` | **Yes** | string | -- | Phone number in E.164 format |

**Output Schema:**
```json
{
    "OptOutListArn": "string",
    "OptOutListName": "string",
    "OptedOutNumber": "string",
    "OptedOutTimestamp": "timestamp",
    "EndUserOptedOut": "boolean"
}
```

---

### 17.5 `describe-opted-out-numbers`

Describes opted-out numbers in an opt-out list.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-opted-out-numbers \
    --opt-out-list-name <value> \
    [--opted-out-numbers <value>] \
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
| `--opt-out-list-name` | **Yes** | string | -- | Opt-out list name or ARN |
| `--opted-out-numbers` | No | list | None | Phone numbers to look up (max 5) |
| `--filters` | No | list | None | Filter: `end-user-opted-out` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OptOutListArn": "string",
    "OptOutListName": "string",
    "OptedOutNumbers": [
        {
            "OptedOutNumber": "string",
            "OptedOutTimestamp": "timestamp",
            "EndUserOptedOut": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 17.6 `delete-opted-out-number`

Removes a phone number from an opt-out list. Each number can only be removed once every 30 days.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-opted-out-number \
    --opt-out-list-name <value> \
    --opted-out-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--opt-out-list-name` | **Yes** | string | -- | Opt-out list name or ARN |
| `--opted-out-number` | **Yes** | string | -- | Phone number in E.164 format |

**Output Schema:**
```json
{
    "OptOutListArn": "string",
    "OptOutListName": "string",
    "OptedOutNumber": "string",
    "OptedOutTimestamp": "timestamp",
    "EndUserOptedOut": "boolean"
}
```

---

## Keywords

### 17.7 `put-keyword`

Adds or updates a keyword on an origination identity (phone number or pool).

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 put-keyword \
    --origination-identity <value> \
    --keyword <value> \
    --keyword-message <value> \
    [--keyword-action <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origination-identity` | **Yes** | string | -- | Phone number or sender ID (ID or ARN) |
| `--keyword` | **Yes** | string | -- | Keyword text (1-30 chars). HELP and STOP cannot be modified |
| `--keyword-message` | **Yes** | string | -- | Response message (1-1600 chars) |
| `--keyword-action` | No | string | None | `AUTOMATIC_RESPONSE`, `OPT_OUT`, or `OPT_IN` |

**Output Schema:**
```json
{
    "OriginationIdentityArn": "string",
    "OriginationIdentity": "string",
    "Keyword": "string",
    "KeywordMessage": "string",
    "KeywordAction": "AUTOMATIC_RESPONSE|OPT_OUT|OPT_IN"
}
```

---

### 17.8 `describe-keywords`

Describes keywords on an origination identity.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-keywords \
    --origination-identity <value> \
    [--keywords <value>] \
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
| `--origination-identity` | **Yes** | string | -- | Phone number or sender ID (ID or ARN) |
| `--keywords` | No | list | None | Keywords to look up (max 5) |
| `--filters` | No | list | None | Filter: `keyword-action` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OriginationIdentityArn": "string",
    "OriginationIdentity": "string",
    "Keywords": [
        {
            "Keyword": "string",
            "KeywordMessage": "string",
            "KeywordAction": "AUTOMATIC_RESPONSE|OPT_OUT|OPT_IN"
        }
    ],
    "NextToken": "string"
}
```

---

### 17.9 `delete-keyword`

Deletes a keyword from an origination identity. HELP and STOP keywords cannot be deleted.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-keyword \
    --origination-identity <value> \
    --keyword <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origination-identity` | **Yes** | string | -- | Phone number or sender ID (ID or ARN) |
| `--keyword` | **Yes** | string | -- | Keyword to delete |

**Output Schema:**
```json
{
    "OriginationIdentityArn": "string",
    "OriginationIdentity": "string",
    "Keyword": "string",
    "KeywordMessage": "string",
    "KeywordAction": "AUTOMATIC_RESPONSE|OPT_OUT|OPT_IN"
}
```
