# Delegations

### 6.1 `get-delegations`

Returns a list of delegations assigned to the current user. **Paginated.**

**Synopsis:**
```bash
aws auditmanager get-delegations \
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
    "delegations": [
        {
            "id": "string",
            "assessmentName": "string",
            "assessmentId": "string",
            "status": "IN_PROGRESS|UNDER_REVIEW|COMPLETE",
            "roleArn": "string",
            "roleType": "PROCESS_OWNER|RESOURCE_OWNER",
            "creationTime": "timestamp",
            "lastUpdated": "timestamp",
            "controlSetId": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.2 `batch-create-delegation-by-assessment`

Creates delegations for a specified assessment.

**Synopsis:**
```bash
aws auditmanager batch-create-delegation-by-assessment \
    --create-delegation-requests <value> \
    --assessment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--create-delegation-requests` | **Yes** | list | -- | Delegation requests (see structure below) |
| `--assessment-id` | **Yes** | string | -- | Assessment ID |

**Delegation Request Structure:**
```json
[
    {
        "comment": "string",
        "controlSetId": "string",
        "roleArn": "string",
        "roleType": "PROCESS_OWNER|RESOURCE_OWNER"
    }
]
```

**Output Schema:**
```json
{
    "delegations": [
        {
            "id": "string",
            "assessmentName": "string",
            "assessmentId": "string",
            "status": "IN_PROGRESS|UNDER_REVIEW|COMPLETE",
            "roleArn": "string",
            "roleType": "PROCESS_OWNER|RESOURCE_OWNER",
            "creationTime": "timestamp",
            "lastUpdated": "timestamp",
            "controlSetId": "string",
            "comment": "string",
            "createdBy": "string"
        }
    ],
    "errors": [
        {
            "createDelegationRequest": {},
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 6.3 `batch-delete-delegation-by-assessment`

Deletes delegations from a specified assessment.

**Synopsis:**
```bash
aws auditmanager batch-delete-delegation-by-assessment \
    --delegation-ids <value> \
    --assessment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delegation-ids` | **Yes** | list(string) | -- | Delegation IDs to delete |
| `--assessment-id` | **Yes** | string | -- | Assessment ID |

**Output Schema:**
```json
{
    "errors": [
        {
            "delegationId": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```
