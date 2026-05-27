# Controls

### 3.1 `create-control`

Creates a custom control in Audit Manager.

**Synopsis:**
```bash
aws auditmanager create-control \
    --name <value> \
    --control-mapping-sources <value> \
    [--description <value>] \
    [--testing-information <value>] \
    [--action-plan-title <value>] \
    [--action-plan-instructions <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Control name (1-300 chars) |
| `--control-mapping-sources` | **Yes** | list | -- | Data mapping sources (see structure below) |
| `--description` | No | string | None | Description (max 1000 chars) |
| `--testing-information` | No | string | None | Testing steps (max 1000 chars) |
| `--action-plan-title` | No | string | None | Action plan title (max 300 chars) |
| `--action-plan-instructions` | No | string | None | Remediation instructions (max 1000 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Control Mapping Sources Structure:**
```json
[
    {
        "sourceName": "string",
        "sourceDescription": "string",
        "sourceSetUpOption": "System_Controls_Mapping|Procedural_Controls_Mapping",
        "sourceType": "AWS_Cloudtrail|AWS_Config|AWS_Security_Hub|AWS_API_Call|MANUAL|Common_Control|Core_Control",
        "sourceKeyword": {
            "keywordInputType": "SELECT_FROM_LIST|UPLOAD_FILE|INPUT_TEXT",
            "keywordValue": "string"
        },
        "sourceFrequency": "DAILY|WEEKLY|MONTHLY",
        "troubleshootingText": "string"
    }
]
```

**Output Schema:**
```json
{
    "control": {
        "arn": "string",
        "id": "string",
        "type": "Standard|Custom|Core",
        "name": "string",
        "description": "string",
        "testingInformation": "string",
        "actionPlanTitle": "string",
        "actionPlanInstructions": "string",
        "controlSources": "string",
        "controlMappingSources": [
            {
                "sourceId": "string",
                "sourceName": "string",
                "sourceDescription": "string",
                "sourceSetUpOption": "string",
                "sourceType": "string",
                "sourceKeyword": {},
                "sourceFrequency": "string",
                "troubleshootingText": "string"
            }
        ],
        "createdAt": "timestamp",
        "lastUpdatedAt": "timestamp",
        "createdBy": "string",
        "lastUpdatedBy": "string",
        "tags": {},
        "state": "ACTIVE|END_OF_SUPPORT"
    }
}
```

---

### 3.2 `get-control`

Returns a control by ID.

**Synopsis:**
```bash
aws auditmanager get-control \
    --control-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-id` | **Yes** | string | -- | Control ID (UUID) |

**Output Schema:** Same as `create-control`.

---

### 3.3 `update-control`

Updates a custom control.

**Synopsis:**
```bash
aws auditmanager update-control \
    --control-id <value> \
    --name <value> \
    --control-mapping-sources <value> \
    [--description <value>] \
    [--testing-information <value>] \
    [--action-plan-title <value>] \
    [--action-plan-instructions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-id` | **Yes** | string | -- | Control ID to update |
| `--name` | **Yes** | string | -- | Updated name |
| `--control-mapping-sources` | **Yes** | list | -- | Updated mapping sources |
| `--description` | No | string | None | Updated description |
| `--testing-information` | No | string | None | Updated testing info |
| `--action-plan-title` | No | string | None | Updated action plan title |
| `--action-plan-instructions` | No | string | None | Updated instructions |

**Output Schema:** Same as `create-control`.

---

### 3.4 `delete-control`

Deletes a custom control.

**Synopsis:**
```bash
aws auditmanager delete-control \
    --control-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-id` | **Yes** | string | -- | Control ID to delete |

**Output Schema:** Empty on success.

---

### 3.5 `list-controls`

Returns a list of controls. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-controls \
    --control-type <value> \
    [--control-catalog-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-type` | **Yes** | string | -- | Type: `Standard`, `Custom`, `Core` |
| `--control-catalog-id` | No | string | None | Filter by catalog ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "controlMetadataList": [
        {
            "arn": "string",
            "id": "string",
            "name": "string",
            "controlSources": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.6 `get-services-in-scope`

Returns a list of AWS services that are in scope for Audit Manager evidence collection.

**Synopsis:**
```bash
aws auditmanager get-services-in-scope \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "serviceMetadata": [
        {
            "name": "string",
            "displayName": "string",
            "description": "string",
            "category": "string"
        }
    ]
}
```

---

### 3.7 `list-keywords-for-data-source`

Returns a list of keywords that can be used for a data source type. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-keywords-for-data-source \
    --source <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source` | **Yes** | string | -- | Source type: `AWS_Cloudtrail`, `AWS_Config`, `AWS_Security_Hub`, `AWS_API_Call` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "keywords": ["string"],
    "nextToken": "string"
}
```
