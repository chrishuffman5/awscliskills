# Permissions

### 3.1 `list-permissions`

Lists the users and groups who have the Grafana `Admin` and `Editor` roles in the workspace. **Paginated operation.**

**Synopsis:**
```bash
aws grafana list-permissions \
    --workspace-id <value> \
    [--group-id <value>] \
    [--user-id <value>] \
    [--user-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--group-id` | No | string | None | Filter by group ID |
| `--user-id` | No | string | None | Filter by user ID |
| `--user-type` | No | string | None | Filter by user type: `SSO_USER`, `SSO_GROUP` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "permissions": [
        {
            "role": "ADMIN|EDITOR|VIEWER",
            "user": {
                "id": "string",
                "type": "SSO_USER|SSO_GROUP"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 3.2 `update-permissions`

Updates which users in a workspace have the Grafana `Admin` or `Editor` roles.

**Synopsis:**
```bash
aws grafana update-permissions \
    --workspace-id <value> \
    --update-instruction-batch <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--update-instruction-batch` | **Yes** | list | -- | List of permission update instructions |

**Update Instruction Structure:**
```json
[
    {
        "action": "ADD|REVOKE",
        "role": "ADMIN|EDITOR|VIEWER",
        "users": [
            {
                "id": "string",
                "type": "SSO_USER|SSO_GROUP"
            }
        ]
    }
]
```

**Output Schema:**
```json
{
    "errors": [
        {
            "message": "string",
            "causedBy": {
                "action": "ADD|REVOKE",
                "role": "ADMIN|EDITOR|VIEWER",
                "users": [
                    {
                        "id": "string",
                        "type": "SSO_USER|SSO_GROUP"
                    }
                ]
            }
        }
    ]
}
```
