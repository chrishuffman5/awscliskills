# Cases

Commands from the `aws connectcases` service.

### 30.1 `create-case`

Creates a case in the specified domain.

**Synopsis:**
```bash
aws connectcases create-case \
    --domain-id <value> \
    --template-id <value> \
    --fields <value> \
    [--client-token <value>] \
    [--performed-by <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID (1-500 chars) |
| `--template-id` | **Yes** | string | -- | Template ID (1-500 chars) |
| `--fields` | **Yes** | list | -- | Field values (0-220 items) |
| `--client-token` | No | string | Auto | Idempotency token (max 64) |
| `--performed-by` | No | tagged union | None | Entity performing the action |
| `--tags` | No | map | None | Tags (max 50) |

**Fields:**
```json
[
    {
        "id": "string",
        "value": { "stringValue": "string" | "doubleValue": 0.0 | "booleanValue": true | "emptyValue": {} | "userArnValue": "string" }
    }
]
```

**Output Schema:**
```json
{
    "caseId": "string",
    "caseArn": "string"
}
```

---

### 30.2 `get-case`

Gets case details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--case-id` | **Yes** | string | -- | Case ID |
| `--fields` | **Yes** | list | -- | Fields to retrieve |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "fields": [ { "id": "string", "value": {} } ],
    "tags": { "key": "value" },
    "nextToken": "string"
}
```

---

### 30.3 `search-cases`

Searches cases. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--filter` | No | structure | None | Filter conditions |
| `--sorts` | No | list | None | Sort criteria |
| `--fields` | No | list | None | Fields to return |
| `--search-term` | No | string | None | Free-text search term |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "cases": [ { "caseId": "string", "fields": [], "tags": {}, "templateId": "string" } ],
    "nextToken": "string",
    "totalCount": "integer"
}
```

---

### 30.4 `update-case`

Updates case fields.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--case-id` | **Yes** | string | -- | Case ID |
| `--fields` | **Yes** | list | -- | Updated field values |
| `--performed-by` | No | tagged union | None | Entity performing action |

**Output:** None

---

### 30.5 `delete-case`

Deletes a case.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--case-id` | **Yes** | string | -- | Case ID |

**Output:** None

---

### 30.6 `get-case-audit-events`

Gets case audit events (history). **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--case-id` | **Yes** | string | -- | Case ID |
| `--max-results` | No | integer | None | Max results (1-25) |
| `--next-token` | No | string | None | Pagination token |

---

### 30.7 `list-cases-for-contact`

Lists cases associated with a contact.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--contact-arn` | **Yes** | string | -- | Contact ARN |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--next-token` | No | string | None | Pagination token |

---

### 30.8-30.10 Related Items

`search-related-items`, `search-all-related-items`, `create-related-item`, `delete-related-item` manage items related to cases (comments, contacts).

**create-related-item output:**
```json
{
    "relatedItemArn": "string",
    "relatedItemId": "string"
}
```

---

### 30.11 `create-domain`

Creates a Cases domain.

**Synopsis:**
```bash
aws connectcases create-domain \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain name (1-100 chars) |

**Output Schema:**
```json
{
    "domainId": "string",
    "domainArn": "string",
    "domainStatus": "Active|CreationInProgress|CreationFailed"
}
```

---

### 30.12 `get-domain`

Gets domain details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |

**Output Schema:**
```json
{
    "domainId": "string",
    "domainArn": "string",
    "name": "string",
    "domainStatus": "Active|CreationInProgress|CreationFailed",
    "createdTime": "timestamp",
    "tags": { "key": "value" }
}
```

---

### 30.13 `list-domains`

Lists Cases domains. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-10) |
| `--next-token` | No | string | None | Pagination token |

---

### 30.14 `delete-domain`

Deletes a Cases domain.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |

**Output:** None

---

### 30.15-30.18 Template Commands

`create-template`, `get-template`, `list-templates`, `update-template`, `delete-template` manage case templates. All require `--domain-id`.

**create-template output:**
```json
{
    "templateId": "string",
    "templateArn": "string"
}
```

---

### 30.19-30.23 Field Commands

`create-field`, `batch-get-field`, `list-fields`, `update-field`, `delete-field`, `list-field-options`, `batch-put-field-options` manage case fields and their options. All require `--domain-id`.

**create-field output:**
```json
{
    "fieldId": "string",
    "fieldArn": "string"
}
```

---

### 30.24-30.27 Layout Commands

`create-layout`, `get-layout`, `list-layouts`, `update-layout`, `delete-layout` manage case layouts (UI configuration). All require `--domain-id`.

**create-layout output:**
```json
{
    "layoutId": "string",
    "layoutArn": "string"
}
```

---

### 30.28-30.31 Case Rule Commands

`create-case-rule`, `batch-get-case-rule`, `list-case-rules`, `update-case-rule`, `delete-case-rule` manage case automation rules. All require `--domain-id`.

---

### 30.32-30.33 Event Configuration Commands

`get-case-event-configuration`, `put-case-event-configuration` manage event configuration for a domain.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--event-bridge` | **Yes** (put) | structure | -- | EventBridge config with `enabled` and `includedData` |

**Output:** None (for put)
