# Slots

### 5.1 `create-slot`

Creates a slot in an intent. A slot is a parameter that the bot must collect from the user to fulfill the intent.

**Synopsis:**
```bash
aws lexv2-models create-slot \
    --slot-name <value> \
    --value-elicitation-setting <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --intent-id <value> \
    [--description <value>] \
    [--slot-type-id <value>] \
    [--obfuscation-setting <value>] \
    [--multiple-values-setting <value>] \
    [--sub-slot-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--slot-name` | **Yes** | string | -- | Slot name (1-100 chars) |
| `--value-elicitation-setting` | **Yes** | structure | -- | Prompts and constraints for eliciting the slot value |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--intent-id` | **Yes** | string | -- | Intent identifier (10 chars) |
| `--description` | No | string | None | Slot description (0-2000 chars) |
| `--slot-type-id` | No | string | None | Slot type ID (built-in or custom, 1-25 chars) |
| `--obfuscation-setting` | No | structure | None | Obfuscation settings: `obfuscationSettingType=None\|DefaultObfuscation` |
| `--multiple-values-setting` | No | structure | None | Allow multiple values: `allowMultipleValues=true\|false` |
| `--sub-slot-setting` | No | structure | None | Sub-slot configuration for composite slots |

**ValueElicitationSetting Structure (simplified):**
```json
{
    "slotConstraint": "Required|Optional",
    "promptSpecification": {
        "messageGroups": [
            {
                "message": {
                    "plainTextMessage": {"value": "What size pizza?"}
                }
            }
        ],
        "maxRetries": 2,
        "allowInterrupt": true
    },
    "defaultValueSpecification": {
        "defaultValueList": [{"defaultValue": "string"}]
    },
    "sampleUtterances": [{"utterance": "string"}],
    "waitAndContinueSpecification": {},
    "slotCaptureSetting": {}
}
```

**Output Schema:**
```json
{
    "slotId": "string",
    "slotName": "string",
    "description": "string",
    "slotTypeId": "string",
    "valueElicitationSetting": {},
    "obfuscationSetting": {"obfuscationSettingType": "None|DefaultObfuscation"},
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "intentId": "string",
    "creationDateTime": "timestamp",
    "multipleValuesSetting": {"allowMultipleValues": true|false},
    "subSlotSetting": {}
}
```

---

### 5.2 `delete-slot`

Deletes a slot from an intent.

**Synopsis:**
```bash
aws lexv2-models delete-slot \
    --slot-id <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --intent-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--slot-id` | **Yes** | string | -- | Slot identifier (10 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--intent-id` | **Yes** | string | -- | Intent identifier (10 chars) |

**Output:** None

---

### 5.3 `describe-slot`

Gets metadata for a slot.

**Synopsis:**
```bash
aws lexv2-models describe-slot \
    --slot-id <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --intent-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--slot-id` | **Yes** | string | -- | Slot identifier (10 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--intent-id` | **Yes** | string | -- | Intent identifier (10 chars) |

**Output Schema:**
```json
{
    "slotId": "string",
    "slotName": "string",
    "description": "string",
    "slotTypeId": "string",
    "valueElicitationSetting": {},
    "obfuscationSetting": {},
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "intentId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "multipleValuesSetting": {},
    "subSlotSetting": {}
}
```

---

### 5.4 `list-slots`

Lists all slots in an intent.

**Synopsis:**
```bash
aws lexv2-models list-slots \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --intent-id <value> \
    [--sort-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--intent-id` | **Yes** | string | -- | Intent identifier |
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum slots to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "intentId": "string",
    "slotSummaries": [
        {
            "slotId": "string",
            "slotName": "string",
            "description": "string",
            "slotConstraint": "Required|Optional",
            "slotTypeId": "string",
            "valueElicitationPromptSpecification": {},
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `update-slot`

Updates an existing slot configuration.

**Synopsis:**
```bash
aws lexv2-models update-slot \
    --slot-id <value> \
    --slot-name <value> \
    --value-elicitation-setting <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --intent-id <value> \
    [--description <value>] \
    [--slot-type-id <value>] \
    [--obfuscation-setting <value>] \
    [--multiple-values-setting <value>] \
    [--sub-slot-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--slot-id` | **Yes** | string | -- | Slot identifier (10 chars) |
| `--slot-name` | **Yes** | string | -- | Updated slot name (1-100 chars) |
| `--value-elicitation-setting` | **Yes** | structure | -- | Updated elicitation settings |
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--intent-id` | **Yes** | string | -- | Intent identifier |
| `--description` | No | string | None | Updated description |
| `--slot-type-id` | No | string | None | Updated slot type |
| `--obfuscation-setting` | No | structure | None | Obfuscation settings |
| `--multiple-values-setting` | No | structure | None | Multiple values settings |
| `--sub-slot-setting` | No | structure | None | Sub-slot settings |

**Output Schema:**
```json
{
    "slotId": "string",
    "slotName": "string",
    "description": "string",
    "slotTypeId": "string",
    "valueElicitationSetting": {},
    "obfuscationSetting": {},
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "intentId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "multipleValuesSetting": {},
    "subSlotSetting": {}
}
```

---

### 5.6 `create-slot-type`

Creates a custom slot type. A slot type defines the values that a slot can accept.

**Synopsis:**
```bash
aws lexv2-models create-slot-type \
    --slot-type-name <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--description <value>] \
    [--slot-type-values <value>] \
    [--value-selection-setting <value>] \
    [--parent-slot-type-signature <value>] \
    [--external-source-setting <value>] \
    [--composite-slot-type-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--slot-type-name` | **Yes** | string | -- | Slot type name (1-100 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--description` | No | string | None | Description (0-2000 chars) |
| `--slot-type-values` | No | list | None | List of values the slot type can take |
| `--value-selection-setting` | No | structure | None | Value resolution strategy |
| `--parent-slot-type-signature` | No | string | None | Built-in slot type to extend |
| `--external-source-setting` | No | structure | None | External grammar slot type source |
| `--composite-slot-type-setting` | No | structure | None | Composite slot type sub-slots |

**Output Schema:**
```json
{
    "slotTypeId": "string",
    "slotTypeName": "string",
    "description": "string",
    "slotTypeValues": [
        {
            "sampleValue": {"value": "string"},
            "synonyms": [{"value": "string"}]
        }
    ],
    "valueSelectionSetting": {
        "resolutionStrategy": "OriginalValue|TopResolution|Concatenation",
        "regexFilter": {"pattern": "string"},
        "advancedRecognitionSetting": {"audioRecognitionStrategy": "UseSlotValuesAsCustomVocabulary"}
    },
    "parentSlotTypeSignature": "string",
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "creationDateTime": "timestamp",
    "externalSourceSetting": {},
    "compositeSlotTypeSetting": {}
}
```

---

### 5.7 `delete-slot-type`

Deletes a slot type.

**Synopsis:**
```bash
aws lexv2-models delete-slot-type \
    --slot-type-id <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--slot-type-id` | **Yes** | string | -- | Slot type identifier |
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--skip-resource-in-use-check` | No | boolean | false | Skip in-use check |

**Output:** None

---

### 5.8 `describe-slot-type`

Gets metadata for a slot type.

**Synopsis:**
```bash
aws lexv2-models describe-slot-type \
    --slot-type-id <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--slot-type-id` | **Yes** | string | -- | Slot type identifier |
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "slotTypeId": "string",
    "slotTypeName": "string",
    "description": "string",
    "slotTypeValues": [],
    "valueSelectionSetting": {},
    "parentSlotTypeSignature": "string",
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "externalSourceSetting": {},
    "compositeSlotTypeSetting": {}
}
```

---

### 5.9 `list-slot-types`

Lists all slot types in a bot locale.

**Synopsis:**
```bash
aws lexv2-models list-slot-types \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--sort-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum slot types to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "slotTypeSummaries": [
        {
            "slotTypeId": "string",
            "slotTypeName": "string",
            "description": "string",
            "parentSlotTypeSignature": "string",
            "lastUpdatedDateTime": "timestamp",
            "slotTypeCategory": "Custom|Extended|ExternalGrammar|Composite"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.10 `update-slot-type`

Updates an existing slot type.

**Synopsis:**
```bash
aws lexv2-models update-slot-type \
    --slot-type-id <value> \
    --slot-type-name <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--description <value>] \
    [--slot-type-values <value>] \
    [--value-selection-setting <value>] \
    [--parent-slot-type-signature <value>] \
    [--external-source-setting <value>] \
    [--composite-slot-type-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--slot-type-id` | **Yes** | string | -- | Slot type identifier |
| `--slot-type-name` | **Yes** | string | -- | Updated slot type name |
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--description` | No | string | None | Updated description |
| `--slot-type-values` | No | list | None | Updated slot type values |
| `--value-selection-setting` | No | structure | None | Updated value selection setting |
| `--parent-slot-type-signature` | No | string | None | Updated parent slot type |
| `--external-source-setting` | No | structure | None | External source settings |
| `--composite-slot-type-setting` | No | structure | None | Composite slot settings |

**Output Schema:**
```json
{
    "slotTypeId": "string",
    "slotTypeName": "string",
    "description": "string",
    "slotTypeValues": [],
    "valueSelectionSetting": {},
    "parentSlotTypeSignature": "string",
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "externalSourceSetting": {},
    "compositeSlotTypeSetting": {}
}
```

---

### 5.11 `list-built-in-slot-types`

Lists built-in slot types available for a locale.

**Synopsis:**
```bash
aws lexv2-models list-built-in-slot-types \
    --locale-id <value> \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--sort-by` | No | structure | None | Sort field and order |
| `--max-results` | No | integer | None | Maximum results (1-20) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "builtInSlotTypeSummaries": [
        {
            "slotTypeSignature": "string",
            "description": "string"
        }
    ],
    "nextToken": "string",
    "localeId": "string"
}
```
