# Inputs

## 2.1 `create-input`

Creates an input that receives IoT data for detector models and alarm models.

**Synopsis:**
```bash
aws iotevents create-input \
    --input-name <value> \
    --input-definition <value> \
    [--input-description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-name` | **Yes** | string | -- | Input name (1-128 chars, pattern `^[a-zA-Z][a-zA-Z0-9_]*$`) |
| `--input-definition` | **Yes** | structure | -- | Input definition with attributes |
| `--input-description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | list | None | Tags |

**InputDefinition:**
```json
{
    "attributes": [
        {"jsonPath": "string"}
    ]
}
```
Attributes: 1-200 items. jsonPath: 1-128 chars.

**Output Schema:**
```json
{
    "inputConfiguration": {
        "inputName": "string",
        "inputDescription": "string",
        "inputArn": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "status": "CREATING|UPDATING|ACTIVE|DELETING"
    }
}
```

---

## 2.2 `describe-input`

Describes an input.

**Synopsis:**
```bash
aws iotevents describe-input \
    --input-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-name` | **Yes** | string | -- | Input name |

**Output Schema:**
```json
{
    "input": {
        "inputConfiguration": {
            "inputName": "string",
            "inputDescription": "string",
            "inputArn": "string",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp",
            "status": "CREATING|UPDATING|ACTIVE|DELETING"
        },
        "inputDefinition": {
            "attributes": [{"jsonPath": "string"}]
        }
    }
}
```

---

## 2.3 `list-inputs`

Lists inputs. **Paginated operation.**

**Synopsis:**
```bash
aws iotevents list-inputs \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "inputSummaries": [
        {
            "inputName": "string",
            "inputDescription": "string",
            "inputArn": "string",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp",
            "status": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 2.4 `update-input`

Updates an input definition.

**Synopsis:**
```bash
aws iotevents update-input \
    --input-name <value> \
    --input-definition <value> \
    [--input-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-name` | **Yes** | string | -- | Input name |
| `--input-definition` | **Yes** | structure | -- | Updated definition |
| `--input-description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "inputConfiguration": {
        "inputName": "string",
        "inputDescription": "string",
        "inputArn": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "status": "CREATING|UPDATING|ACTIVE|DELETING"
    }
}
```

---

## 2.5 `delete-input`

Deletes an input.

**Synopsis:**
```bash
aws iotevents delete-input \
    --input-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-name` | **Yes** | string | -- | Input name |

**Output:** None

---

## 2.6 `list-input-routings`

Lists detector models and alarm models that use the specified input.

**Synopsis:**
```bash
aws iotevents list-input-routings \
    --input-identifier <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-identifier` | **Yes** | structure | -- | `{iotEventsInputIdentifier: {inputName: "string"}}` or `{iotSiteWiseInputIdentifier: {iotSiteWiseAssetModelPropertyIdentifier: {assetModelId, propertyId}}}` |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "routedResources": [
        {
            "name": "string",
            "arn": "string"
        }
    ],
    "nextToken": "string"
}
```
