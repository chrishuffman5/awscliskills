# Service-Linked Roles

### 16.1 `create-service-linked-role`

Creates a service-linked role for an AWS service.

**Synopsis:**
```bash
aws iam create-service-linked-role \
    --aws-service-name <value> \
    [--description <value>] \
    [--custom-suffix <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-service-name` | **Yes** | string | -- | Service principal (e.g., `ecs.amazonaws.com`) |
| `--description` | No | string | None | Description |
| `--custom-suffix` | No | string | None | Suffix appended to role name |

**Output Schema:**
```json
{
    "Role": {
        "Path": "string",
        "RoleName": "string",
        "RoleId": "string",
        "Arn": "string",
        "CreateDate": "timestamp",
        "AssumeRolePolicyDocument": "string",
        "Description": "string"
    }
}
```

---

### 16.2 `delete-service-linked-role`

Submits a deletion request for a service-linked role. Deletion is asynchronous.

**Synopsis:**
```bash
aws iam delete-service-linked-role --role-name <value>
```

**Output Schema:**
```json
{
    "DeletionTaskId": "string"
}
```

---

### 16.3 `get-service-linked-role-deletion-status`

Checks the status of a service-linked role deletion.

**Synopsis:**
```bash
aws iam get-service-linked-role-deletion-status --deletion-task-id <value>
```

**Output Schema:**
```json
{
    "Status": "SUCCEEDED|IN_PROGRESS|FAILED|NOT_STARTED",
    "Reason": {
        "Reason": "string",
        "RoleUsageList": [
            {
                "Region": "string",
                "Resources": ["string"]
            }
        ]
    }
}
```

---
