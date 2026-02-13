# Contact Channels

### 9.1 `create-contact-channel`

A contact channel is the method that Incident Manager uses to engage your contact.

**Synopsis:**
```bash
aws ssm-contacts create-contact-channel \
    --contact-id <value> \
    --name <value> \
    --type <value> \
    --delivery-address <value> \
    [--defer-activation | --no-defer-activation] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-id` | **Yes** | string | -- | Contact ARN |
| `--name` | **Yes** | string | -- | Channel name (1-255 chars) |
| `--type` | **Yes** | string | -- | Channel type: `SMS`, `VOICE`, `EMAIL` |
| `--delivery-address` | **Yes** | structure | -- | Delivery address. Shorthand: `SimpleAddress=string` (phone number or email) |
| `--defer-activation` | No | boolean | false | Defer activation (do not send activation code immediately) |
| `--idempotency-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "ContactChannelArn": "string"
}
```

---

### 9.2 `delete-contact-channel`

To no longer receive Incident Manager engagements to a contact channel, you can delete the channel.

**Synopsis:**
```bash
aws ssm-contacts delete-contact-channel \
    --contact-channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-channel-id` | **Yes** | string | -- | Contact channel ARN |

**Output Schema:**
```json
{}
```

---

### 9.3 `get-contact-channel`

List details of a specific contact channel.

**Synopsis:**
```bash
aws ssm-contacts get-contact-channel \
    --contact-channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-channel-id` | **Yes** | string | -- | Contact channel ARN |

**Output Schema:**
```json
{
    "ContactArn": "string",
    "ContactChannelArn": "string",
    "Name": "string",
    "Type": "SMS|VOICE|EMAIL",
    "DeliveryAddress": {
        "SimpleAddress": "string"
    },
    "ActivationStatus": "ACTIVATED|NOT_ACTIVATED"
}
```

---

### 9.4 `list-contact-channels`

Lists all contact channels for the specified contact. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-contact-channels \
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
    "ContactChannels": [
        {
            "ContactChannelArn": "string",
            "ContactArn": "string",
            "Name": "string",
            "Type": "SMS|VOICE|EMAIL",
            "DeliveryAddress": {
                "SimpleAddress": "string"
            },
            "ActivationStatus": "ACTIVATED|NOT_ACTIVATED"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `update-contact-channel`

Updates a contact's contact channel.

**Synopsis:**
```bash
aws ssm-contacts update-contact-channel \
    --contact-channel-id <value> \
    [--name <value>] \
    [--delivery-address <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-channel-id` | **Yes** | string | -- | Contact channel ARN |
| `--name` | No | string | None | Updated name |
| `--delivery-address` | No | structure | None | Updated delivery address |

**Output Schema:**
```json
{}
```

---

### 9.6 `activate-contact-channel`

Activates a contact's contact channel. Incident Manager can then engage the contact through the channel.

**Synopsis:**
```bash
aws ssm-contacts activate-contact-channel \
    --contact-channel-id <value> \
    --activation-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-channel-id` | **Yes** | string | -- | Contact channel ARN |
| `--activation-code` | **Yes** | string | -- | Activation code sent to the channel |

**Output Schema:**
```json
{}
```

---

### 9.7 `deactivate-contact-channel`

To no longer receive Incident Manager engagements through a contact channel, you can deactivate it.

**Synopsis:**
```bash
aws ssm-contacts deactivate-contact-channel \
    --contact-channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-channel-id` | **Yes** | string | -- | Contact channel ARN |

**Output Schema:**
```json
{}
```

---

### 9.8 `send-activation-code`

Sends an activation code to a contact channel. The contact can use this code to activate the contact channel.

**Synopsis:**
```bash
aws ssm-contacts send-activation-code \
    --contact-channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-channel-id` | **Yes** | string | -- | Contact channel ARN |

**Output Schema:**
```json
{}
```
