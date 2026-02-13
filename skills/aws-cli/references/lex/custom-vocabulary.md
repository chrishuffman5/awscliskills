# Custom Vocabulary

### 6.1 `batch-create-custom-vocabulary-item`

Creates multiple custom vocabulary items in a bot locale. Custom vocabulary improves speech recognition for specific words and phrases.

**Synopsis:**
```bash
aws lexv2-models batch-create-custom-vocabulary-item \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --custom-vocabulary-item-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--custom-vocabulary-item-list` | **Yes** | list | -- | List of vocabulary items to create |

**CustomVocabularyItem Structure:**
```json
[
    {
        "phrase": "string",
        "weight": "integer",
        "displayAs": "string"
    }
]
```

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "errors": [
        {
            "itemId": "string",
            "errorMessage": "string",
            "errorCode": "DUPLICATE_INPUT|RESOURCE_DOES_NOT_EXIST|RESOURCE_ALREADY_EXISTS|INTERNAL_SERVER_FAILURE"
        }
    ],
    "resources": [
        {
            "itemId": "string",
            "phrase": "string",
            "weight": "integer",
            "displayAs": "string"
        }
    ]
}
```

---

### 6.2 `batch-delete-custom-vocabulary-item`

Deletes multiple custom vocabulary items.

**Synopsis:**
```bash
aws lexv2-models batch-delete-custom-vocabulary-item \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --custom-vocabulary-item-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--custom-vocabulary-item-list` | **Yes** | list | -- | List of item IDs to delete |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "errors": [
        {
            "itemId": "string",
            "errorMessage": "string",
            "errorCode": "string"
        }
    ],
    "resources": [
        {
            "itemId": "string",
            "phrase": "string",
            "weight": "integer",
            "displayAs": "string"
        }
    ]
}
```

---

### 6.3 `batch-update-custom-vocabulary-item`

Updates multiple custom vocabulary items.

**Synopsis:**
```bash
aws lexv2-models batch-update-custom-vocabulary-item \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --custom-vocabulary-item-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--custom-vocabulary-item-list` | **Yes** | list | -- | List of items to update |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "errors": [],
    "resources": []
}
```

---

### 6.4 `delete-custom-vocabulary`

Deletes all custom vocabulary items for a bot locale.

**Synopsis:**
```bash
aws lexv2-models delete-custom-vocabulary \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "customVocabularyStatus": "Ready|Deleting|Exporting|Importing|Creating"
}
```

---

### 6.5 `describe-custom-vocabulary-metadata`

Gets metadata for the custom vocabulary associated with a bot locale.

**Synopsis:**
```bash
aws lexv2-models describe-custom-vocabulary-metadata \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "customVocabularyStatus": "Ready|Deleting|Exporting|Importing|Creating"
}
```

---

### 6.6 `list-custom-vocabulary-items`

Lists custom vocabulary items for a bot locale.

**Synopsis:**
```bash
aws lexv2-models list-custom-vocabulary-items \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--max-results` | No | integer | None | Maximum items to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "customVocabularyItems": [
        {
            "itemId": "string",
            "phrase": "string",
            "weight": "integer",
            "displayAs": "string"
        }
    ],
    "nextToken": "string"
}
```
