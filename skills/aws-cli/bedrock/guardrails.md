# Guardrails

### `create-guardrail`

Creates a guardrail to block topics and implement safeguards for generative AI applications. Supports content filters, denied topics, word filters, PII detection, contextual grounding, and automated reasoning.

**Synopsis:**
```bash
aws bedrock create-guardrail \
    --name <value> \
    --blocked-input-messaging <value> \
    --blocked-outputs-messaging <value> \
    [--description <value>] \
    [--topic-policy-config <value>] \
    [--content-policy-config <value>] \
    [--word-policy-config <value>] \
    [--sensitive-information-policy-config <value>] \
    [--contextual-grounding-policy-config <value>] \
    [--automated-reasoning-policy-config <value>] \
    [--cross-region-config <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Guardrail name (1-50 chars). Pattern: `[0-9a-zA-Z-_]+` |
| `--blocked-input-messaging` | **Yes** | string | -- | Message when input is blocked (1-500 chars) |
| `--blocked-outputs-messaging` | **Yes** | string | -- | Message when output is blocked (1-500 chars) |
| `--description` | No | string | None | Description (1-200 chars) |
| `--topic-policy-config` | No | structure | None | Topic denial policies |
| `--content-policy-config` | No | structure | None | Content filter policies |
| `--word-policy-config` | No | structure | None | Word filter policies |
| `--sensitive-information-policy-config` | No | structure | None | PII and regex policies |
| `--contextual-grounding-policy-config` | No | structure | None | Grounding and relevance policies |
| `--automated-reasoning-policy-config` | No | structure | None | Automated reasoning policies |
| `--cross-region-config` | No | structure | None | Cross-region guardrail profile |
| `--kms-key-id` | No | string | None | KMS key ARN for encryption (1-2048 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |

**Content Policy Config Structure:**
```json
{
    "filtersConfig": [
        {
            "type": "SEXUAL|VIOLENCE|HATE|INSULTS|MISCONDUCT|PROMPT_ATTACK",
            "inputStrength": "NONE|LOW|MEDIUM|HIGH",
            "outputStrength": "NONE|LOW|MEDIUM|HIGH",
            "inputModalities": ["TEXT|IMAGE"],
            "outputModalities": ["TEXT|IMAGE"]
        }
    ]
}
```

**Topic Policy Config Structure:**
```json
{
    "topicsConfig": [
        {
            "name": "string",
            "definition": "string",
            "examples": ["string"],
            "type": "DENY"
        }
    ]
}
```

**Sensitive Information Policy Config Structure:**
```json
{
    "piiEntitiesConfig": [
        {
            "type": "ADDRESS|EMAIL|PHONE|US_SOCIAL_SECURITY_NUMBER|...",
            "action": "BLOCK|ANONYMIZE"
        }
    ],
    "regexesConfig": [
        {
            "name": "string",
            "description": "string",
            "pattern": "string",
            "action": "BLOCK|ANONYMIZE"
        }
    ]
}
```

**Word Policy Config Structure:**
```json
{
    "wordsConfig": [
        {
            "text": "string"
        }
    ],
    "managedWordListsConfig": [
        {
            "type": "PROFANITY"
        }
    ]
}
```

**Contextual Grounding Policy Config Structure:**
```json
{
    "filtersConfig": [
        {
            "type": "GROUNDING|RELEVANCE",
            "threshold": 0.0
        }
    ]
}
```

**Output Schema:**
```json
{
    "guardrailId": "string",
    "guardrailArn": "string",
    "version": "DRAFT",
    "createdAt": "timestamp"
}
```

---

### `get-guardrail`

Gets details of a guardrail.

**Synopsis:**
```bash
aws bedrock get-guardrail \
    --guardrail-identifier <value> \
    [--guardrail-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--guardrail-identifier` | **Yes** | string | -- | Guardrail ID or ARN |
| `--guardrail-version` | No | string | None | Version number or `DRAFT` |

**Output Schema:**
```json
{
    "name": "string",
    "description": "string",
    "guardrailId": "string",
    "guardrailArn": "string",
    "version": "string",
    "status": "CREATING|UPDATING|VERSIONING|READY|FAILED|DELETING",
    "topicPolicy": {
        "topics": [
            {
                "name": "string",
                "definition": "string",
                "examples": ["string"],
                "type": "DENY"
            }
        ]
    },
    "contentPolicy": {
        "filters": [
            {
                "type": "SEXUAL|VIOLENCE|HATE|INSULTS|MISCONDUCT|PROMPT_ATTACK",
                "inputStrength": "NONE|LOW|MEDIUM|HIGH",
                "outputStrength": "NONE|LOW|MEDIUM|HIGH"
            }
        ]
    },
    "wordPolicy": {
        "words": [{"text": "string"}],
        "managedWordLists": [{"type": "PROFANITY"}]
    },
    "sensitiveInformationPolicy": {
        "piiEntities": [{"type": "string", "action": "BLOCK|ANONYMIZE"}],
        "regexes": [{"name": "string", "pattern": "string", "action": "BLOCK|ANONYMIZE"}]
    },
    "contextualGroundingPolicy": {
        "filters": [{"type": "GROUNDING|RELEVANCE", "threshold": "double"}]
    },
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "statusReasons": ["string"],
    "failureRecommendations": ["string"],
    "blockedInputMessaging": "string",
    "blockedOutputsMessaging": "string",
    "kmsKeyArn": "string"
}
```

---

### `list-guardrails`

Lists guardrails in the account. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-guardrails \
    [--guardrail-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--guardrail-identifier` | No | string | None | Filter by guardrail ID (lists versions) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "guardrails": [
        {
            "id": "string",
            "arn": "string",
            "status": "CREATING|UPDATING|VERSIONING|READY|FAILED|DELETING",
            "name": "string",
            "description": "string",
            "version": "string",
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-guardrail`

Updates a guardrail configuration.

**Synopsis:**
```bash
aws bedrock update-guardrail \
    --guardrail-identifier <value> \
    --name <value> \
    --blocked-input-messaging <value> \
    --blocked-outputs-messaging <value> \
    [--description <value>] \
    [--topic-policy-config <value>] \
    [--content-policy-config <value>] \
    [--word-policy-config <value>] \
    [--sensitive-information-policy-config <value>] \
    [--contextual-grounding-policy-config <value>] \
    [--automated-reasoning-policy-config <value>] \
    [--cross-region-config <value>] \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--guardrail-identifier` | **Yes** | string | -- | Guardrail ID or ARN |
| `--name` | **Yes** | string | -- | Updated name (1-50 chars) |
| `--blocked-input-messaging` | **Yes** | string | -- | Updated blocked input message |
| `--blocked-outputs-messaging` | **Yes** | string | -- | Updated blocked output message |
| `--description` | No | string | None | Updated description |
| (all policy configs) | No | structure | None | Same structure as create-guardrail |
| `--kms-key-id` | No | string | None | KMS key ARN |

**Output Schema:**
```json
{
    "guardrailId": "string",
    "guardrailArn": "string",
    "version": "DRAFT",
    "updatedAt": "timestamp"
}
```

---

### `delete-guardrail`

Deletes a guardrail.

**Synopsis:**
```bash
aws bedrock delete-guardrail \
    --guardrail-identifier <value> \
    [--guardrail-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--guardrail-identifier` | **Yes** | string | -- | Guardrail ID or ARN |
| `--guardrail-version` | No | string | None | Version to delete (omit to delete all) |

**Output:** None (HTTP 200 on success)

---

### `create-guardrail-version`

Creates a versioned snapshot of a guardrail. Versions are immutable.

**Synopsis:**
```bash
aws bedrock create-guardrail-version \
    --guardrail-identifier <value> \
    [--description <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--guardrail-identifier` | **Yes** | string | -- | Guardrail ID or ARN |
| `--description` | No | string | None | Version description (1-200 chars) |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "guardrailId": "string",
    "version": "string"
}
```

---

### `get-guardrail-policy`

Gets the policy details for a guardrail.

**Synopsis:**
```bash
aws bedrock get-guardrail-policy \
    --guardrail-identifier <value> \
    [--guardrail-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--guardrail-identifier` | **Yes** | string | -- | Guardrail ID or ARN |
| `--guardrail-version` | No | string | None | Version number or `DRAFT` |

**Output Schema:**
```json
{
    "guardrailId": "string",
    "guardrailArn": "string",
    "version": "string",
    "topicPolicy": {...},
    "contentPolicy": {...},
    "wordPolicy": {...},
    "sensitiveInformationPolicy": {...},
    "contextualGroundingPolicy": {...},
    "automatedReasoningPolicy": {...}
}
```
