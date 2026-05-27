# Templates

All template commands follow the same pattern per channel type (email, SMS, push, voice, in-app). Templates support versioning via `list-template-versions` and `update-template-active-version`.

### 5.1 `create-email-template`

Creates an email message template.

**Synopsis:**
```bash
aws pinpoint create-email-template \
    --template-name <value> \
    --email-template-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--email-template-request` | **Yes** | structure | -- | Template content |

**EmailTemplateRequest Fields:**
- `Subject` (string): Email subject line
- `HtmlPart` (string): HTML body
- `TextPart` (string): Plain text body
- `DefaultSubstitutions` (string): Default substitution values (JSON)
- `RecommenderId` (string): Recommender model ID
- `Headers` (list): Email headers (Name/Value pairs, max 15)
- `TemplateDescription` (string): Template description
- `tags` (map): Tags

**Output Schema:**
```json
{
    "CreateTemplateMessageBody": {
        "Arn": "string",
        "Message": "string",
        "RequestID": "string"
    }
}
```

---

### 5.2-5.5 Create Other Templates

`create-sms-template`, `create-push-template`, `create-voice-template`, `create-in-app-template` follow the same pattern with channel-specific request structures:

**SMS:** `--sms-template-request` with `Body`, `DefaultSubstitutions`, `RecommenderId`, `TemplateDescription`, `tags`

**Push:** `--push-notification-template-request` with `Default` (Action, Body, Sound, Title, Url), `ADM`, `APNS`, `Baidu`, `GCM` (channel-specific overrides), `DefaultSubstitutions`, `RecommenderId`, `TemplateDescription`, `tags`

**Voice:** `--voice-template-request` with `Body`, `LanguageCode`, `VoiceId`, `DefaultSubstitutions`, `TemplateDescription`, `tags`

**In-App:** `--in-app-template-request` with `Content` (list of InAppMessageContent), `Layout` (`BOTTOM_BANNER|TOP_BANNER|OVERLAYS|MOBILE_FEED|MIDDLE_BANNER|CAROUSEL`), `CustomConfig`, `TemplateDescription`, `tags`

---

### 5.6-5.10 Get Templates

```bash
aws pinpoint get-email-template --template-name <value> [--version <value>]
aws pinpoint get-sms-template --template-name <value> [--version <value>]
aws pinpoint get-push-template --template-name <value> [--version <value>]
aws pinpoint get-voice-template --template-name <value> [--version <value>]
aws pinpoint get-in-app-template --template-name <value> [--version <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--version` | No | string | Active version | Specific version to retrieve |

---

### 5.11-5.15 Update Templates

```bash
aws pinpoint update-email-template --template-name <value> --email-template-request <value> [--create-new-version | --no-create-new-version] [--version <value>]
```

Additional parameters for all update commands:

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--create-new-version` | No | boolean | false | Create a new version instead of updating |
| `--version` | No | string | None | Version to update |

---

### 5.16-5.20 Delete Templates

```bash
aws pinpoint delete-email-template --template-name <value> [--version <value>]
aws pinpoint delete-sms-template --template-name <value> [--version <value>]
aws pinpoint delete-push-template --template-name <value> [--version <value>]
aws pinpoint delete-voice-template --template-name <value> [--version <value>]
aws pinpoint delete-in-app-template --template-name <value> [--version <value>]
```

---

### 5.21 `list-templates`

Lists all message templates.

**Synopsis:**
```bash
aws pinpoint list-templates \
    [--next-token <value>] \
    [--page-size <value>] \
    [--prefix <value>] \
    [--template-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--page-size` | No | string | None | Max items per page |
| `--prefix` | No | string | None | Filter by name prefix |
| `--template-type` | No | string | None | Filter: `EMAIL`, `SMS`, `PUSH`, `VOICE`, `INAPP` |

**Output Schema:**
```json
{
    "TemplatesResponse": {
        "Item": [
            {
                "Arn": "string",
                "CreationDate": "string",
                "DefaultSubstitutions": "string",
                "LastModifiedDate": "string",
                "TemplateDescription": "string",
                "TemplateName": "string",
                "TemplateType": "EMAIL|SMS|PUSH|VOICE|INAPP",
                "Version": "string",
                "tags": {}
            }
        ],
        "NextToken": "string"
    }
}
```

---

### 5.22 `list-template-versions`

Lists versions of a template.

**Synopsis:**
```bash
aws pinpoint list-template-versions \
    --template-name <value> \
    --template-type <value> \
    [--next-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### 5.23 `update-template-active-version`

Sets the active version of a template.

**Synopsis:**
```bash
aws pinpoint update-template-active-version \
    --template-name <value> \
    --template-type <value> \
    --template-active-version-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--template-type` | **Yes** | string | -- | `EMAIL`, `SMS`, `PUSH`, `VOICE`, `INAPP` |
| `--template-active-version-request` | **Yes** | structure | -- | Shorthand: `Version=string` |
