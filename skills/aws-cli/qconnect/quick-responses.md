# Quick Responses

### 4.1 `create-quick-response`

Creates a quick response for agents to use in conversations.

**Synopsis:**
```bash
aws qconnect create-quick-response \
    --knowledge-base-id <value> \
    --name <value> \
    --content <value> \
    [--content-type <value>] \
    [--grouping-configuration <value>] \
    [--description <value>] \
    [--shortcut-key <value>] \
    [--is-active | --no-is-active] \
    [--channels <value>] \
    [--language <value>] \
    [--client-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN (must be QUICK_RESPONSES type) |
| `--name` | **Yes** | string | -- | Name (1-100 chars) |
| `--content` | **Yes** | structure | -- | Content: `content=string` (1-1024 chars) |
| `--content-type` | No | string | None | `application/x.quickresponse;format=plain` or `...format=markdown` |
| `--grouping-configuration` | No | structure | None | User group config: `criteria=string,values=string,...` |
| `--description` | No | string | None | Description (1-255 chars) |
| `--shortcut-key` | No | string | None | Shortcut key (1-10 chars) |
| `--is-active` | No | boolean | None | Whether active |
| `--channels` | No | list | None | Connect channels (e.g., Chat) |
| `--language` | No | string | None | Language code (e.g., `en_US`) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "quickResponse": {
        "quickResponseArn": "string",
        "quickResponseId": "string",
        "knowledgeBaseArn": "string",
        "knowledgeBaseId": "string",
        "name": "string",
        "contentType": "string",
        "status": "CREATE_IN_PROGRESS|CREATE_FAILED|CREATED|DELETE_IN_PROGRESS|DELETE_FAILED|DELETED|UPDATE_IN_PROGRESS|UPDATE_FAILED",
        "createdTime": "timestamp",
        "lastModifiedTime": "timestamp",
        "contents": {
            "plainText": {"content": "string"},
            "markdown": {"content": "string"}
        },
        "description": "string",
        "shortcutKey": "string",
        "isActive": "boolean",
        "channels": ["string"],
        "language": "string",
        "tags": {}
    }
}
```

---

### 4.2 `get-quick-response`

Gets a quick response.

**Synopsis:**
```bash
aws qconnect get-quick-response \
    --knowledge-base-id <value> \
    --quick-response-id <value>
```

---

### 4.3 `list-quick-responses`

Lists quick responses. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-quick-responses \
    --knowledge-base-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

---

### 4.4 `search-quick-responses`

Searches quick responses in a knowledge base.

**Synopsis:**
```bash
aws qconnect search-quick-responses \
    --knowledge-base-id <value> \
    --search-expression <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--attributes <value>]
```

---

### 4.5 `update-quick-response`

Updates a quick response.

**Synopsis:**
```bash
aws qconnect update-quick-response \
    --knowledge-base-id <value> \
    --quick-response-id <value> \
    [--name <value>] \
    [--content <value>] \
    [--content-type <value>] \
    [--description <value>] \
    [--is-active | --no-is-active] \
    [--channels <value>] \
    [--language <value>]
```

---

### 4.6 `delete-quick-response`

Deletes a quick response.

**Synopsis:**
```bash
aws qconnect delete-quick-response \
    --knowledge-base-id <value> \
    --quick-response-id <value>
```

**Output:** None
