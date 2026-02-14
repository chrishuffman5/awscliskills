# State Templates

### 7.1 `create-state-template`

Creates a state template for tracking vehicle state via MQTT.

**Synopsis:**
```bash
aws iotfleetwise create-state-template \
    --name <value> \
    --signal-catalog-arn <value> \
    --state-template-properties <value> \
    [--description <value>] \
    [--data-extra-dimensions <value>] \
    [--metadata-extra-dimensions <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | State template name (1-100 chars) |
| `--signal-catalog-arn` | **Yes** | string | -- | ARN of the signal catalog |
| `--state-template-properties` | **Yes** | list | -- | Signal names to track (1-500) |
| `--description` | No | string | None | Description (1-2048 chars) |
| `--data-extra-dimensions` | No | list | None | Vehicle attributes for payload (0-5) |
| `--metadata-extra-dimensions` | No | list | None | Vehicle attributes for MQTT user properties (0-5) |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "id": "string"
}
```

---

### 7.2 `get-state-template`

Retrieves information about a state template.

**Synopsis:**
```bash
aws iotfleetwise get-state-template \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | State template name or ARN |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "id": "string",
    "description": "string",
    "signalCatalogArn": "string",
    "stateTemplateProperties": ["string"],
    "dataExtraDimensions": ["string"],
    "metadataExtraDimensions": ["string"],
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp"
}
```

---

### 7.3 `list-state-templates`

Lists state templates. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-state-templates \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "summaries": [
        {
            "name": "string",
            "arn": "string",
            "signalCatalogArn": "string",
            "description": "string",
            "id": "string",
            "creationTime": "timestamp",
            "lastModificationTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `update-state-template`

Updates a state template's properties or description.

**Synopsis:**
```bash
aws iotfleetwise update-state-template \
    --identifier <value> \
    [--description <value>] \
    [--state-template-properties-to-add <value>] \
    [--state-template-properties-to-remove <value>] \
    [--data-extra-dimensions <value>] \
    [--metadata-extra-dimensions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | State template name or ARN |
| `--description` | No | string | None | Updated description |
| `--state-template-properties-to-add` | No | list | None | Signal names to add (1-500) |
| `--state-template-properties-to-remove` | No | list | None | Signal names to remove (min 1) |
| `--data-extra-dimensions` | No | list | None | Updated data dimensions (0-5) |
| `--metadata-extra-dimensions` | No | list | None | Updated metadata dimensions (0-5) |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "id": "string"
}
```

---

### 7.5 `delete-state-template`

Deletes a state template.

**Synopsis:**
```bash
aws iotfleetwise delete-state-template \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | State template name or ARN |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "id": "string"
}
```
