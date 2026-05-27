# Agent Runtime RAG

### `retrieve`

Retrieves relevant information from a knowledge base using semantic search.

**Synopsis:**
```bash
aws bedrock-agent-runtime retrieve \
    --knowledge-base-id <value> \
    --retrieval-query <value> \
    [--retrieval-configuration <value>] \
    [--guardrail-configuration <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |
| `--retrieval-query` | **Yes** | structure | -- | Query text. Structure: `text=string` |
| `--retrieval-configuration` | No | structure | None | Retrieval settings (vector search config) |
| `--guardrail-configuration` | No | structure | None | Guardrail to apply to results |

**Retrieval Configuration:**
```json
{
    "vectorSearchConfiguration": {
        "numberOfResults": 10,
        "overrideSearchType": "HYBRID|SEMANTIC",
        "filter": {
            "equals": {
                "key": "string",
                "value": "string|number|boolean"
            }
        },
        "rerankingConfiguration": {
            "type": "BEDROCK_RERANKING_MODEL",
            "bedrockRerankingConfiguration": {
                "modelConfiguration": {
                    "modelArn": "string"
                },
                "numberOfRerankedResults": 5
            }
        }
    }
}
```

**Filter Types:** `equals`, `notEquals`, `greaterThan`, `greaterThanOrEquals`, `lessThan`, `lessThanOrEquals`, `in`, `notIn`, `startsWith`, `listContains`, `stringContains`, `andAll`, `orAll`

**Output Schema:**
```json
{
    "retrievalResults": [
        {
            "content": {
                "type": "TEXT|IMAGE|ROW",
                "text": "string",
                "row": [
                    {
                        "columnName": "string",
                        "columnValue": "string",
                        "type": "STRING|BLOB|BOOLEAN|LONG|DOUBLE|NULL"
                    }
                ]
            },
            "location": {
                "type": "S3|WEB|CONFLUENCE|SALESFORCE|SHAREPOINT|CUSTOM|KENDRA|SQL",
                "s3Location": {"uri": "string"},
                "webLocation": {"url": "string"},
                "confluenceLocation": {"url": "string"},
                "salesforceLocation": {"url": "string"},
                "sharePointLocation": {"url": "string"},
                "customDocumentLocation": {"id": "string"},
                "kendraDocumentLocation": {"uri": "string"},
                "sqlLocation": {"query": "string"}
            },
            "score": "double",
            "metadata": {"string": "document"}
        }
    ],
    "nextToken": "string",
    "guardrailAction": "INTERVENED|NONE"
}
```

---

### `retrieve-and-generate`

Queries a knowledge base and generates a response using a foundation model. The response cites relevant sources.

**Synopsis:**
```bash
aws bedrock-agent-runtime retrieve-and-generate \
    --input <value> \
    [--retrieve-and-generate-configuration <value>] \
    [--session-configuration <value>] \
    [--session-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input` | **Yes** | structure | -- | Query input. Structure: `text=string` (0-1000 chars) |
| `--retrieve-and-generate-configuration` | No | structure | None | RAG configuration |
| `--session-configuration` | No | structure | None | Session config with KMS key |
| `--session-id` | No | string | None | Session ID for conversation continuity (2-100 chars) |

**Knowledge Base RAG Config:**
```json
{
    "type": "KNOWLEDGE_BASE",
    "knowledgeBaseConfiguration": {
        "knowledgeBaseId": "string",
        "modelArn": "arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-3-sonnet-20240229-v1:0",
        "generationConfiguration": {
            "promptTemplate": {
                "textPromptTemplate": "string"
            },
            "inferenceConfig": {
                "textInferenceConfig": {
                    "maxTokens": 1024,
                    "temperature": 0.7,
                    "topP": 0.9,
                    "stopSequences": []
                }
            },
            "guardrailConfiguration": {
                "guardrailId": "string",
                "guardrailVersion": "string"
            }
        },
        "retrievalConfiguration": {
            "vectorSearchConfiguration": {
                "numberOfResults": 10,
                "overrideSearchType": "HYBRID|SEMANTIC",
                "filter": {...}
            }
        },
        "orchestrationConfiguration": {
            "queryTransformationConfiguration": {
                "type": "QUERY_DECOMPOSITION"
            }
        }
    }
}
```

**External Sources RAG Config:**
```json
{
    "type": "EXTERNAL_SOURCES",
    "externalSourcesConfiguration": {
        "modelArn": "string",
        "sources": [
            {
                "sourceType": "S3",
                "s3Location": {
                    "uri": "s3://bucket/doc.pdf"
                }
            },
            {
                "sourceType": "BYTE_CONTENT",
                "byteContent": {
                    "contentType": "text/plain",
                    "data": "blob",
                    "identifier": "my-doc"
                }
            }
        ],
        "generationConfiguration": {...}
    }
}
```

**Output Schema:**
```json
{
    "sessionId": "string",
    "output": {
        "text": "string"
    },
    "citations": [
        {
            "generatedResponsePart": {
                "textResponsePart": {
                    "span": {
                        "start": "integer",
                        "end": "integer"
                    },
                    "text": "string"
                }
            },
            "retrievedReferences": [
                {
                    "content": {
                        "type": "TEXT|IMAGE|ROW|AUDIO|VIDEO",
                        "text": "string"
                    },
                    "location": {
                        "type": "S3|WEB|...",
                        "s3Location": {"uri": "string"}
                    },
                    "metadata": {"string": "document"}
                }
            ]
        }
    ],
    "guardrailAction": "INTERVENED|NONE"
}
```

---

### `rerank`

Reranks search results using a reranking model to improve relevance ordering.

**Synopsis:**
```bash
aws bedrock-agent-runtime rerank \
    --queries <value> \
    --sources <value> \
    --reranking-configuration <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queries` | **Yes** | list | -- | Queries to rerank against |
| `--sources` | **Yes** | list | -- | Source documents to rerank |
| `--reranking-configuration` | **Yes** | structure | -- | Reranking model config |

**Reranking Configuration:**
```json
{
    "type": "BEDROCK_RERANKING_MODEL",
    "bedrockRerankingConfiguration": {
        "modelConfiguration": {
            "modelArn": "arn:aws:bedrock:us-east-1::foundation-model/cohere.rerank-v3-5:0"
        },
        "numberOfResults": 10
    }
}
```

**Output Schema:**
```json
{
    "results": [
        {
            "index": "integer",
            "relevanceScore": "float"
        }
    ],
    "nextToken": "string"
}
```

---

### `generate-query`

Generates a query for a knowledge base, useful for transforming natural language into structured queries.

**Synopsis:**
```bash
aws bedrock-agent-runtime generate-query \
    --query-generation-input <value> \
    --transformation-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-generation-input` | **Yes** | structure | -- | Input for query generation |
| `--transformation-configuration` | **Yes** | structure | -- | Transformation config |

**Output Schema:**
```json
{
    "queries": [
        {
            "type": "REDSHIFT_SQL",
            "sql": "string"
        }
    ]
}
```
