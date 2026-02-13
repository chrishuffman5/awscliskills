# Message Templates

### 8.1 `create-message-template`

Creates a message template for a specific channel.

**Synopsis:**
```bash
aws qconnect create-message-template \
    --knowledge-base-id <value> \
    --channel-subtype <value> \
    [--name <value>] \
    [--content <value>] \
    [--description <value>] \
    [--language <value>] \
    [--source-configuration <value>] \
    [--default-attributes <value>] \
    [--grouping-configuration <value>] \
    [--client-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN (MESSAGE_TEMPLATES type) |
| `--channel-subtype` | **Yes** | string | -- | `EMAIL`, `SMS`, `WHATSAPP`, `PUSH` |
| `--name` | No | string | None | Template name (1-255 chars) |
| `--content` | No | structure | None | Channel-specific content (see below) |
| `--description` | No | string | None | Description (1-255 chars) |
| `--language` | No | string | None | Language code (e.g., `en_US`) |
| `--source-configuration` | No | structure | None | WhatsApp source config |
| `--default-attributes` | No | structure | None | Default variable values |
| `--grouping-configuration` | No | structure | None | User group config |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Email Content:**
```json
{
    "email": {
        "subject": "string",
        "body": {
            "plainText": {"content": "string"},
            "html": {"content": "string"}
        },
        "headers": [{"name": "string", "value": "string"}]
    }
}
```

**SMS Content:**
```json
{
    "sms": {
        "body": {"plainText": {"content": "string"}}
    }
}
```

**Output Schema:**
```json
{
    "messageTemplate": {
        "messageTemplateArn": "string",
        "messageTemplateId": "string",
        "knowledgeBaseArn": "string",
        "knowledgeBaseId": "string",
        "name": "string",
        "channelSubtype": "string",
        "content": {},
        "description": "string",
        "language": "string",
        "createdTime": "timestamp",
        "lastModifiedTime": "timestamp",
        "tags": {}
    }
}
```

---

### 8.2 `create-message-template-version`

Creates an immutable version of a message template.

---

### 8.3 `create-message-template-attachment`

Attaches a file to a message template.

**Synopsis:**
```bash
aws qconnect create-message-template-attachment \
    --knowledge-base-id <value> \
    --message-template-id <value> \
    --content-disposition <value> \
    --name <value> \
    --body <value>
```

---

### 8.4 `get-message-template`

Gets a message template.

**Synopsis:**
```bash
aws qconnect get-message-template \
    --knowledge-base-id <value> \
    --message-template-id <value>
```

---

### 8.5 `list-message-templates`

Lists message templates. **Paginated operation.**

---

### 8.6 `list-message-template-versions`

Lists message template versions. **Paginated operation.**

---

### 8.7 `search-message-templates`

Searches message templates.

**Synopsis:**
```bash
aws qconnect search-message-templates \
    --knowledge-base-id <value> \
    --search-expression <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

---

### 8.8 `render-message-template`

Renders a message template with attribute values.

**Synopsis:**
```bash
aws qconnect render-message-template \
    --knowledge-base-id <value> \
    --message-template-id <value> \
    --attributes <value>
```

---

### 8.9 `update-message-template`

Updates message template content.

---

### 8.10 `update-message-template-metadata`

Updates message template metadata (name, description, grouping).

---

### 8.11 `activate-message-template`

Activates a specific version of a message template.

**Synopsis:**
```bash
aws qconnect activate-message-template \
    --knowledge-base-id <value> \
    --message-template-id <value> \
    --version-number <value>
```

---

### 8.12 `deactivate-message-template`

Deactivates a specific version of a message template.

---

### 8.13 `delete-message-template`

Deletes a message template.

**Output:** None

---

### 8.14 `delete-message-template-attachment`

Deletes an attachment from a message template.

**Output:** None
