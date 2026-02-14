# Email

### 21.1 `create-email-address`

Creates an email address for the specified instance.

**Synopsis:**
```bash
aws connect create-email-address \
    --instance-id <value> \
    --email-address <value> \
    [--description <value>] \
    [--display-name <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--email-address` | **Yes** | string | -- | Email address (1-255 chars) |
| `--description` | No | string | None | Description (0-4096 chars) |
| `--display-name` | No | string | None | Display name (0-256 chars) |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "EmailAddressId": "string",
    "EmailAddressArn": "string"
}
```

---

### 21.2 `describe-email-address`

Describes an email address.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--email-address-id` | **Yes** | string | -- | Email address ID |

**Output Schema:**
```json
{
    "EmailAddressId": "string",
    "EmailAddressArn": "string",
    "EmailAddress": "string",
    "DisplayName": "string",
    "Description": "string",
    "Tags": { "key": "value" },
    "CreateTimestamp": "string",
    "ModifiedTimestamp": "string"
}
```

---

### 21.3 `update-email-address-metadata`

Updates email address metadata.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--email-address-id` | **Yes** | string | -- | Email address ID |
| `--description` | No | string | None | Updated description |
| `--display-name` | No | string | None | Updated display name |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "EmailAddressId": "string",
    "EmailAddressArn": "string"
}
```

---

### 21.4 `delete-email-address`

Deletes an email address.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--email-address-id` | **Yes** | string | -- | Email address ID |

**Output:** None

---

### 21.5 `search-email-addresses`

Searches email addresses. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-criteria` | No | structure | None | Search criteria |
| `--search-filter` | No | structure | None | Tag filter |

---

### 21.6 `associate-email-address-alias`

Associates an email alias with an email address.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--email-address-id` | **Yes** | string | -- | Email address ID |
| `--email-address-alias` | **Yes** | string | -- | Alias email address |

**Output:** None

---

### 21.7 `disassociate-email-address-alias`

Removes an email alias from an email address.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--email-address-id` | **Yes** | string | -- | Email address ID |
| `--email-address-alias` | **Yes** | string | -- | Alias email address |

**Output:** None

---

### 21.8 `start-email-contact`

Starts an inbound email contact.

**Synopsis:**
```bash
aws connect start-email-contact \
    --instance-id <value> \
    --destination-email-address <value> \
    --from-email-address <value> \
    --email-message <value> \
    [--name <value>] \
    [--description <value>] \
    [--references <value>] \
    [--contact-flow-id <value>] \
    [--additional-recipients <value>] \
    [--attachments <value>] \
    [--segment-attributes <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--destination-email-address` | **Yes** | structure | -- | Destination email (Connect email address) |
| `--from-email-address` | **Yes** | structure | -- | Sender email address |
| `--email-message` | **Yes** | structure | -- | Email message content |
| `--name` | No | string | None | Contact name |
| `--description` | No | string | None | Description |
| `--references` | No | map | None | References |
| `--contact-flow-id` | No | string | None | Flow ID |
| `--additional-recipients` | No | structure | None | CC recipients |
| `--attachments` | No | list | None | Attachments |
| `--segment-attributes` | No | map | None | Segment attributes |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ContactId": "string"
}
```

---

### 21.9 `start-outbound-email-contact`

Starts an outbound email contact.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Existing contact ID |
| `--email-message` | **Yes** | structure | -- | Email message content |
| `--from-email-address` | No | structure | None | Sender address |
| `--destination-email-address` | No | structure | None | Destination address |
| `--additional-recipients` | No | structure | None | CC recipients |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ContactId": "string"
}
```

---

### 21.10 `send-outbound-email`

Sends an outbound email from a contact.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--email-message` | **Yes** | structure | -- | Email message content |
| `--from-email-address` | No | structure | None | Sender address |
| `--destination-email-address` | No | structure | None | Destination address |
| `--additional-recipients` | No | structure | None | CC recipients |
| `--traffic-type` | No | string | None | Traffic type |
| `--source-campaign` | No | structure | None | Source campaign |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None
