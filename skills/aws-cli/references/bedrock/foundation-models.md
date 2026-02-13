# Foundation Models

### `list-foundation-models`

Lists Amazon Bedrock foundation models that you can use. You can filter the results by provider, output modality, customization type, and inference type.

**Synopsis:**
```bash
aws bedrock list-foundation-models \
    [--by-provider <value>] \
    [--by-customization-type <value>] \
    [--by-output-modality <value>] \
    [--by-inference-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--by-provider` | No | string | None | Filter by model provider (e.g., `Anthropic`, `Amazon`, `Meta`). Pattern: `[A-Za-z0-9- ]{1,63}` |
| `--by-customization-type` | No | string | None | Filter by customization type: `FINE_TUNING`, `CONTINUED_PRE_TRAINING`, `DISTILLATION` |
| `--by-output-modality` | No | string | None | Filter by output modality: `TEXT`, `IMAGE`, `EMBEDDING` |
| `--by-inference-type` | No | string | None | Filter by inference type: `ON_DEMAND`, `PROVISIONED` |

**Output Schema:**
```json
{
    "modelSummaries": [
        {
            "modelArn": "string",
            "modelId": "string",
            "modelName": "string",
            "providerName": "string",
            "inputModalities": ["TEXT|IMAGE|EMBEDDING"],
            "outputModalities": ["TEXT|IMAGE|EMBEDDING"],
            "responseStreamingSupported": true|false,
            "customizationsSupported": ["FINE_TUNING|CONTINUED_PRE_TRAINING|DISTILLATION"],
            "inferenceTypesSupported": ["ON_DEMAND|PROVISIONED"],
            "modelLifecycle": {
                "status": "ACTIVE|LEGACY"
            }
        }
    ]
}
```

---

### `get-foundation-model`

Gets details about a specified Amazon Bedrock foundation model.

**Synopsis:**
```bash
aws bedrock get-foundation-model \
    --model-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-identifier` | **Yes** | string | -- | The model ID or ARN. Min: 1, Max: 2048 |

**Output Schema:**
```json
{
    "modelDetails": {
        "modelArn": "string",
        "modelId": "string",
        "modelName": "string",
        "providerName": "string",
        "inputModalities": ["TEXT|IMAGE|EMBEDDING"],
        "outputModalities": ["TEXT|IMAGE|EMBEDDING"],
        "responseStreamingSupported": true|false,
        "customizationsSupported": ["FINE_TUNING|CONTINUED_PRE_TRAINING|DISTILLATION"],
        "inferenceTypesSupported": ["ON_DEMAND|PROVISIONED"],
        "modelLifecycle": {
            "status": "ACTIVE|LEGACY"
        }
    }
}
```

---

### `list-foundation-model-agreement-offers`

Lists agreement offers for a specified foundation model.

**Synopsis:**
```bash
aws bedrock list-foundation-model-agreement-offers \
    --model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | The model ID to list agreement offers for |

**Output Schema:**
```json
{
    "modelId": "string",
    "offers": [
        {
            "offerToken": "string"
        }
    ]
}
```

---

### `create-foundation-model-agreement`

Creates an agreement for a specified foundation model.

**Synopsis:**
```bash
aws bedrock create-foundation-model-agreement \
    --model-id <value> \
    --offer-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | The model ID to create the agreement for |
| `--offer-token` | **Yes** | string | -- | The offer token for the agreement |

**Output Schema:**
```json
{
    "modelId": "string"
}
```

---

### `delete-foundation-model-agreement`

Deletes an agreement for a specified foundation model.

**Synopsis:**
```bash
aws bedrock delete-foundation-model-agreement \
    --model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | The model ID to delete the agreement for |

**Output:** None (HTTP 200 on success)

---

### `get-foundation-model-availability`

Gets the availability of a foundation model.

**Synopsis:**
```bash
aws bedrock get-foundation-model-availability \
    --model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | The model ID to check availability for |

**Output Schema:**
```json
{
    "modelId": "string",
    "agreementAvailability": {
        "status": "AVAILABLE|PENDING|IN_PROGRESS|NOT_AVAILABLE"
    },
    "authorizationStatus": "AUTHORIZED|NOT_AUTHORIZED",
    "entitlementAvailability": "AVAILABLE|NOT_AVAILABLE"
}
```
