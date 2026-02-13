# Access Control

### 7.1 `create-access-control-configuration`

Creates an access control configuration for documents in an index. Defines which users and groups can access specific documents.

**Synopsis:**
```bash
aws kendra create-access-control-configuration \
    --index-id <value> \
    --name <value> \
    [--description <value>] \
    [--access-control-list <value>] \
    [--hierarchical-access-control-list <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--name` | **Yes** | string | -- | Configuration name (1-200 chars) |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--access-control-list` | No | list | None | Access control entries |
| `--hierarchical-access-control-list` | No | list | None | Hierarchical access control entries |
| `--client-token` | No | string | None | Idempotency token (1-100 chars) |

**Access Control List Entry:**
```json
{
    "Name": "string (1-200 chars)",
    "Type": "USER|GROUP",
    "Access": "ALLOW|DENY",
    "DataSourceId": "string (optional, 1-100 chars)"
}
```

**Output Schema:**
```json
{
    "Id": "string (1-36 chars)"
}
```

---

### 7.2 `delete-access-control-configuration`

Deletes an access control configuration.

**Synopsis:**
```bash
aws kendra delete-access-control-configuration \
    --index-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--id` | **Yes** | string | -- | Access control config ID |

**Output:** None

---

### 7.3 `describe-access-control-configuration`

Gets details about an access control configuration.

**Synopsis:**
```bash
aws kendra describe-access-control-configuration \
    --index-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--id` | **Yes** | string | -- | Access control config ID |

**Output Schema:**
```json
{
    "Name": "string",
    "Description": "string",
    "ErrorMessage": "string",
    "AccessControlList": [
        {
            "Name": "string",
            "Type": "USER|GROUP",
            "Access": "ALLOW|DENY",
            "DataSourceId": "string"
        }
    ],
    "HierarchicalAccessControlList": [
        {
            "PrincipalList": [
                {
                    "Name": "string",
                    "Type": "USER|GROUP",
                    "Access": "ALLOW|DENY",
                    "DataSourceId": "string"
                }
            ]
        }
    ]
}
```

---

### 7.4 `list-access-control-configurations`

Lists access control configurations for an index. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-access-control-configurations \
    --index-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccessControlConfigurations": [
        {
            "Id": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `update-access-control-configuration`

Updates an access control configuration.

**Synopsis:**
```bash
aws kendra update-access-control-configuration \
    --index-id <value> \
    --id <value> \
    [--name <value>] \
    [--description <value>] \
    [--access-control-list <value>] \
    [--hierarchical-access-control-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--id` | **Yes** | string | -- | Access control config ID |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--access-control-list` | No | list | None | New access control entries |
| `--hierarchical-access-control-list` | No | list | None | New hierarchical entries |

**Output:** None

---

### 7.6 `put-principal-mapping`

Maps users to groups for access control. Kendra uses group membership to filter search results.

**Synopsis:**
```bash
aws kendra put-principal-mapping \
    --index-id <value> \
    --group-id <value> \
    --group-members <value> \
    [--data-source-id <value>] \
    [--ordering-id <value>] \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--group-id` | **Yes** | string | -- | Group identifier (1-1024 chars) |
| `--group-members` | **Yes** | structure | -- | Group members list |
| `--data-source-id` | No | string | None | Data source ID to scope mapping |
| `--ordering-id` | No | long | None | Ordering ID for conflict resolution |
| `--role-arn` | No | string | None | IAM role ARN |

**Output:** None

---

### 7.7 `delete-principal-mapping`

Deletes a group mapping.

**Synopsis:**
```bash
aws kendra delete-principal-mapping \
    --index-id <value> \
    --group-id <value> \
    [--data-source-id <value>] \
    [--ordering-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--group-id` | **Yes** | string | -- | Group identifier |
| `--data-source-id` | No | string | None | Data source ID |
| `--ordering-id` | No | long | None | Ordering ID |

**Output:** None

---

### 7.8 `describe-principal-mapping`

Gets the status of a group mapping.

**Synopsis:**
```bash
aws kendra describe-principal-mapping \
    --index-id <value> \
    --group-id <value> \
    [--data-source-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--group-id` | **Yes** | string | -- | Group identifier |
| `--data-source-id` | No | string | None | Data source ID |

**Output Schema:**
```json
{
    "IndexId": "string",
    "DataSourceId": "string",
    "GroupId": "string",
    "GroupOrderingIdSummaries": [
        {
            "Status": "FAILED|SUCCEEDED|PROCESSING|DELETING|DELETED",
            "LastUpdatedAt": "timestamp",
            "ReceivedAt": "timestamp",
            "OrderingId": "long",
            "FailureReason": "string"
        }
    ]
}
```

---

### 7.9 `list-groups-older-than-ordering-id`

Lists groups with outdated mappings that were received before a given ordering ID. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-groups-older-than-ordering-id \
    --index-id <value> \
    --ordering-id <value> \
    [--data-source-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--ordering-id` | **Yes** | long | -- | Ordering ID threshold |
| `--data-source-id` | No | string | None | Data source ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GroupsSummaries": [
        {
            "GroupId": "string",
            "OrderingId": "long"
        }
    ],
    "NextToken": "string"
}
```
