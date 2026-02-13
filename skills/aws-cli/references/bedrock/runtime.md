# Runtime

### `invoke-model`

Invokes a foundation model to run inference using the provided input. The response body is written to the specified output file.

**Synopsis:**
```bash
aws bedrock-runtime invoke-model \
    --model-id <value> \
    [--body <value>] \
    [--content-type <value>] \
    [--accept <value>] \
    [--trace <value>] \
    [--guardrail-identifier <value>] \
    [--guardrail-version <value>] \
    [--performance-config-latency <value>] \
    [--service-tier <value>] \
    <outfile> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | Model ID, ARN, inference profile ID, or provisioned throughput ARN (1-2048 chars) |
| `outfile` | **Yes** | string | -- | Output filename for the response body |
| `--body` | No | blob | None | Prompt and inference parameters as JSON (max 25 MB) |
| `--content-type` | No | string | `application/json` | Input MIME type |
| `--accept` | No | string | `application/json` | Desired output MIME type |
| `--trace` | No | string | None | `ENABLED`, `DISABLED`, or `ENABLED_FULL` |
| `--guardrail-identifier` | No | string | None | Guardrail ID or ARN |
| `--guardrail-version` | No | string | None | Guardrail version or `DRAFT` |
| `--performance-config-latency` | No | string | None | `standard` or `optimized` |
| `--service-tier` | No | string | None | `priority`, `default`, `flex`, `reserved` |

**Example (Claude):**
```bash
aws bedrock-runtime invoke-model \
  --model-id anthropic.claude-3-sonnet-20240229-v1:0 \
  --content-type application/json \
  --body '{"anthropic_version":"bedrock-2023-05-31","max_tokens":1024,"messages":[{"role":"user","content":"Hello, Claude!"}]}' \
  response.json
```

**Example (Titan):**
```bash
aws bedrock-runtime invoke-model \
  --model-id amazon.titan-text-express-v1 \
  --content-type application/json \
  --body '{"inputText":"What is AI?","textGenerationConfig":{"maxTokenCount":512,"temperature":0.7}}' \
  response.json
```

**Output Schema:**
```json
{
    "body": "blob",
    "contentType": "string",
    "performanceConfigLatency": "standard|optimized",
    "serviceTier": "priority|default|flex|reserved"
}
```

---

### `converse`

Sends messages to a model using a consistent API format across all supported models. Supports multi-turn conversations, tool use, images, documents, video, audio, guardrails, and structured output.

**Synopsis:**
```bash
aws bedrock-runtime converse \
    --model-id <value> \
    [--messages <value>] \
    [--system <value>] \
    [--inference-config <value>] \
    [--tool-config <value>] \
    [--guardrail-config <value>] \
    [--additional-model-request-fields <value>] \
    [--prompt-variables <value>] \
    [--additional-model-response-field-paths <value>] \
    [--request-metadata <value>] \
    [--performance-config <value>] \
    [--service-tier <value>] \
    [--output-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | Model ID, ARN, inference profile, or prompt ARN (1-2048 chars) |
| `--messages` | No | list | None | Conversation messages (role + content) |
| `--system` | No | list | None | System prompt blocks |
| `--inference-config` | No | structure | None | `maxTokens`, `temperature`, `topP`, `stopSequences` |
| `--tool-config` | No | structure | None | Tool definitions and tool choice |
| `--guardrail-config` | No | structure | None | Guardrail ID, version, and trace settings |
| `--additional-model-request-fields` | No | document | None | Model-specific parameters |
| `--prompt-variables` | No | map | None | Variables for prompt management |
| `--additional-model-response-field-paths` | No | list | None | JSON Pointer paths for extra response fields (max 10) |
| `--request-metadata` | No | map | None | Key-value metadata for logging (1-16 entries) |
| `--performance-config` | No | structure | None | Latency setting: `standard` or `optimized` |
| `--service-tier` | No | structure | None | Processing tier: `priority`, `default`, `flex`, `reserved` |
| `--output-config` | No | structure | None | Structured output with JSON schema |

**Messages Structure:**
```json
[
    {
        "role": "user",
        "content": [
            {"text": "What is Amazon Bedrock?"}
        ]
    }
]
```

**Multi-modal Message (with image):**
```json
[
    {
        "role": "user",
        "content": [
            {"text": "Describe this image:"},
            {
                "image": {
                    "format": "png",
                    "source": {
                        "bytes": "base64-encoded-data"
                    }
                }
            }
        ]
    }
]
```

**Tool Config Structure:**
```json
{
    "tools": [
        {
            "toolSpec": {
                "name": "get_weather",
                "description": "Get current weather for a location",
                "inputSchema": {
                    "json": {
                        "type": "object",
                        "properties": {
                            "location": {"type": "string", "description": "City name"}
                        },
                        "required": ["location"]
                    }
                }
            }
        }
    ],
    "toolChoice": {"auto": {}}
}
```

**Inference Config:**
```json
{
    "maxTokens": 1024,
    "temperature": 0.7,
    "topP": 0.9,
    "stopSequences": ["\n\nHuman:"]
}
```

**Output Schema:**
```json
{
    "output": {
        "message": {
            "role": "assistant",
            "content": [
                {"text": "string"},
                {
                    "toolUse": {
                        "toolUseId": "string",
                        "name": "string",
                        "input": {}
                    }
                },
                {
                    "reasoningContent": {
                        "reasoningText": {
                            "text": "string",
                            "signature": "string"
                        }
                    }
                }
            ]
        }
    },
    "stopReason": "end_turn|tool_use|max_tokens|stop_sequence|guardrail_intervened|content_filtered",
    "usage": {
        "inputTokens": "integer",
        "outputTokens": "integer"
    },
    "metrics": {
        "latencyMs": "long"
    },
    "additionalModelResponseFields": {},
    "trace": {...},
    "performanceConfig": {
        "latency": "standard|optimized"
    }
}
```

---

### `apply-guardrail`

Applies a guardrail to content independent of a model invocation. Useful for evaluating content against guardrail policies.

**Synopsis:**
```bash
aws bedrock-runtime apply-guardrail \
    --guardrail-identifier <value> \
    --guardrail-version <value> \
    --source <value> \
    --content <value> \
    [--output-scope <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--guardrail-identifier` | **Yes** | string | -- | Guardrail ID or ARN |
| `--guardrail-version` | **Yes** | string | -- | Version number or `DRAFT` |
| `--source` | **Yes** | string | -- | Content source: `INPUT` or `OUTPUT` |
| `--content` | **Yes** | list | -- | Content to evaluate (text or image) |
| `--output-scope` | No | string | `INTERVENTIONS` | `INTERVENTIONS` or `FULL` (includes non-detected entries) |

**Content Structure (text):**
```json
[
    {
        "text": {
            "text": "Content to evaluate",
            "qualifiers": ["grounding_source", "query", "guard_content"]
        }
    }
]
```

**Output Schema:**
```json
{
    "usage": {
        "topicPolicyUnits": "integer",
        "contentPolicyUnits": "integer",
        "wordPolicyUnits": "integer",
        "sensitiveInformationPolicyUnits": "integer",
        "sensitiveInformationPolicyFreeUnits": "integer",
        "contextualGroundingPolicyUnits": "integer",
        "automatedReasoningPolicyUnits": "integer"
    },
    "action": "NONE|GUARDRAIL_INTERVENED",
    "actionReason": "string",
    "outputs": [{"text": "string"}],
    "assessments": [
        {
            "topicPolicy": {
                "topics": [
                    {
                        "name": "string",
                        "type": "DENY",
                        "action": "BLOCKED|NONE",
                        "detected": true|false
                    }
                ]
            },
            "contentPolicy": {
                "filters": [
                    {
                        "type": "INSULTS|HATE|SEXUAL|VIOLENCE|MISCONDUCT|PROMPT_ATTACK",
                        "confidence": "NONE|LOW|MEDIUM|HIGH",
                        "filterStrength": "NONE|LOW|MEDIUM|HIGH",
                        "action": "BLOCKED|NONE",
                        "detected": true|false
                    }
                ]
            },
            "wordPolicy": {
                "customWords": [{"match": "string", "action": "BLOCKED|NONE"}],
                "managedWordLists": [{"match": "string", "type": "PROFANITY", "action": "BLOCKED|NONE"}]
            },
            "sensitiveInformationPolicy": {
                "piiEntities": [{"match": "string", "type": "string", "action": "ANONYMIZED|BLOCKED|NONE"}],
                "regexes": [{"name": "string", "match": "string", "action": "ANONYMIZED|BLOCKED|NONE"}]
            },
            "contextualGroundingPolicy": {
                "filters": [
                    {
                        "type": "GROUNDING|RELEVANCE",
                        "threshold": "double",
                        "score": "double",
                        "action": "BLOCKED|NONE"
                    }
                ]
            }
        }
    ],
    "guardrailCoverage": {
        "textCharacters": {"guarded": "integer", "total": "integer"},
        "images": {"guarded": "integer", "total": "integer"}
    }
}
```

---

### `count-tokens`

Counts the number of tokens in a prompt for a specified model.

**Synopsis:**
```bash
aws bedrock-runtime count-tokens \
    --model-id <value> \
    --messages <value> \
    [--system <value>] \
    [--tool-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | Model ID |
| `--messages` | **Yes** | list | -- | Messages to count tokens for (same structure as converse) |
| `--system` | No | list | None | System prompt blocks |
| `--tool-config` | No | structure | None | Tool configuration |

**Output Schema:**
```json
{
    "totalTokens": "integer"
}
```

---

### `start-async-invoke`

Starts an asynchronous model invocation.

**Synopsis:**
```bash
aws bedrock-runtime start-async-invoke \
    --model-id <value> \
    --output-data-config <value> \
    [--model-input <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-id` | **Yes** | string | -- | Model ID or ARN |
| `--output-data-config` | **Yes** | structure | -- | S3 output location |
| `--model-input` | No | document | None | Model input payload |
| `--client-request-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "invocationArn": "string"
}
```

---

### `get-async-invoke`

Gets details of an asynchronous model invocation.

**Synopsis:**
```bash
aws bedrock-runtime get-async-invoke \
    --invocation-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--invocation-arn` | **Yes** | string | -- | Invocation ARN |

**Output Schema:**
```json
{
    "invocationArn": "string",
    "modelArn": "string",
    "clientRequestToken": "string",
    "status": "InProgress|Completed|Failed",
    "failureMessage": "string",
    "submitTime": "timestamp",
    "lastModifiedTime": "timestamp",
    "endTime": "timestamp",
    "outputDataConfig": {
        "s3OutputDataConfig": {
            "s3Uri": "string",
            "bucketOwner": "string"
        }
    }
}
```

---

### `list-async-invokes`

Lists asynchronous model invocations. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-runtime list-async-invokes \
    [--submit-time-after <value>] \
    [--submit-time-before <value>] \
    [--status-equals <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--submit-time-after` | No | timestamp | None | Filter by submit time |
| `--submit-time-before` | No | timestamp | None | Filter by submit time |
| `--status-equals` | No | string | None | Filter: `InProgress`, `Completed`, `Failed` |
| `--sort-by` | No | string | None | Sort field: `SubmitTime` |
| `--sort-order` | No | string | None | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "nextToken": "string",
    "asyncInvokeSummaries": [
        {
            "invocationArn": "string",
            "modelArn": "string",
            "status": "InProgress|Completed|Failed",
            "submitTime": "timestamp",
            "endTime": "timestamp",
            "outputDataConfig": {...}
        }
    ]
}
```
