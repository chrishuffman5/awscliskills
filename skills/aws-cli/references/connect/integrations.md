# Integrations

### 17.1 `create-integration-association`

Creates an integration association with an instance.

**Synopsis:**
```bash
aws connect create-integration-association \
    --instance-id <value> \
    --integration-type <value> \
    --integration-arn <value> \
    [--source-application-url <value>] \
    [--source-application-name <value>] \
    [--source-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--integration-type` | **Yes** | string | -- | `EVENT`, `VOICE_ID`, `PINPOINT_APP`, `WISDOM_ASSISTANT`, `WISDOM_KNOWLEDGE_BASE`, `WISDOM_QUICK_RESPONSES`, `CASES_DOMAIN`, `APPLICATION`, `FILE_SCANNER`, `SES_IDENTITY`, `ANALYTICS_CONNECTOR`, `CALL_TRANSFER_CONNECTOR`, `COGNITO_USER_POOL` |
| `--integration-arn` | **Yes** | string | -- | Integration resource ARN |
| `--source-application-url` | No | string | None | Source app URL (for EVENT type) |
| `--source-application-name` | No | string | None | Source app name (for EVENT type) |
| `--source-type` | No | string | None | `SALESFORCE`, `ZENDESK`, `CASES` |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "IntegrationAssociationId": "string",
    "IntegrationAssociationArn": "string"
}
```

---

### 17.2 `list-integration-associations`

Lists integration associations. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--integration-type` | No | string | None | Filter by type |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--integration-arn` | No | string | None | Filter by ARN |

**Output Schema:**
```json
{
    "IntegrationAssociationSummaryList": [ { "IntegrationAssociationId": "string", "IntegrationAssociationArn": "string", "InstanceId": "string", "IntegrationType": "string", "IntegrationArn": "string", "SourceApplicationUrl": "string", "SourceApplicationName": "string", "SourceType": "string" } ],
    "NextToken": "string"
}
```

---

### 17.3 `delete-integration-association`

Deletes an integration association.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--integration-association-id` | **Yes** | string | -- | Integration association ID |

**Output:** None

---

### 17.4 `associate-lambda-function`

Associates a Lambda function with an instance.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--function-arn` | **Yes** | string | -- | Lambda function ARN |

**Output:** None

---

### 17.5 `list-lambda-functions`

Lists Lambda functions associated with an instance. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-25) |

**Output Schema:**
```json
{
    "LambdaFunctions": ["string"],
    "NextToken": "string"
}
```

---

### 17.6 `disassociate-lambda-function`

Removes a Lambda function from an instance.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--function-arn` | **Yes** | string | -- | Lambda function ARN |

**Output:** None

---

### 17.7 `associate-lex-bot`

Associates a Lex bot with an instance.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--lex-bot` | **Yes** | structure | -- | `Name` and `LexRegion` |

**Output:** None

---

### 17.8 `list-lex-bots`

Lists Lex bots. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-25) |

---

### 17.9 `disassociate-lex-bot`

Removes a Lex bot from an instance.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--bot-name` | **Yes** | string | -- | Bot name |
| `--lex-region` | **Yes** | string | -- | Lex region |

**Output:** None

---

### 17.10-17.12 Bot Commands (V2)

`associate-bot`, `list-bots`, `disassociate-bot` manage Amazon Lex V2 bot associations. These require `--instance-id` and bot configuration with `LexV2Bot` containing `AliasArn`.

---

### 17.13-17.15 Use Case Commands

`create-use-case`, `list-use-cases`, `delete-use-case` manage use cases for integration associations. Require `--instance-id` and `--integration-association-id`.

**create-use-case output:**
```json
{
    "UseCaseId": "string",
    "UseCaseArn": "string"
}
```

---

### 17.16-17.18 Approved Origin Commands

`associate-approved-origin`, `list-approved-origins`, `disassociate-approved-origin` manage approved origins for an instance. Require `--instance-id` and `--origin` (URL).

**Output:** None (for associate/disassociate)
