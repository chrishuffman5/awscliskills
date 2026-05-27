# Knowledge Bases

### `create-knowledge-base`

Creates a knowledge base backed by a vector store, Amazon Kendra index, or SQL database.

**Synopsis:**
```bash
aws bedrock-agent create-knowledge-base \
    --name <value> \
    --role-arn <value> \
    --knowledge-base-configuration <value> \
    [--description <value>] \
    [--storage-configuration <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Knowledge base name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for Bedrock |
| `--knowledge-base-configuration` | **Yes** | structure | -- | KB type and embedding model config |
| `--description` | No | string | None | Description (1-200 chars) |
| `--storage-configuration` | No | structure | None | Vector store configuration |
| `--tags` | No | map | None | Key-value tags |
| `--client-token` | No | string | None | Idempotency token (33-256 chars) |

**Knowledge Base Configuration (Vector):**
```json
{
    "type": "VECTOR",
    "vectorKnowledgeBaseConfiguration": {
        "embeddingModelArn": "arn:aws:bedrock:us-east-1::foundation-model/amazon.titan-embed-text-v1",
        "embeddingModelConfiguration": {
            "bedrockEmbeddingModelConfiguration": {
                "dimensions": 1024,
                "embeddingDataType": "FLOAT32|BINARY"
            }
        }
    }
}
```

**Knowledge Base Configuration (Kendra):**
```json
{
    "type": "KENDRA",
    "kendraKnowledgeBaseConfiguration": {
        "kendraIndexArn": "arn:aws:kendra:us-east-1:123456789012:index/my-index"
    }
}
```

**Knowledge Base Configuration (SQL):**
```json
{
    "type": "SQL",
    "sqlKnowledgeBaseConfiguration": {
        "type": "REDSHIFT",
        "redshiftConfiguration": {
            "storageConfigurations": [...],
            "queryEngineConfiguration": {...},
            "queryGenerationConfiguration": {...}
        }
    }
}
```

**Storage Configuration (OpenSearch Serverless):**
```json
{
    "type": "OPENSEARCH_SERVERLESS",
    "opensearchServerlessConfiguration": {
        "collectionArn": "arn:aws:aoss:...",
        "vectorIndexName": "my-index",
        "fieldMapping": {
            "vectorField": "embedding",
            "textField": "text",
            "metadataField": "metadata"
        }
    }
}
```

**Supported Storage Types:** `OPENSEARCH_SERVERLESS`, `OPENSEARCH_MANAGED_CLUSTER`, `PINECONE`, `REDIS_ENTERPRISE_CLOUD`, `RDS`, `MONGO_DB_ATLAS`, `NEPTUNE_ANALYTICS`, `S3_VECTORS`

**Output Schema:**
```json
{
    "knowledgeBase": {
        "knowledgeBaseId": "string",
        "name": "string",
        "knowledgeBaseArn": "string",
        "description": "string",
        "roleArn": "string",
        "knowledgeBaseConfiguration": {...},
        "storageConfiguration": {...},
        "status": "CREATING|ACTIVE|DELETING|UPDATING|FAILED|DELETE_UNSUCCESSFUL",
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "failureReasons": ["string"]
    }
}
```

---

### `get-knowledge-base`

Gets details of a knowledge base.

**Synopsis:**
```bash
aws bedrock-agent get-knowledge-base \
    --knowledge-base-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |

**Output Schema:** Same as `create-knowledge-base` output.

---

### `list-knowledge-bases`

Lists knowledge bases. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-knowledge-bases \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "knowledgeBaseSummaries": [
        {
            "knowledgeBaseId": "string",
            "name": "string",
            "description": "string",
            "status": "CREATING|ACTIVE|DELETING|UPDATING|FAILED|DELETE_UNSUCCESSFUL",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-knowledge-base`

Updates a knowledge base configuration.

**Synopsis:**
```bash
aws bedrock-agent update-knowledge-base \
    --knowledge-base-id <value> \
    --name <value> \
    --role-arn <value> \
    --knowledge-base-configuration <value> \
    [--description <value>] \
    [--storage-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:** Same as `create-knowledge-base` output.

---

### `delete-knowledge-base`

Deletes a knowledge base.

**Synopsis:**
```bash
aws bedrock-agent delete-knowledge-base \
    --knowledge-base-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |

**Output Schema:**
```json
{
    "knowledgeBaseId": "string",
    "status": "DELETING"
}
```

---

### `create-data-source`

Creates a data source for a knowledge base, specifying where to ingest documents from.

**Synopsis:**
```bash
aws bedrock-agent create-data-source \
    --knowledge-base-id <value> \
    --name <value> \
    --data-source-configuration <value> \
    [--description <value>] \
    [--data-deletion-policy <value>] \
    [--server-side-encryption-configuration <value>] \
    [--vector-ingestion-configuration <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |
| `--name` | **Yes** | string | -- | Data source name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--data-source-configuration` | **Yes** | structure | -- | Source type and configuration |
| `--description` | No | string | None | Description (1-200 chars) |
| `--data-deletion-policy` | No | string | None | `RETAIN` or `DELETE` |
| `--server-side-encryption-configuration` | No | structure | None | KMS key for encryption |
| `--vector-ingestion-configuration` | No | structure | None | Chunking and parsing configuration |
| `--client-token` | No | string | None | Idempotency token |

**Data Source Configuration (S3):**
```json
{
    "type": "S3",
    "s3Configuration": {
        "bucketArn": "arn:aws:s3:::my-bucket",
        "inclusionPrefixes": ["docs/"],
        "bucketOwnerAccountId": "123456789012"
    }
}
```

**Supported Data Source Types:** `S3`, `WEB`, `CONFLUENCE`, `SALESFORCE`, `SHAREPOINT`, `CUSTOM`

**Output Schema:**
```json
{
    "dataSource": {
        "knowledgeBaseId": "string",
        "dataSourceId": "string",
        "name": "string",
        "status": "AVAILABLE|DELETING|DELETE_UNSUCCESSFUL",
        "description": "string",
        "dataSourceConfiguration": {...},
        "serverSideEncryptionConfiguration": {...},
        "vectorIngestionConfiguration": {...},
        "dataDeletionPolicy": "RETAIN|DELETE",
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "failureReasons": ["string"]
    }
}
```

---

### `get-data-source`

Gets details of a data source.

**Synopsis:**
```bash
aws bedrock-agent get-data-source \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:** Same as `create-data-source` output.

---

### `list-data-sources`

Lists data sources for a knowledge base. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-data-sources \
    --knowledge-base-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `update-data-source`

Updates a data source configuration.

**Synopsis:**
```bash
aws bedrock-agent update-data-source \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    --name <value> \
    --data-source-configuration <value> \
    [--description <value>] \
    [--data-deletion-policy <value>] \
    [--server-side-encryption-configuration <value>] \
    [--vector-ingestion-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `delete-data-source`

Deletes a data source from a knowledge base.

**Synopsis:**
```bash
aws bedrock-agent delete-data-source \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `start-ingestion-job`

Starts an ingestion job to sync data from a data source into a knowledge base.

**Synopsis:**
```bash
aws bedrock-agent start-ingestion-job \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |
| `--data-source-id` | **Yes** | string | -- | Data source ID |
| `--description` | No | string | None | Description (1-200 chars) |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "ingestionJob": {
        "knowledgeBaseId": "string",
        "dataSourceId": "string",
        "ingestionJobId": "string",
        "description": "string",
        "status": "STARTING|IN_PROGRESS|COMPLETE|FAILED|STOPPING|STOPPED",
        "statistics": {
            "numberOfDocumentsScanned": "long",
            "numberOfNewDocumentsIndexed": "long",
            "numberOfModifiedDocumentsIndexed": "long",
            "numberOfDocumentsDeleted": "long",
            "numberOfDocumentsFailed": "long"
        },
        "failureReasons": ["string"],
        "startedAt": "timestamp",
        "updatedAt": "timestamp"
    }
}
```

---

### `get-ingestion-job`

Gets details of an ingestion job.

**Synopsis:**
```bash
aws bedrock-agent get-ingestion-job \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    --ingestion-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `list-ingestion-jobs`

Lists ingestion jobs for a data source. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-ingestion-jobs \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    [--filters <value>] \
    [--sort-by <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `stop-ingestion-job`

Stops a running ingestion job.

**Synopsis:**
```bash
aws bedrock-agent stop-ingestion-job \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    --ingestion-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `ingest-knowledge-base-documents`

Ingests specific documents into a knowledge base (inline ingestion, not via data source sync).

**Synopsis:**
```bash
aws bedrock-agent ingest-knowledge-base-documents \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    --documents <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |
| `--data-source-id` | **Yes** | string | -- | Data source ID |
| `--documents` | **Yes** | list | -- | Documents to ingest |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "documentDetails": [
        {
            "knowledgeBaseId": "string",
            "dataSourceId": "string",
            "status": "INDEXED|PARTIALLY_INDEXED|PENDING|FAILED|METADATA_PARTIALLY_INDEXED|METADATA_UPDATE_FAILED|IGNORED|NOT_FOUND|STARTING|IN_PROGRESS|DELETING|DELETE_IN_PROGRESS",
            "identifier": {...},
            "statusDescription": "string",
            "updatedAt": "timestamp"
        }
    ]
}
```

---

### `get-knowledge-base-documents`

Gets details of specific documents in a knowledge base.

**Synopsis:**
```bash
aws bedrock-agent get-knowledge-base-documents \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    --document-identifiers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `list-knowledge-base-documents`

Lists documents in a knowledge base. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-knowledge-base-documents \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `delete-knowledge-base-documents`

Deletes specific documents from a knowledge base.

**Synopsis:**
```bash
aws bedrock-agent delete-knowledge-base-documents \
    --knowledge-base-id <value> \
    --data-source-id <value> \
    --document-identifiers <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```
