# Assessments

### 1.1 `create-assessment`

Creates an assessment in Audit Manager.

**Synopsis:**
```bash
aws auditmanager create-assessment \
    --name <value> \
    --framework-id <value> \
    --assessment-reports-destination <value> \
    --scope <value> \
    --roles <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Assessment name (1-300 chars) |
| `--framework-id` | **Yes** | string | -- | Framework ID (UUID format) |
| `--assessment-reports-destination` | **Yes** | structure | -- | S3 destination. Shorthand: `destinationType=S3,destination=s3://bucket-name` |
| `--scope` | **Yes** | structure | -- | Scope with AWS accounts. Shorthand: `awsAccounts=[{id=123456789012}]` |
| `--roles` | **Yes** | list | -- | Roles. Shorthand: `roleType=PROCESS_OWNER,roleArn=arn:aws:iam::...` |
| `--description` | No | string | None | Description (max 1000 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "assessment": {
        "arn": "string",
        "awsAccount": {
            "id": "string",
            "emailAddress": "string",
            "name": "string"
        },
        "metadata": {
            "name": "string",
            "id": "string",
            "description": "string",
            "complianceType": "string",
            "status": "ACTIVE|INACTIVE",
            "assessmentReportsDestination": {
                "destinationType": "S3",
                "destination": "string"
            },
            "scope": {
                "awsAccounts": [{"id": "string", "emailAddress": "string", "name": "string"}],
                "awsServices": []
            },
            "roles": [{"roleType": "PROCESS_OWNER|RESOURCE_OWNER", "roleArn": "string"}],
            "delegations": [],
            "creationTime": "timestamp",
            "lastUpdated": "timestamp"
        },
        "framework": {
            "id": "string",
            "arn": "string",
            "metadata": {
                "name": "string",
                "description": "string",
                "complianceType": "string"
            },
            "controlSets": []
        },
        "tags": {"key": "value"}
    }
}
```

---

### 1.2 `get-assessment`

Returns an assessment by ID.

**Synopsis:**
```bash
aws auditmanager get-assessment \
    --assessment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID (UUID format) |

**Output Schema:**
```json
{
    "assessment": {
        "arn": "string",
        "awsAccount": {},
        "metadata": {
            "name": "string",
            "id": "string",
            "description": "string",
            "status": "ACTIVE|INACTIVE",
            "assessmentReportsDestination": {},
            "scope": {},
            "roles": [],
            "delegations": [],
            "creationTime": "timestamp",
            "lastUpdated": "timestamp"
        },
        "framework": {
            "id": "string",
            "arn": "string",
            "metadata": {},
            "controlSets": [
                {
                    "id": "string",
                    "description": "string",
                    "status": "ACTIVE|UNDER_REVIEW|REVIEWED",
                    "roles": [],
                    "controls": [
                        {
                            "id": "string",
                            "name": "string",
                            "description": "string",
                            "status": "UNDER_REVIEW|REVIEWED|INACTIVE",
                            "response": "MANUAL|AUTOMATE|DEFER|IGNORE",
                            "comments": [],
                            "evidenceSources": ["string"],
                            "evidenceCount": "integer",
                            "assessmentReportEvidenceCount": "integer"
                        }
                    ],
                    "delegations": [],
                    "systemEvidenceCount": "integer",
                    "manualEvidenceCount": "integer"
                }
            ]
        },
        "tags": {}
    },
    "userRole": {
        "roleType": "PROCESS_OWNER|RESOURCE_OWNER",
        "roleArn": "string"
    }
}
```

---

### 1.3 `update-assessment`

Updates an assessment.

**Synopsis:**
```bash
aws auditmanager update-assessment \
    --assessment-id <value> \
    --scope <value> \
    [--assessment-name <value>] \
    [--assessment-description <value>] \
    [--assessment-reports-destination <value>] \
    [--roles <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--scope` | **Yes** | structure | -- | Updated scope |
| `--assessment-name` | No | string | None | Updated name |
| `--assessment-description` | No | string | None | Updated description |
| `--assessment-reports-destination` | No | structure | None | Updated reports destination |
| `--roles` | No | list | None | Updated roles |

**Output Schema:** Same as `create-assessment`.

---

### 1.4 `delete-assessment`

Deletes an assessment.

**Synopsis:**
```bash
aws auditmanager delete-assessment \
    --assessment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID to delete |

**Output Schema:** Empty on success.

---

### 1.5 `list-assessments`

Returns a list of assessments. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-assessments \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | Filter by status: `ACTIVE`, `INACTIVE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "assessmentMetadata": [
        {
            "name": "string",
            "id": "string",
            "complianceType": "string",
            "status": "ACTIVE|INACTIVE",
            "roles": [],
            "delegations": [],
            "creationTime": "timestamp",
            "lastUpdated": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.6 `update-assessment-status`

Updates the status of an assessment (active or inactive).

**Synopsis:**
```bash
aws auditmanager update-assessment-status \
    --assessment-id <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--status` | **Yes** | string | -- | New status: `ACTIVE`, `INACTIVE` |

**Output Schema:** Same as `create-assessment`.

---

### 1.7 `update-assessment-control`

Updates a specific control within an assessment.

**Synopsis:**
```bash
aws auditmanager update-assessment-control \
    --assessment-id <value> \
    --control-set-id <value> \
    --control-id <value> \
    [--control-status <value>] \
    [--comment-body <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--control-set-id` | **Yes** | string | -- | Control set ID |
| `--control-id` | **Yes** | string | -- | Control ID |
| `--control-status` | No | string | None | Status: `UNDER_REVIEW`, `REVIEWED`, `INACTIVE` |
| `--comment-body` | No | string | None | Comment text (max 500 chars) |

**Output Schema:**
```json
{
    "control": {
        "id": "string",
        "name": "string",
        "description": "string",
        "status": "UNDER_REVIEW|REVIEWED|INACTIVE",
        "response": "MANUAL|AUTOMATE|DEFER|IGNORE",
        "comments": [
            {
                "authorName": "string",
                "commentBody": "string",
                "postedDate": "timestamp"
            }
        ],
        "evidenceSources": ["string"],
        "evidenceCount": "integer",
        "assessmentReportEvidenceCount": "integer"
    }
}
```

---

### 1.8 `update-assessment-control-set-status`

Updates the status of a control set in an assessment.

**Synopsis:**
```bash
aws auditmanager update-assessment-control-set-status \
    --assessment-id <value> \
    --control-set-id <value> \
    --status <value> \
    --comment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--control-set-id` | **Yes** | string | -- | Control set ID |
| `--status` | **Yes** | string | -- | Status: `ACTIVE`, `UNDER_REVIEW`, `REVIEWED` |
| `--comment` | **Yes** | string | -- | Comment explaining the status change |

**Output Schema:**
```json
{
    "controlSet": {
        "id": "string",
        "description": "string",
        "status": "ACTIVE|UNDER_REVIEW|REVIEWED",
        "roles": [],
        "controls": [],
        "delegations": [],
        "systemEvidenceCount": "integer",
        "manualEvidenceCount": "integer"
    }
}
```

---

### 1.9 `get-change-logs`

Returns a list of change logs for an assessment. **Paginated.**

**Synopsis:**
```bash
aws auditmanager get-change-logs \
    --assessment-id <value> \
    [--control-set-id <value>] \
    [--control-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--control-set-id` | No | string | None | Filter by control set |
| `--control-id` | No | string | None | Filter by control |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "changeLogs": [
        {
            "objectType": "ASSESSMENT|CONTROL_SET|CONTROL|DELEGATION|ASSESSMENT_REPORT",
            "objectName": "string",
            "action": "CREATE|UPDATE_METADATA|ACTIVE|INACTIVE|DELETE|UNDER_REVIEW|REVIEWED|IMPORT_EVIDENCE",
            "createdAt": "timestamp",
            "createdBy": "string"
        }
    ],
    "nextToken": "string"
}
```
