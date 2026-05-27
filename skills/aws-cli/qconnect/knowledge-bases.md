# Knowledge Bases

### 2.1 `create-knowledge-base`

Creates a knowledge base.

**Synopsis:**
```bash
aws qconnect create-knowledge-base \
    --name <value> \
    --knowledge-base-type <value> \
    [--source-configuration <value>] \
    [--rendering-configuration <value>] \
    [--vector-ingestion-configuration <value>] \
    [--server-side-encryption-configuration <value>] \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | KB name (1-255 chars) |
| `--knowledge-base-type` | **Yes** | string | -- | Type: `CUSTOM`, `EXTERNAL`, `QUICK_RESPONSES`, `MESSAGE_TEMPLATES`, `MANAGED` |
| `--source-configuration` | No | structure | None | External/managed data source config |
| `--rendering-configuration` | No | structure | None | Content rendering: `templateUri=string` |
| `--vector-ingestion-configuration` | No | structure | None | Chunking and parsing config |
| `--server-side-encryption-configuration` | No | structure | None | KMS config: `kmsKeyId=string` |
| `--description` | No | string | None | Description (1-255 chars) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Source Configuration (Managed Web Crawler):**
```json
{
    "managedSourceConfiguration": {
        "webCrawlerConfiguration": {
            "urlConfiguration": {"seedUrls": [{"url": "https://example.com"}]},
            "crawlerLimits": {"rateLimit": 300},
            "scope": "HOST_ONLY|SUBDOMAINS",
            "inclusionFilters": ["string"],
            "exclusionFilters": ["string"]
        }
    }
}
```

**Vector Ingestion Configuration:**
```json
{
    "chunkingConfiguration": {
        "chunkingStrategy": "FIXED_SIZE|NONE|HIERARCHICAL|SEMANTIC",
        "fixedSizeChunkingConfiguration": {"maxTokens": 300, "overlapPercentage": 20}
    },
    "parsingConfiguration": {
        "parsingStrategy": "BEDROCK_FOUNDATION_MODEL",
        "bedrockFoundationModelConfiguration": {"modelArn": "string"}
    }
}
```

**Output Schema:**
```json
{
    "knowledgeBase": {
        "knowledgeBaseId": "string",
        "knowledgeBaseArn": "string",
        "name": "string",
        "knowledgeBaseType": "string",
        "status": "CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE|DELETE_IN_PROGRESS|DELETE_FAILED|DELETED",
        "description": "string",
        "sourceConfiguration": {},
        "renderingConfiguration": {},
        "vectorIngestionConfiguration": {},
        "serverSideEncryptionConfiguration": {},
        "tags": {},
        "lastContentModificationTime": "timestamp",
        "ingestionStatus": "string",
        "ingestionFailureReasons": ["string"]
    }
}
```

---

### 2.2 `get-knowledge-base`

Gets a knowledge base.

**Synopsis:**
```bash
aws qconnect get-knowledge-base \
    --knowledge-base-id <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN |

**Output Schema:** Same as `create-knowledge-base`.

---

### 2.3 `list-knowledge-bases`

Lists knowledge bases. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-knowledge-bases \
    [--next-token <value>] \
    [--max-results <value>]
```

**Output Schema:**
```json
{
    "knowledgeBaseSummaries": [...],
    "nextToken": "string"
}
```

---

### 2.4 `delete-knowledge-base`

Deletes a knowledge base.

**Synopsis:**
```bash
aws qconnect delete-knowledge-base \
    --knowledge-base-id <value>
```

**Output:** None

---

### 2.5 `update-knowledge-base-template-uri`

Updates the template URI for a knowledge base.

**Synopsis:**
```bash
aws qconnect update-knowledge-base-template-uri \
    --knowledge-base-id <value> \
    --template-uri <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN |
| `--template-uri` | **Yes** | string | -- | Template URI (1-4096 chars) |

**Output Schema:** Returns knowledge base object.

---

### 2.6 `remove-knowledge-base-template-uri`

Removes the template URI from a knowledge base.

**Synopsis:**
```bash
aws qconnect remove-knowledge-base-template-uri \
    --knowledge-base-id <value>
```

**Output Schema:** Returns knowledge base object.
