# Assessment Frameworks

### 2.1 `create-assessment-framework`

Creates a custom framework in Audit Manager.

**Synopsis:**
```bash
aws auditmanager create-assessment-framework \
    --name <value> \
    --control-sets <value> \
    [--description <value>] \
    [--compliance-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Framework name (1-300 chars) |
| `--control-sets` | **Yes** | list | -- | Control sets with controls. JSON: `[{"name":"SetName","controls":[{"id":"uuid"}]}]` |
| `--description` | No | string | None | Description (max 1000 chars) |
| `--compliance-type` | No | string | None | Compliance type (e.g., CIS, HIPAA, max 100 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "framework": {
        "arn": "string",
        "id": "string",
        "name": "string",
        "type": "Standard|Custom",
        "complianceType": "string",
        "description": "string",
        "controlSources": "string",
        "controlSets": [
            {
                "id": "string",
                "name": "string",
                "controls": [
                    {
                        "arn": "string",
                        "id": "string",
                        "type": "Standard|Custom|Core",
                        "name": "string",
                        "description": "string",
                        "controlMappingSources": [],
                        "createdAt": "timestamp",
                        "lastUpdatedAt": "timestamp",
                        "state": "ACTIVE|END_OF_SUPPORT"
                    }
                ]
            }
        ],
        "createdAt": "timestamp",
        "lastUpdatedAt": "timestamp",
        "createdBy": "string",
        "lastUpdatedBy": "string",
        "tags": {}
    }
}
```

---

### 2.2 `get-assessment-framework`

Returns a framework by ID.

**Synopsis:**
```bash
aws auditmanager get-assessment-framework \
    --framework-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-id` | **Yes** | string | -- | Framework ID (UUID) |

**Output Schema:** Same as `create-assessment-framework`.

---

### 2.3 `update-assessment-framework`

Updates a custom framework.

**Synopsis:**
```bash
aws auditmanager update-assessment-framework \
    --framework-id <value> \
    --name <value> \
    --control-sets <value> \
    [--description <value>] \
    [--compliance-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-id` | **Yes** | string | -- | Framework ID to update |
| `--name` | **Yes** | string | -- | Updated name |
| `--control-sets` | **Yes** | list | -- | Updated control sets |
| `--description` | No | string | None | Updated description |
| `--compliance-type` | No | string | None | Updated compliance type |

**Output Schema:** Same as `create-assessment-framework`.

---

### 2.4 `delete-assessment-framework`

Deletes a custom framework.

**Synopsis:**
```bash
aws auditmanager delete-assessment-framework \
    --framework-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-id` | **Yes** | string | -- | Framework ID to delete |

**Output Schema:** Empty on success.

---

### 2.5 `list-assessment-frameworks`

Returns a list of frameworks. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-assessment-frameworks \
    --framework-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-type` | **Yes** | string | -- | Framework type: `Standard`, `Custom` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "frameworkMetadataList": [
        {
            "arn": "string",
            "id": "string",
            "name": "string",
            "type": "Standard|Custom",
            "complianceType": "string",
            "description": "string",
            "logo": "string",
            "controlSetsCount": "integer",
            "controlsCount": "integer",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.6 `start-assessment-framework-share`

Shares a custom framework with another AWS account.

**Synopsis:**
```bash
aws auditmanager start-assessment-framework-share \
    --framework-id <value> \
    --destination-account <value> \
    --destination-region <value> \
    [--comment <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-id` | **Yes** | string | -- | Framework ID to share |
| `--destination-account` | **Yes** | string | -- | Destination account ID (12 digits) |
| `--destination-region` | **Yes** | string | -- | Destination AWS region |
| `--comment` | No | string | None | Comment for the share request (max 500 chars) |

**Output Schema:**
```json
{
    "assessmentFrameworkShareRequest": {
        "id": "string",
        "frameworkId": "string",
        "frameworkName": "string",
        "frameworkDescription": "string",
        "status": "ACTIVE|REPLICATING|SHARED|EXPIRING|FAILED|EXPIRED|DECLINED|REVOKED",
        "sourceAccount": "string",
        "destinationAccount": "string",
        "destinationRegion": "string",
        "expirationTime": "timestamp",
        "creationTime": "timestamp",
        "lastUpdated": "timestamp",
        "comment": "string",
        "standardControlsCount": "integer",
        "customControlsCount": "integer",
        "complianceType": "string"
    }
}
```

---

### 2.7 `update-assessment-framework-share`

Updates a framework share request (accept, decline, or revoke).

**Synopsis:**
```bash
aws auditmanager update-assessment-framework-share \
    --request-id <value> \
    --request-type <value> \
    --action <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--request-id` | **Yes** | string | -- | Share request ID (UUID) |
| `--request-type` | **Yes** | string | -- | Request type: `SENT`, `RECEIVED` |
| `--action` | **Yes** | string | -- | Action: `ACCEPT`, `DECLINE`, `REVOKE` |

**Output Schema:** Same structure as `start-assessment-framework-share`.

---

### 2.8 `delete-assessment-framework-share`

Deletes a framework share request.

**Synopsis:**
```bash
aws auditmanager delete-assessment-framework-share \
    --request-id <value> \
    --request-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--request-id` | **Yes** | string | -- | Share request ID |
| `--request-type` | **Yes** | string | -- | Request type: `SENT`, `RECEIVED` |

**Output Schema:** Empty on success.

---

### 2.9 `list-assessment-framework-share-requests`

Returns a list of framework share requests. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-assessment-framework-share-requests \
    --request-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--request-type` | **Yes** | string | -- | Request type: `SENT`, `RECEIVED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "assessmentFrameworkShareRequests": [
        {
            "id": "string",
            "frameworkId": "string",
            "frameworkName": "string",
            "status": "ACTIVE|REPLICATING|SHARED|EXPIRING|FAILED|EXPIRED|DECLINED|REVOKED",
            "sourceAccount": "string",
            "destinationAccount": "string",
            "destinationRegion": "string",
            "expirationTime": "timestamp",
            "creationTime": "timestamp",
            "lastUpdated": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
