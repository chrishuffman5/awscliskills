# Definitions

### 2.1 `put-pipeline-definition`

Adds tasks, schedules, and preconditions to the specified pipeline. You can use this to populate a new pipeline or update an existing one. The definition is also validated as it is uploaded.

**Synopsis:**
```bash
aws datapipeline put-pipeline-definition \
    --pipeline-id <value> \
    --pipeline-definition <value> \
    [--parameter-objects <value>] \
    [--parameter-values <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID to update |
| `--pipeline-definition` | **Yes** | string | -- | Pipeline definition JSON (inline or `file://path`) |
| `--parameter-objects` | No | list | None | Parameter objects used in the definition. Shorthand: `id=string,attributes=[{key=string,stringValue=string},...] ...` |
| `--parameter-values` | No | list | None | Parameter values. Shorthand: `id=string,stringValue=string ...` |

**Pipeline Definition Structure (file format):**
```json
{
    "objects": [
        {
            "id": "string",
            "name": "string",
            "fields": [
                {
                    "key": "string",
                    "stringValue": "string",
                    "refValue": "string"
                }
            ]
        }
    ]
}
```

**Output Schema:**
```json
{
    "validationErrors": [
        {
            "id": "string",
            "errors": ["string"]
        }
    ],
    "validationWarnings": [
        {
            "id": "string",
            "warnings": ["string"]
        }
    ],
    "errored": true|false
}
```

---

### 2.2 `get-pipeline-definition`

Retrieves the pipeline definition that was previously uploaded using `put-pipeline-definition`.

**Synopsis:**
```bash
aws datapipeline get-pipeline-definition \
    --pipeline-id <value> \
    [--version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--version` | No | string | `latest` | Version of the definition: `latest` or `active` |

**Output Schema:**
```json
{
    "pipelineObjects": [
        {
            "id": "string",
            "name": "string",
            "fields": [
                {
                    "key": "string",
                    "stringValue": "string",
                    "refValue": "string"
                }
            ]
        }
    ],
    "parameterObjects": [
        {
            "id": "string",
            "attributes": [
                {
                    "key": "string",
                    "stringValue": "string"
                }
            ]
        }
    ],
    "parameterValues": [
        {
            "id": "string",
            "stringValue": "string"
        }
    ]
}
```

---

### 2.3 `validate-pipeline-definition`

Validates the specified pipeline definition to check for errors without saving or activating the pipeline.

**Synopsis:**
```bash
aws datapipeline validate-pipeline-definition \
    --pipeline-id <value> \
    --pipeline-definition <value> \
    [--parameter-objects <value>] \
    [--parameter-values <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--pipeline-definition` | **Yes** | string | -- | Pipeline definition JSON (inline or `file://path`) |
| `--parameter-objects` | No | list | None | Parameter objects |
| `--parameter-values` | No | list | None | Parameter values |

**Output Schema:**
```json
{
    "validationErrors": [
        {
            "id": "string",
            "errors": ["string"]
        }
    ],
    "validationWarnings": [
        {
            "id": "string",
            "warnings": ["string"]
        }
    ],
    "errored": true|false
}
```
