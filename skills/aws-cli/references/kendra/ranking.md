# Ranking (Kendra Intelligent Ranking)

Commands in this group use `aws kendra-ranking` (not `aws kendra`).

### 9.1 `create-rescore-execution-plan`

Creates a rescore execution plan for Amazon Kendra Intelligent Ranking.

**Synopsis:**
```bash
aws kendra-ranking create-rescore-execution-plan \
    --name <value> \
    [--description <value>] \
    [--capacity-units <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Plan name (1-1000 chars) |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--capacity-units` | No | structure | None | Capacity: `{RescoreCapacityUnits: integer (0-1000)}` |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |

**Output Schema:**
```json
{
    "Id": "string (36 chars)",
    "Arn": "string"
}
```

---

### 9.2 `delete-rescore-execution-plan`

Deletes a rescore execution plan.

**Synopsis:**
```bash
aws kendra-ranking delete-rescore-execution-plan \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Rescore execution plan ID (36 chars) |

**Output:** None

---

### 9.3 `describe-rescore-execution-plan`

Gets details about a rescore execution plan.

**Synopsis:**
```bash
aws kendra-ranking describe-rescore-execution-plan \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Rescore execution plan ID (36 chars) |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string",
    "Name": "string",
    "Description": "string",
    "CapacityUnits": {
        "RescoreCapacityUnits": "integer"
    },
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
    "ErrorMessage": "string"
}
```

---

### 9.4 `list-rescore-execution-plans`

Lists all rescore execution plans. **Paginated operation.**

**Synopsis:**
```bash
aws kendra-ranking list-rescore-execution-plans \
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
    "SummaryItems": [
        {
            "Name": "string",
            "Id": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `update-rescore-execution-plan`

Updates a rescore execution plan.

**Synopsis:**
```bash
aws kendra-ranking update-rescore-execution-plan \
    --id <value> \
    [--name <value>] \
    [--description <value>] \
    [--capacity-units <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Rescore execution plan ID (36 chars) |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--capacity-units` | No | structure | None | New capacity |

**Output:** None

---

### 9.6 `rescore`

Re-ranks search results from an external search service using Kendra's semantic search.

**Synopsis:**
```bash
aws kendra-ranking rescore \
    --rescore-execution-plan-id <value> \
    --search-query <value> \
    --documents <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rescore-execution-plan-id` | **Yes** | string | -- | Plan ID (36 chars) |
| `--search-query` | **Yes** | string | -- | Search query text (1-1000 chars) |
| `--documents` | **Yes** | list | -- | Documents to re-rank (min 1) |

**Document Structure:**
```json
{
    "Id": "string (1-2048 chars)",
    "GroupId": "string (optional, 1-2048 chars)",
    "Title": "string (optional, 1-1024 chars)",
    "Body": "string (optional, 1-2048 chars)",
    "TokenizedTitle": ["string"],
    "TokenizedBody": ["string"],
    "OriginalScore": "float (-100000 to 100000)"
}
```

**Output Schema:**
```json
{
    "RescoreId": "string (1-36 chars)",
    "ResultItems": [
        {
            "DocumentId": "string",
            "Score": "float"
        }
    ]
}
```
