# Experiences

### 8.1 `create-experience`

Creates a Kendra search experience for users to search and interact with documents.

**Synopsis:**
```bash
aws kendra create-experience \
    --name <value> \
    --index-id <value> \
    [--role-arn <value>] \
    [--configuration <value>] \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Experience name (1-1000 chars) |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--role-arn` | No | string | None | IAM role ARN for Query API and IAM Identity Center access |
| `--configuration` | No | structure | None | Content source and user identity config |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--client-token` | No | string | None | Idempotency token (1-100 chars) |

**Configuration Structure:**
```json
{
    "ContentSourceConfiguration": {
        "DataSourceIds": ["string"],
        "FaqIds": ["string"],
        "DirectPutContent": "boolean"
    },
    "UserIdentityConfiguration": {
        "IdentityAttributeName": "string"
    }
}
```

**Output Schema:**
```json
{
    "Id": "string (1-36 chars)"
}
```

---

### 8.2 `delete-experience`

Deletes a search experience.

**Synopsis:**
```bash
aws kendra delete-experience \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output:** None

---

### 8.3 `describe-experience`

Gets details about a search experience.

**Synopsis:**
```bash
aws kendra describe-experience \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output Schema:**
```json
{
    "Id": "string",
    "IndexId": "string",
    "Name": "string",
    "Endpoints": [
        {
            "EndpointType": "HOME",
            "Endpoint": "string"
        }
    ],
    "Configuration": {},
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "Description": "string",
    "Status": "CREATING|ACTIVE|DELETING|FAILED",
    "RoleArn": "string",
    "ErrorMessage": "string"
}
```

---

### 8.4 `list-experiences`

Lists search experiences for an index. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-experiences \
    --index-id <value> \
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
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SummaryItems": [
        {
            "Name": "string",
            "Id": "string",
            "CreatedAt": "timestamp",
            "Status": "CREATING|ACTIVE|DELETING|FAILED",
            "Endpoints": [{"EndpointType": "HOME", "Endpoint": "string"}]
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-experience`

Updates a search experience.

**Synopsis:**
```bash
aws kendra update-experience \
    --id <value> \
    --index-id <value> \
    [--name <value>] \
    [--role-arn <value>] \
    [--configuration <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--name` | No | string | None | New name |
| `--role-arn` | No | string | None | New IAM role ARN |
| `--configuration` | No | structure | None | New configuration |
| `--description` | No | string | None | New description |

**Output:** None

---

### 8.6 `associate-entities-to-experience`

Associates users or groups with a search experience.

**Synopsis:**
```bash
aws kendra associate-entities-to-experience \
    --id <value> \
    --index-id <value> \
    --entity-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--entity-list` | **Yes** | list | -- | Entities to associate: `[{EntityId: string, EntityType: USER\|GROUP}]` |

**Output Schema:**
```json
{
    "FailedEntityList": [
        {
            "EntityId": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 8.7 `disassociate-entities-from-experience`

Removes users or groups from a search experience.

**Synopsis:**
```bash
aws kendra disassociate-entities-from-experience \
    --id <value> \
    --index-id <value> \
    --entity-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--entity-list` | **Yes** | list | -- | Entities to remove |

**Output Schema:**
```json
{
    "FailedEntityList": [
        {
            "EntityId": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 8.8 `list-experience-entities`

Lists users and groups associated with a search experience. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-experience-entities \
    --id <value> \
    --index-id <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "SummaryItems": [
        {
            "EntityId": "string",
            "EntityType": "USER|GROUP",
            "DisplayData": {
                "UserName": "string",
                "GroupName": "string",
                "IdentifiedUserName": "string",
                "FirstName": "string",
                "LastName": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 8.9 `associate-personas-to-entities`

Assigns personas (roles) to users or groups within a search experience.

**Synopsis:**
```bash
aws kendra associate-personas-to-entities \
    --id <value> \
    --index-id <value> \
    --personas <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--personas` | **Yes** | list | -- | Personas: `[{EntityId: string, Persona: OWNER\|VIEWER}]` |

**Output Schema:**
```json
{
    "FailedEntityList": [
        {
            "EntityId": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 8.10 `disassociate-personas-from-entities`

Removes personas from users or groups in a search experience.

**Synopsis:**
```bash
aws kendra disassociate-personas-from-entities \
    --id <value> \
    --index-id <value> \
    --entity-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--entity-ids` | **Yes** | list(string) | -- | Entity IDs to remove personas from |

**Output Schema:**
```json
{
    "FailedEntityList": [
        {
            "EntityId": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 8.11 `list-entity-personas`

Lists personas assigned to an entity in a search experience. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-entity-personas \
    --id <value> \
    --index-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Experience ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "SummaryItems": [
        {
            "EntityId": "string",
            "Persona": "OWNER|VIEWER",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
