# Email Templates

### 4.1 `create-email-template`

Creates an email template. Templates can contain subject, HTML body, and text body with substitution variables using `{{variable}}` syntax.

**Synopsis:**
```bash
aws sesv2 create-email-template \
    --template-name <value> \
    --template-content <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Name of the email template |
| `--template-content` | **Yes** | structure | -- | Template content (subject, HTML, text) |

**Template Content Structure:**
```json
{
    "Subject": "string",
    "Text": "string",
    "Html": "string"
}
```

**Output Schema:**
```json
{}
```

---

### 4.2 `delete-email-template`

Deletes an email template.

**Synopsis:**
```bash
aws sesv2 delete-email-template \
    --template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Name of the template to delete |

**Output Schema:**
```json
{}
```

---

### 4.3 `get-email-template`

Retrieves the content of an email template.

**Synopsis:**
```bash
aws sesv2 get-email-template \
    --template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Name of the template |

**Output Schema:**
```json
{
    "TemplateName": "string",
    "TemplateContent": {
        "Subject": "string",
        "Text": "string",
        "Html": "string"
    }
}
```

---

### 4.4 `list-email-templates`

Lists all email templates in the account. **Paginated operation.**

**Synopsis:**
```bash
aws sesv2 list-email-templates \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 10) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TemplatesMetadata": [
        {
            "TemplateName": "string",
            "CreatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-email-template`

Updates an email template's content.

**Synopsis:**
```bash
aws sesv2 update-email-template \
    --template-name <value> \
    --template-content <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Name of the template to update |
| `--template-content` | **Yes** | structure | -- | Updated template content (same structure as create) |

**Output Schema:**
```json
{}
```
