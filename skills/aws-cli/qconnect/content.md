# Content

### 3.1 `start-content-upload`

Gets a pre-signed URL for uploading content to a knowledge base.

**Synopsis:**
```bash
aws qconnect start-content-upload \
    --knowledge-base-id <value> \
    --content-type <value> \
    [--presigned-url-time-to-live <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN |
| `--content-type` | **Yes** | string | -- | MIME type (see supported types below) |
| `--presigned-url-time-to-live` | No | integer | None | URL expiry in seconds |

**Supported Content Types:** `text/plain`, `text/html`, `text/csv`, `application/pdf`, `application/vnd.openxmlformats-officedocument.wordprocessingml.document`

**Output Schema:**
```json
{
    "uploadId": "string",
    "url": "string",
    "urlExpiry": "timestamp",
    "headersToInclude": {"string": "string"}
}
```

---

### 3.2 `create-content`

Creates content in a knowledge base. Requires `uploadId` from `start-content-upload`.

**Synopsis:**
```bash
aws qconnect create-content \
    --knowledge-base-id <value> \
    --name <value> \
    --upload-id <value> \
    [--title <value>] \
    [--override-link-out-uri <value>] \
    [--metadata <value>] \
    [--client-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN |
| `--name` | **Yes** | string | -- | Content name (1-255 chars) |
| `--upload-id` | **Yes** | string | -- | Upload ID from `start-content-upload` |
| `--title` | No | string | None | Title (1-255 chars, defaults to name) |
| `--override-link-out-uri` | No | string | None | Article URI (1-4096 chars) |
| `--metadata` | No | map | None | Custom metadata (max 10 pairs) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "content": {
        "contentArn": "string",
        "contentId": "string",
        "knowledgeBaseArn": "string",
        "knowledgeBaseId": "string",
        "name": "string",
        "revisionId": "string",
        "title": "string",
        "contentType": "string",
        "status": "string",
        "metadata": {},
        "tags": {},
        "linkOutUri": "string",
        "url": "string",
        "urlExpiry": "timestamp"
    }
}
```

---

### 3.3 `get-content`

Gets content from a knowledge base.

**Synopsis:**
```bash
aws qconnect get-content \
    --knowledge-base-id <value> \
    --content-id <value>
```

**Output Schema:** Same as `create-content`.

---

### 3.4 `get-content-summary`

Gets a summary of content.

**Synopsis:**
```bash
aws qconnect get-content-summary \
    --knowledge-base-id <value> \
    --content-id <value>
```

---

### 3.5 `list-contents`

Lists content in a knowledge base. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-contents \
    --knowledge-base-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

---

### 3.6 `search-content`

Searches for content in a knowledge base.

**Synopsis:**
```bash
aws qconnect search-content \
    --knowledge-base-id <value> \
    --search-expression <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN |
| `--search-expression` | **Yes** | structure | -- | Search filters |

---

### 3.7 `update-content`

Updates content in a knowledge base.

**Synopsis:**
```bash
aws qconnect update-content \
    --knowledge-base-id <value> \
    --content-id <value> \
    [--revision-id <value>] \
    [--title <value>] \
    [--override-link-out-uri <value>] \
    [--metadata <value>] \
    [--upload-id <value>]
```

---

### 3.8 `delete-content`

Deletes content from a knowledge base.

**Synopsis:**
```bash
aws qconnect delete-content \
    --knowledge-base-id <value> \
    --content-id <value>
```

**Output:** None

---

## Content Associations

### 3.9 `create-content-association`

Creates an association between content and another resource.

**Synopsis:**
```bash
aws qconnect create-content-association \
    --knowledge-base-id <value> \
    --content-id <value> \
    --association-type <value> \
    --association <value> \
    [--client-token <value>] \
    [--tags <value>]
```

---

### 3.10 `get-content-association`

Gets a content association.

---

### 3.11 `list-content-associations`

Lists content associations. **Paginated operation.**

---

### 3.12 `delete-content-association`

Deletes a content association.
