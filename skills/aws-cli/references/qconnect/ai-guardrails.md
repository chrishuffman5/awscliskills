# AI Guardrails

### 6.1 `create-ai-guardrail`

Creates content filtering guardrails for AI agents.

**Synopsis:**
```bash
aws qconnect create-ai-guardrail \
    --assistant-id <value> \
    --name <value> \
    --blocked-input-messaging <value> \
    --blocked-outputs-messaging <value> \
    --visibility-status <value> \
    [--description <value>] \
    [--topic-policy-config <value>] \
    [--content-policy-config <value>] \
    [--word-policy-config <value>] \
    [--sensitive-information-policy-config <value>] \
    [--contextual-grounding-policy-config <value>] \
    [--client-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--name` | **Yes** | string | -- | Guardrail name (1-255 chars) |
| `--blocked-input-messaging` | **Yes** | string | -- | Message when input is blocked (1-500 chars) |
| `--blocked-outputs-messaging` | **Yes** | string | -- | Message when output is blocked (1-500 chars) |
| `--visibility-status` | **Yes** | string | -- | `SAVED` or `PUBLISHED` |
| `--description` | No | string | None | Description (1-200 chars) |
| `--topic-policy-config` | No | structure | None | Denied topics config |
| `--content-policy-config` | No | structure | None | Content filter config |
| `--word-policy-config` | No | structure | None | Word/profanity filter config |
| `--sensitive-information-policy-config` | No | structure | None | PII and regex filter config |
| `--contextual-grounding-policy-config` | No | structure | None | Grounding/relevance filters |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Content Policy Config:**
```json
{
    "filtersConfig": [
        {
            "type": "SEXUAL|VIOLENCE|HATE|INSULTS|MISCONDUCT|PROMPT_ATTACK",
            "inputStrength": "NONE|LOW|MEDIUM|HIGH",
            "outputStrength": "NONE|LOW|MEDIUM|HIGH"
        }
    ]
}
```

**Sensitive Information Policy Config:**
```json
{
    "piiEntitiesConfig": [
        {"type": "ADDRESS|EMAIL|PHONE|NAME|...", "action": "BLOCK|ANONYMIZE"}
    ],
    "regexesConfig": [
        {"name": "string", "pattern": "string", "action": "BLOCK|ANONYMIZE"}
    ]
}
```

**Contextual Grounding Policy Config:**
```json
{
    "filtersConfig": [
        {"type": "GROUNDING|RELEVANCE", "threshold": 0.7}
    ]
}
```

**Output Schema:**
```json
{
    "aiGuardrail": {
        "assistantId": "string",
        "assistantArn": "string",
        "aiGuardrailId": "string",
        "aiGuardrailArn": "string",
        "name": "string",
        "visibilityStatus": "string",
        "blockedInputMessaging": "string",
        "blockedOutputsMessaging": "string",
        "description": "string",
        "topicPolicyConfig": {},
        "contentPolicyConfig": {},
        "wordPolicyConfig": {},
        "sensitiveInformationPolicyConfig": {},
        "contextualGroundingPolicyConfig": {},
        "tags": {},
        "status": "string",
        "modifiedTime": "timestamp"
    }
}
```

---

### 6.2 `create-ai-guardrail-version`

Creates an immutable version of an AI guardrail.

**Synopsis:**
```bash
aws qconnect create-ai-guardrail-version \
    --assistant-id <value> \
    --ai-guardrail-id <value> \
    [--client-token <value>] \
    [--modified-time <value>]
```

---

### 6.3 `get-ai-guardrail`

Gets an AI guardrail.

**Synopsis:**
```bash
aws qconnect get-ai-guardrail \
    --assistant-id <value> \
    --ai-guardrail-id <value>
```

---

### 6.4 `list-ai-guardrails`

Lists AI guardrails. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-ai-guardrails \
    --assistant-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

---

### 6.5 `list-ai-guardrail-versions`

Lists versions of an AI guardrail. **Paginated operation.**

---

### 6.6 `update-ai-guardrail`

Updates an AI guardrail.

**Synopsis:**
```bash
aws qconnect update-ai-guardrail \
    --assistant-id <value> \
    --ai-guardrail-id <value> \
    --visibility-status <value> \
    --blocked-input-messaging <value> \
    --blocked-outputs-messaging <value> \
    [--name <value>] \
    [--description <value>] \
    [--topic-policy-config <value>] \
    [--content-policy-config <value>] \
    [--word-policy-config <value>] \
    [--sensitive-information-policy-config <value>] \
    [--contextual-grounding-policy-config <value>] \
    [--client-token <value>]
```

---

### 6.7 `delete-ai-guardrail`

Deletes an AI guardrail.

**Synopsis:**
```bash
aws qconnect delete-ai-guardrail \
    --assistant-id <value> \
    --ai-guardrail-id <value>
```

**Output:** None

---

### 6.8 `delete-ai-guardrail-version`

Deletes a specific version of an AI guardrail.

**Synopsis:**
```bash
aws qconnect delete-ai-guardrail-version \
    --assistant-id <value> \
    --ai-guardrail-id <value> \
    --version-number <value>
```

**Output:** None
