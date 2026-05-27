# Recommendations

### 10.1 `notify-recommendations-received`

Marks recommendations as received by the agent.

**Synopsis:**
```bash
aws qconnect notify-recommendations-received \
    --assistant-id <value> \
    --session-id <value> \
    --recommendation-ids <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--session-id` | **Yes** | string | -- | Session ID or ARN |
| `--recommendation-ids` | **Yes** | list | -- | List of recommendation IDs |

**Output Schema:**
```json
{
    "recommendationIds": ["string"],
    "errors": [
        {
            "recommendationId": "string",
            "message": "string"
        }
    ]
}
```

---

### 10.2 `put-feedback`

Provides feedback on the relevance of a recommendation.

**Synopsis:**
```bash
aws qconnect put-feedback \
    --assistant-id <value> \
    --target-id <value> \
    --target-type <value> \
    --content-feedback <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--target-id` | **Yes** | string | -- | Target resource ID |
| `--target-type` | **Yes** | string | -- | Target type: `RECOMMENDATION`, `RESULT` |
| `--content-feedback` | **Yes** | structure | -- | Feedback: `generativeContentFeedbackData={relevance=HELPFUL|NOT_HELPFUL}` |

**Output Schema:**
```json
{
    "assistantId": "string",
    "assistantArn": "string",
    "targetId": "string",
    "targetType": "string",
    "contentFeedback": {}
}
```

---

### 10.3 `list-spans`

Lists monitoring spans for observability.

**Synopsis:**
```bash
aws qconnect list-spans \
    --assistant-id <value> \
    --session-id <value> \
    --message-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```
