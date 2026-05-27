# Engagements

### 10.1 `start-engagement`

Starts an engagement to a contact or escalation plan. The engagement engages each contact specified in the incident.

**Synopsis:**
```bash
aws ssm-contacts start-engagement \
    --contact-id <value> \
    --sender <value> \
    --subject <value> \
    --content <value> \
    [--public-subject <value>] \
    [--public-content <value>] \
    [--incident-id <value>] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-id` | **Yes** | string | -- | Contact or escalation plan ARN |
| `--sender` | **Yes** | string | -- | Sender of the engagement (user/service) |
| `--subject` | **Yes** | string | -- | Subject of the engagement |
| `--content` | **Yes** | string | -- | Content/body of the engagement |
| `--public-subject` | No | string | None | Public subject (for SMS/voice) |
| `--public-content` | No | string | None | Public content (for SMS/voice) |
| `--incident-id` | No | string | None | ARN of the incident |
| `--idempotency-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "EngagementArn": "string"
}
```

---

### 10.2 `stop-engagement`

Stops an engagement before it finishes the final stage of the escalation plan or engagement plan.

**Synopsis:**
```bash
aws ssm-contacts stop-engagement \
    --engagement-id <value> \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engagement-id` | **Yes** | string | -- | Engagement ARN |
| `--reason` | No | string | None | Reason for stopping |

**Output Schema:**
```json
{}
```

---

### 10.3 `describe-engagement`

Describes an engagement to a contact channel.

**Synopsis:**
```bash
aws ssm-contacts describe-engagement \
    --engagement-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engagement-id` | **Yes** | string | -- | Engagement ARN |

**Output Schema:**
```json
{
    "ContactArn": "string",
    "EngagementArn": "string",
    "Sender": "string",
    "Subject": "string",
    "Content": "string",
    "PublicSubject": "string",
    "PublicContent": "string",
    "IncidentId": "string",
    "StartTime": "timestamp",
    "StopTime": "timestamp"
}
```

---

### 10.4 `list-engagements`

Lists all engagements that have happened in an incident. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-engagements \
    [--incident-id <value>] \
    [--time-range-value <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-id` | No | string | None | Filter by incident ARN |
| `--time-range-value` | No | structure | None | Time range filter |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Engagements": [
        {
            "EngagementArn": "string",
            "ContactArn": "string",
            "Sender": "string",
            "IncidentId": "string",
            "StartTime": "timestamp",
            "StopTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.5 `accept-page`

Used to acknowledge an engagement to a contact channel during an incident.

**Synopsis:**
```bash
aws ssm-contacts accept-page \
    --page-id <value> \
    --accept-type <value> \
    --accept-code <value> \
    [--note <value>] \
    [--contact-channel-id <value>] \
    [--accept-code-validation <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-id` | **Yes** | string | -- | Page ARN |
| `--accept-type` | **Yes** | string | -- | `DELIVERED`, `READ` |
| `--accept-code` | **Yes** | string | -- | 6-digit code sent to the contact channel |
| `--note` | No | string | None | Note about acceptance |
| `--contact-channel-id` | No | string | None | Contact channel that received the page |
| `--accept-code-validation` | No | string | None | `IGNORE` or `ENFORCE` |

**Output Schema:**
```json
{}
```

---

### 10.6 `describe-page`

Lists details of the engagement to a contact channel.

**Synopsis:**
```bash
aws ssm-contacts describe-page \
    --page-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-id` | **Yes** | string | -- | Page ARN |

**Output Schema:**
```json
{
    "PageArn": "string",
    "EngagementArn": "string",
    "ContactArn": "string",
    "Sender": "string",
    "Subject": "string",
    "Content": "string",
    "PublicSubject": "string",
    "PublicContent": "string",
    "IncidentId": "string",
    "SentTime": "timestamp",
    "ReadTime": "timestamp",
    "DeliveryTime": "timestamp"
}
```

---

### 10.7 `list-pages-by-contact`

Lists the engagements to a contact's contact channels. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-pages-by-contact \
    --contact-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-id` | **Yes** | string | -- | Contact ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Pages": [
        {
            "PageArn": "string",
            "EngagementArn": "string",
            "ContactArn": "string",
            "Sender": "string",
            "IncidentId": "string",
            "SentTime": "timestamp",
            "DeliveryTime": "timestamp",
            "ReadTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.8 `list-pages-by-engagement`

Lists the engagements to contact channels that occurred by engaging a contact. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-pages-by-engagement \
    --engagement-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engagement-id` | **Yes** | string | -- | Engagement ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Pages": [
        {
            "PageArn": "string",
            "EngagementArn": "string",
            "ContactArn": "string",
            "Sender": "string",
            "IncidentId": "string",
            "SentTime": "timestamp",
            "DeliveryTime": "timestamp",
            "ReadTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.9 `list-page-receipts`

Lists all of the engagements to contact channels that have been acknowledged. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-page-receipts \
    --page-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-id` | **Yes** | string | -- | Page ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Receipts": [
        {
            "ContactChannelArn": "string",
            "ReceiptType": "DELIVERED|ERROR|READ|SENT|STOP",
            "ReceiptInfo": "string",
            "ReceiptTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.10 `list-page-resolutions`

Returns the resolution path of engagements to a contact channel. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-page-resolutions \
    --page-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-id` | **Yes** | string | -- | Page ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "PageResolutions": [
        {
            "ContactArn": "string",
            "Type": "PERSONAL|ESCALATION|ONCALL_SCHEDULE",
            "StageIndex": "integer"
        }
    ],
    "NextToken": "string"
}
```
