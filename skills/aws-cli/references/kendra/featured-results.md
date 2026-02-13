# Featured Results

### 6.1 `create-featured-results-set`

Creates a set of featured results that appear at the top of search results for specific queries.

**Synopsis:**
```bash
aws kendra create-featured-results-set \
    --index-id <value> \
    --featured-results-set-name <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--status <value>] \
    [--query-texts <value>] \
    [--featured-documents <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--featured-results-set-name` | **Yes** | string | -- | Name (1-1000 chars) |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--client-token` | No | string | None | Idempotency token |
| `--status` | No | string | None | `ACTIVE` or `INACTIVE` |
| `--query-texts` | No | list | None | Query texts to trigger (0-49 items) |
| `--featured-documents` | No | list | None | Documents to feature: `[{Id: string}]` |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "FeaturedResultsSet": {
        "FeaturedResultsSetId": "string",
        "FeaturedResultsSetName": "string",
        "Description": "string",
        "Status": "ACTIVE|INACTIVE",
        "QueryTexts": ["string"],
        "FeaturedDocuments": [{"Id": "string"}],
        "LastUpdatedTimestamp": "long",
        "CreationTimestamp": "long"
    }
}
```

---

### 6.2 `delete-featured-results-set`

Deletes a featured results set.

**Synopsis:**
```bash
aws kendra delete-featured-results-set \
    --index-id <value> \
    --featured-results-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--featured-results-set-id` | **Yes** | string | -- | Featured results set ID |

**Output:** None

---

### 6.3 `describe-featured-results-set`

Gets details about a featured results set.

**Synopsis:**
```bash
aws kendra describe-featured-results-set \
    --index-id <value> \
    --featured-results-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--featured-results-set-id` | **Yes** | string | -- | Featured results set ID |

**Output Schema:**
```json
{
    "FeaturedResultsSetId": "string",
    "FeaturedResultsSetName": "string",
    "Description": "string",
    "Status": "ACTIVE|INACTIVE",
    "QueryTexts": ["string"],
    "FeaturedDocumentsWithMetadata": [
        {
            "Id": "string",
            "Title": "string",
            "URI": "string"
        }
    ],
    "FeaturedDocumentsMissing": [{"Id": "string"}],
    "LastUpdatedTimestamp": "long",
    "CreationTimestamp": "long"
}
```

---

### 6.4 `list-featured-results-sets`

Lists featured results sets for an index. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-featured-results-sets \
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
    "FeaturedResultsSetSummaryItems": [
        {
            "FeaturedResultsSetId": "string",
            "FeaturedResultsSetName": "string",
            "Status": "ACTIVE|INACTIVE",
            "LastUpdatedTimestamp": "long",
            "CreationTimestamp": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `update-featured-results-set`

Updates a featured results set.

**Synopsis:**
```bash
aws kendra update-featured-results-set \
    --index-id <value> \
    --featured-results-set-id <value> \
    [--featured-results-set-name <value>] \
    [--description <value>] \
    [--status <value>] \
    [--query-texts <value>] \
    [--featured-documents <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--featured-results-set-id` | **Yes** | string | -- | Featured results set ID |
| `--featured-results-set-name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--status` | No | string | None | `ACTIVE` or `INACTIVE` |
| `--query-texts` | No | list | None | New query texts |
| `--featured-documents` | No | list | None | New featured documents |

**Output Schema:**
```json
{
    "FeaturedResultsSet": {
        "FeaturedResultsSetId": "string",
        "FeaturedResultsSetName": "string",
        "Description": "string",
        "Status": "ACTIVE|INACTIVE",
        "QueryTexts": ["string"],
        "FeaturedDocuments": [{"Id": "string"}],
        "LastUpdatedTimestamp": "long",
        "CreationTimestamp": "long"
    }
}
```
