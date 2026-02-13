# Data Sources

### 2.1 `create-data-source`

Creates a data source connector to sync documents into a Kendra index.

**Synopsis:**
```bash
aws kendra create-data-source \
    --name <value> \
    --index-id <value> \
    --type <value> \
    [--configuration <value>] \
    [--vpc-configuration <value>] \
    [--description <value>] \
    [--schedule <value>] \
    [--role-arn <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--language-code <value>] \
    [--custom-document-enrichment-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Data source name (1-1000 chars) |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--type` | **Yes** | string | -- | Data source type (see supported types in index.md) |
| `--configuration` | No | structure | None | Connector-specific configuration. Required for all types except `CUSTOM` |
| `--vpc-configuration` | No | structure | None | VPC configuration for private data sources |
| `--description` | No | string | None | Description |
| `--schedule` | No | string | None | Cron expression for sync schedule |
| `--role-arn` | No | string | None | IAM role ARN with data source access |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-token` | No | string | None | Idempotency token |
| `--language-code` | No | string | None | Language code for the data source |
| `--custom-document-enrichment-configuration` | No | structure | None | Custom document enrichment config |

**Output Schema:**
```json
{
    "Id": "string"
}
```

---

### 2.2 `delete-data-source`

Deletes a data source connector. Documents already indexed are not removed.

**Synopsis:**
```bash
aws kendra delete-data-source \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Data source ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output:** None

---

### 2.3 `describe-data-source`

Gets information about a data source connector.

**Synopsis:**
```bash
aws kendra describe-data-source \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Data source ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output Schema:**
```json
{
    "Id": "string",
    "IndexId": "string",
    "Name": "string",
    "Type": "S3|SHAREPOINT|DATABASE|...",
    "Configuration": {},
    "VpcConfiguration": {},
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "Description": "string",
    "Status": "CREATING|DELETING|FAILED|UPDATING|ACTIVE",
    "Schedule": "string",
    "RoleArn": "string",
    "ErrorMessage": "string",
    "LanguageCode": "string",
    "CustomDocumentEnrichmentConfiguration": {}
}
```

---

### 2.4 `list-data-sources`

Lists data source connectors for an index. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-data-sources \
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
            "Type": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "Status": "string",
            "LanguageCode": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-data-source`

Updates the configuration of a data source connector.

**Synopsis:**
```bash
aws kendra update-data-source \
    --id <value> \
    --index-id <value> \
    [--name <value>] \
    [--configuration <value>] \
    [--vpc-configuration <value>] \
    [--description <value>] \
    [--schedule <value>] \
    [--role-arn <value>] \
    [--language-code <value>] \
    [--custom-document-enrichment-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Data source ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--name` | No | string | None | New name |
| `--configuration` | No | structure | None | New configuration |
| `--vpc-configuration` | No | structure | None | New VPC config |
| `--description` | No | string | None | New description |
| `--schedule` | No | string | None | New sync schedule |
| `--role-arn` | No | string | None | New IAM role |
| `--language-code` | No | string | None | New language code |
| `--custom-document-enrichment-configuration` | No | structure | None | New enrichment config |

**Output:** None

---

### 2.6 `start-data-source-sync-job`

Starts a synchronization job for a data source connector.

**Synopsis:**
```bash
aws kendra start-data-source-sync-job \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Data source ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output Schema:**
```json
{
    "ExecutionId": "string"
}
```

---

### 2.7 `stop-data-source-sync-job`

Stops a running synchronization job.

**Synopsis:**
```bash
aws kendra stop-data-source-sync-job \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Data source ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output:** None

---

### 2.8 `list-data-source-sync-jobs`

Lists sync job history for a data source. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-data-source-sync-jobs \
    --id <value> \
    --index-id <value> \
    [--status-filter <value>] \
    [--start-time-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Data source ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--status-filter` | No | string | None | Filter by status: `FAILED`, `SUCCEEDED`, `SYNCING`, `INCOMPLETE`, `STOPPING`, `ABORTED`, `SYNCING_INDEXING` |
| `--start-time-filter` | No | structure | None | Filter by time range |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "History": [
        {
            "ExecutionId": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "Status": "FAILED|SUCCEEDED|SYNCING|INCOMPLETE|STOPPING|ABORTED|SYNCING_INDEXING",
            "ErrorMessage": "string",
            "ErrorCode": "string",
            "DataSourceErrorCode": "string",
            "Metrics": {
                "DocumentsAdded": "string",
                "DocumentsModified": "string",
                "DocumentsDeleted": "string",
                "DocumentsFailed": "string",
                "DocumentsScanned": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 2.9 `batch-put-document`

Adds documents directly to a Kendra index (without a data source connector).

**Synopsis:**
```bash
aws kendra batch-put-document \
    --index-id <value> \
    --documents <value> \
    [--role-arn <value>] \
    [--custom-document-enrichment-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--documents` | **Yes** | list | -- | Documents to add (min 1, max 10) |
| `--role-arn` | No | string | None | IAM role for S3 access |
| `--custom-document-enrichment-configuration` | No | structure | None | Enrichment config |

**Output Schema:**
```json
{
    "FailedDocuments": [
        {
            "Id": "string",
            "ErrorCode": "InternalError|InvalidRequest",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.10 `batch-delete-document`

Removes documents from a Kendra index.

**Synopsis:**
```bash
aws kendra batch-delete-document \
    --index-id <value> \
    --document-id-list <value> \
    [--data-source-sync-job-metric-target <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--document-id-list` | **Yes** | list(string) | -- | Document IDs to delete (min 1, max 10) |
| `--data-source-sync-job-metric-target` | No | structure | None | Data source sync job to update metrics for |

**Output Schema:**
```json
{
    "FailedDocuments": [
        {
            "Id": "string",
            "ErrorCode": "InternalError|InvalidRequest",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.11 `batch-get-document-status`

Gets the ingestion status of a batch of documents.

**Synopsis:**
```bash
aws kendra batch-get-document-status \
    --index-id <value> \
    --document-info-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--document-info-list` | **Yes** | list | -- | Documents to check (min 1, max 10) |

**Output Schema:**
```json
{
    "Errors": [
        {
            "DocumentId": "string",
            "ErrorCode": "InternalError|InvalidRequest",
            "ErrorMessage": "string"
        }
    ],
    "DocumentStatusList": [
        {
            "DocumentId": "string",
            "DocumentStatus": "NOT_FOUND|PROCESSING|INDEXED|UPDATED|FAILED|UPDATE_FAILED"
        }
    ]
}
```

---

### 2.12 `query`

Searches the Kendra index using natural language. Returns ranked results with highlights.

**Synopsis:**
```bash
aws kendra query \
    --index-id <value> \
    [--query-text <value>] \
    [--attribute-filter <value>] \
    [--facets <value>] \
    [--requested-document-attributes <value>] \
    [--query-result-type-filter <value>] \
    [--document-relevance-override-configurations <value>] \
    [--page-number <value>] \
    [--page-size <value>] \
    [--sorting-configuration <value>] \
    [--sorting-configurations <value>] \
    [--user-context <value>] \
    [--visitor-id <value>] \
    [--spell-correction-configuration <value>] \
    [--collapse-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--query-text` | No | string | None | Natural language query (truncated at 30 tokens) |
| `--attribute-filter` | No | structure | None | Filter results by document attributes |
| `--facets` | No | list | None | Document attributes for faceted search |
| `--requested-document-attributes` | No | list | None | Attributes to include in response (1-100) |
| `--query-result-type-filter` | No | string | None | `DOCUMENT`, `QUESTION_ANSWER`, or `ANSWER` |
| `--document-relevance-override-configurations` | No | list | None | Override relevance tuning (0-500) |
| `--page-number` | No | integer | 1 | Page number |
| `--page-size` | No | integer | 10 | Results per page (max 100) |
| `--sorting-configuration` | No | structure | None | Single sort config |
| `--sorting-configurations` | No | list | None | Multiple sort configs (1-3) |
| `--user-context` | No | structure | None | User context for access control |
| `--visitor-id` | No | string | None | User identifier for analytics |
| `--spell-correction-configuration` | No | structure | None | Enable spell correction |
| `--collapse-configuration` | No | structure | None | Collapse results by attribute |

**Output Schema:**
```json
{
    "QueryId": "string",
    "ResultItems": [
        {
            "Id": "string",
            "Type": "DOCUMENT|QUESTION_ANSWER|ANSWER",
            "Format": "TABLE|TEXT",
            "DocumentId": "string",
            "DocumentTitle": {"Text": "string", "Highlights": []},
            "DocumentExcerpt": {"Text": "string", "Highlights": []},
            "DocumentURI": "string",
            "DocumentAttributes": [],
            "ScoreAttributes": {"ScoreConfidence": "VERY_HIGH|HIGH|MEDIUM|LOW|NOT_AVAILABLE"},
            "FeedbackToken": "string"
        }
    ],
    "FacetResults": [],
    "TotalNumberOfResults": "integer",
    "Warnings": [],
    "SpellCorrectedQueries": []
}
```

---

### 2.13 `retrieve`

Retrieves relevant passages from the index. Designed for RAG/LLM use cases, returning up to 200 token words per passage.

**Synopsis:**
```bash
aws kendra retrieve \
    --index-id <value> \
    --query-text <value> \
    [--attribute-filter <value>] \
    [--requested-document-attributes <value>] \
    [--document-relevance-override-configurations <value>] \
    [--page-number <value>] \
    [--page-size <value>] \
    [--user-context <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--query-text` | **Yes** | string | -- | Query text (truncated at 30 tokens) |
| `--attribute-filter` | No | structure | None | Filter results by attributes |
| `--requested-document-attributes` | No | list | None | Attributes to include (1-100) |
| `--document-relevance-override-configurations` | No | list | None | Relevance overrides |
| `--page-number` | No | integer | 1 | Page number |
| `--page-size` | No | integer | 10 | Results per page (max 100) |
| `--user-context` | No | structure | None | User context for access control |

**Output Schema:**
```json
{
    "QueryId": "string",
    "ResultItems": [
        {
            "Id": "string",
            "DocumentId": "string",
            "DocumentTitle": "string",
            "Content": "string",
            "DocumentURI": "string",
            "DocumentAttributes": [],
            "ScoreAttributes": {"ScoreConfidence": "VERY_HIGH|HIGH|MEDIUM|LOW|NOT_AVAILABLE"}
        }
    ]
}
```

---

### 2.14 `get-snapshots`

Gets search analytics snapshots for an index.

**Synopsis:**
```bash
aws kendra get-snapshots \
    --index-id <value> \
    --interval <value> \
    --metric-type <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--interval` | **Yes** | string | -- | Time interval: `THIS_MONTH`, `THIS_WEEK`, `ONE_WEEK_AGO`, `TWO_WEEKS_AGO`, `ONE_MONTH_AGO`, `TWO_MONTHS_AGO` |
| `--metric-type` | **Yes** | string | -- | Metric: `QUERIES_BY_COUNT`, `QUERIES_BY_ZERO_CLICK_RATE`, `QUERIES_BY_ZERO_RESULT_RATE`, `DOCS_BY_CLICK_COUNT`, `AGG_QUERY_DOC_METRICS`, `TREND_QUERY_DOC_METRICS` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SnapShotTimeFilter": {
        "StartTime": "timestamp",
        "EndTime": "timestamp"
    },
    "SnapshotsDataHeader": ["string"],
    "SnapshotsData": [["string"]],
    "NextToken": "string"
}
```

---

### 2.15 `submit-feedback`

Submits relevance feedback for a query result.

**Synopsis:**
```bash
aws kendra submit-feedback \
    --index-id <value> \
    --query-id <value> \
    [--click-feedback-items <value>] \
    [--relevance-feedback-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--query-id` | **Yes** | string | -- | Query ID from query response |
| `--click-feedback-items` | No | list | None | Click feedback items |
| `--relevance-feedback-items` | No | list | None | Relevance feedback: `RELEVANT` or `NOT_RELEVANT` |

**Output:** None
