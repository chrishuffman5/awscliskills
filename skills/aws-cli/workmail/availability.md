# Availability

### 11.1 `create-availability-configuration`

Creates an availability provider configuration for a domain (EWS or Lambda).

**Synopsis:**
```bash
aws workmail create-availability-configuration \
    --organization-id <value> \
    --domain-name <value> \
    [--client-token <value>] \
    [--ews-provider <value>] \
    [--lambda-provider <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--domain-name` | **Yes** | string | -- | Domain name (3-255 chars) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--ews-provider` | No | structure | None | EWS availability provider (mutually exclusive with lambda-provider) |
| `--lambda-provider` | No | structure | None | Lambda availability provider (mutually exclusive with ews-provider) |

**EWS Provider structure:**
```json
{
    "EwsEndpoint": "https://exchange.example.com/ews/exchange.asmx",
    "EwsUsername": "string",
    "EwsPassword": "string"
}
```

**Lambda Provider structure:**
```json
{
    "LambdaArn": "arn:aws:lambda:us-east-1:123456789012:function:my-function"
}
```

**Output:** None

---

### 11.2 `list-availability-configurations`

Lists availability configurations for an organization. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-availability-configurations \
    --organization-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "AvailabilityConfigurations": [
        {
            "DomainName": "string",
            "ProviderType": "EWS|LAMBDA",
            "EwsProvider": {
                "EwsEndpoint": "string",
                "EwsUsername": "string"
            },
            "LambdaProvider": {
                "LambdaArn": "string"
            },
            "DateCreated": "timestamp",
            "DateModified": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.3 `update-availability-configuration`

Updates an availability configuration for a domain.

**Synopsis:**
```bash
aws workmail update-availability-configuration \
    --organization-id <value> \
    --domain-name <value> \
    [--ews-provider <value>] \
    [--lambda-provider <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--ews-provider` | No | structure | None | Updated EWS provider |
| `--lambda-provider` | No | structure | None | Updated Lambda provider |

**Output:** None

---

### 11.4 `delete-availability-configuration`

Deletes an availability configuration for a domain.

**Synopsis:**
```bash
aws workmail delete-availability-configuration \
    --organization-id <value> \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--domain-name` | **Yes** | string | -- | Domain name |

**Output:** None

---

### 11.5 `test-availability-configuration`

Tests an availability configuration by performing a lookup against the provider.

**Synopsis:**
```bash
aws workmail test-availability-configuration \
    --organization-id <value> \
    [--domain-name <value>] \
    [--ews-provider <value>] \
    [--lambda-provider <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--domain-name` | No | string | None | Domain to test (uses existing config) |
| `--ews-provider` | No | structure | None | EWS provider to test |
| `--lambda-provider` | No | structure | None | Lambda provider to test |

**Output Schema:**
```json
{
    "TestPassed": "boolean",
    "FailureReason": "string"
}
```
