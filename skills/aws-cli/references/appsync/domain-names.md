# Domain Names

### 8.1 `create-domain-name`

Creates a custom domain name for an AppSync API.

**Synopsis:**
```bash
aws appsync create-domain-name \
    --domain-name <value> \
    --certificate-arn <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name (1-253 chars) |
| `--certificate-arn` | **Yes** | string | -- | ACM certificate ARN (must be in us-east-1) |
| `--description` | No | string | None | Description (0-255 chars) |
| `--tags` | No | map | None | Resource tags (max 50) |

**Output Schema:**
```json
{
    "domainNameConfig": {
        "domainName": "string",
        "description": "string",
        "certificateArn": "string",
        "appsyncDomainName": "string",
        "hostedZoneId": "string",
        "domainNameArn": "string",
        "tags": {"string": "string"}
    }
}
```

---

### 8.2 `get-domain-name`

Retrieves a custom domain name configuration.

**Synopsis:**
```bash
aws appsync get-domain-name \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | The domain name |

**Output Schema:** Same as `create-domain-name`.

---

### 8.3 `list-domain-names`

Lists custom domain names. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-domain-names \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "domainNameConfigs": [
        {
            "domainName": "string",
            "description": "string",
            "certificateArn": "string",
            "appsyncDomainName": "string",
            "hostedZoneId": "string",
            "domainNameArn": "string",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 8.4 `update-domain-name`

Updates a custom domain name configuration.

**Synopsis:**
```bash
aws appsync update-domain-name \
    --domain-name <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | The domain name |
| `--description` | No | string | None | Updated description |

**Output Schema:** Same as `create-domain-name`.

---

### 8.5 `delete-domain-name`

Deletes a custom domain name.

**Synopsis:**
```bash
aws appsync delete-domain-name \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | The domain name to delete |

**Output:** None

---

### 8.6 `associate-api`

Associates a GraphQL API with a custom domain name.

**Synopsis:**
```bash
aws appsync associate-api \
    --domain-name <value> \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | The domain name |
| `--api-id` | **Yes** | string | -- | The API ID (private APIs cannot be associated) |

**Output Schema:**
```json
{
    "apiAssociation": {
        "domainName": "string",
        "apiId": "string",
        "associationStatus": "PROCESSING|FAILED|SUCCESS",
        "deploymentDetail": "string"
    }
}
```

---

### 8.7 `get-api-association`

Gets the API association for a custom domain name.

**Synopsis:**
```bash
aws appsync get-api-association \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | The domain name |

**Output Schema:**
```json
{
    "apiAssociation": {
        "domainName": "string",
        "apiId": "string",
        "associationStatus": "PROCESSING|FAILED|SUCCESS",
        "deploymentDetail": "string"
    }
}
```

---

### 8.8 `disassociate-api`

Disassociates a GraphQL API from a custom domain name.

**Synopsis:**
```bash
aws appsync disassociate-api \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | The domain name to disassociate |

**Output:** None
