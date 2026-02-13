# Domain Names & Base Path Mappings

### 8.1 `create-domain-name`

Creates a custom domain name for use with API Gateway.

**Synopsis:**
```bash
aws apigateway create-domain-name \
    --domain-name <value> \
    [--certificate-name <value>] \
    [--certificate-body <value>] \
    [--certificate-private-key <value>] \
    [--certificate-chain <value>] \
    [--certificate-arn <value>] \
    [--regional-certificate-name <value>] \
    [--regional-certificate-arn <value>] \
    [--endpoint-configuration <value>] \
    [--tags <value>] \
    [--security-policy <value>] \
    [--mutual-tls-authentication <value>] \
    [--ownership-verification-certificate-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name (e.g., `api.example.com`) |
| `--certificate-name` | No | string | None | Name for the edge-optimized certificate |
| `--certificate-body` | No | string | None | PEM-encoded certificate body (edge) |
| `--certificate-private-key` | No | string | None | PEM-encoded private key (edge) |
| `--certificate-chain` | No | string | None | PEM-encoded certificate chain (edge) |
| `--certificate-arn` | No | string | None | ACM certificate ARN for edge-optimized endpoint (must be in us-east-1) |
| `--regional-certificate-name` | No | string | None | Name for the regional certificate |
| `--regional-certificate-arn` | No | string | None | ACM certificate ARN for regional endpoint |
| `--endpoint-configuration` | No | structure | None | Endpoint type. Shorthand: `types=EDGE\|REGIONAL` |
| `--tags` | No | map | None | Key-value tags |
| `--security-policy` | No | string | `TLS_1_2` | TLS version: `TLS_1_0` or `TLS_1_2` |
| `--mutual-tls-authentication` | No | structure | None | Mutual TLS config. Shorthand: `truststoreUri=string,truststoreVersion=string` |
| `--ownership-verification-certificate-arn` | No | string | None | ACM certificate ARN for ownership verification |

**Output Schema:**
```json
{
    "domainName": "string",
    "certificateName": "string",
    "certificateArn": "string",
    "certificateUploadDate": "timestamp",
    "regionalDomainName": "string",
    "regionalHostedZoneId": "string",
    "regionalCertificateName": "string",
    "regionalCertificateArn": "string",
    "distributionDomainName": "string",
    "distributionHostedZoneId": "string",
    "endpointConfiguration": {
        "types": ["EDGE|REGIONAL"],
        "vpcEndpointIds": ["string"]
    },
    "domainNameStatus": "AVAILABLE|UPDATING|PENDING|PENDING_CERTIFICATE_REIMPORT|PENDING_OWNERSHIP_VERIFICATION",
    "domainNameStatusMessage": "string",
    "securityPolicy": "TLS_1_0|TLS_1_2",
    "tags": {},
    "mutualTlsAuthentication": {
        "truststoreUri": "string",
        "truststoreVersion": "string",
        "truststoreWarnings": ["string"]
    },
    "ownershipVerificationCertificateArn": "string"
}
```

---

### 8.2 `delete-domain-name`

Deletes a custom domain name.

**Synopsis:**
```bash
aws apigateway delete-domain-name \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name to delete |

**Output:** None

---

### 8.3 `get-domain-name`

Gets information about a custom domain name.

**Synopsis:**
```bash
aws apigateway get-domain-name \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name |

**Output Schema:** Same as `create-domain-name`.

---

### 8.4 `get-domain-names`

Lists custom domain names. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-domain-names \
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
| `--page-size` | No | integer | None | Items per API call (max 500) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "domainName": "string",
            "certificateName": "string",
            "certificateArn": "string",
            "regionalDomainName": "string",
            "regionalCertificateArn": "string",
            "distributionDomainName": "string",
            "endpointConfiguration": {},
            "domainNameStatus": "string",
            "securityPolicy": "string",
            "tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-domain-name`

Updates a custom domain name using patch operations.

**Synopsis:**
```bash
aws apigateway update-domain-name \
    --domain-name <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name |
| `--patch-operations` | No | list | None | Patch operations |

**Supported Patch Paths:** `/certificateArn`, `/regionalCertificateArn`, `/certificateName`, `/regionalCertificateName`, `/securityPolicy`, `/mutualTlsAuthentication/truststoreUri`, `/mutualTlsAuthentication/truststoreVersion`

**Output Schema:** Same as `create-domain-name`.

---

### 8.6 `create-base-path-mapping`

Creates a base path mapping that maps a path to a REST API stage.

**Synopsis:**
```bash
aws apigateway create-base-path-mapping \
    --domain-name <value> \
    --rest-api-id <value> \
    [--base-path <value>] \
    [--stage <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name |
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--base-path` | No | string | `(none)` | Base path (e.g., `v1`). Use `(none)` for root |
| `--stage` | No | string | None | Stage name to map to |

**Output Schema:**
```json
{
    "basePath": "string",
    "restApiId": "string",
    "stage": "string"
}
```

---

### 8.7 `delete-base-path-mapping`

Deletes a base path mapping.

**Synopsis:**
```bash
aws apigateway delete-base-path-mapping \
    --domain-name <value> \
    --base-path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name |
| `--base-path` | **Yes** | string | -- | Base path (use `(none)` for root mapping) |

**Output:** None

---

### 8.8 `get-base-path-mapping`

Gets a base path mapping.

**Synopsis:**
```bash
aws apigateway get-base-path-mapping \
    --domain-name <value> \
    --base-path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name |
| `--base-path` | **Yes** | string | -- | Base path (use `(none)` for root mapping) |

**Output Schema:** Same as `create-base-path-mapping`.

---

### 8.9 `get-base-path-mappings`

Lists base path mappings for a domain name. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-base-path-mappings \
    --domain-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "basePath": "string",
            "restApiId": "string",
            "stage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.10 `update-base-path-mapping`

Updates a base path mapping using patch operations.

**Synopsis:**
```bash
aws apigateway update-base-path-mapping \
    --domain-name <value> \
    --base-path <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Custom domain name |
| `--base-path` | **Yes** | string | -- | Base path |
| `--patch-operations` | No | list | None | Patch operations |

**Supported Patch Paths:** `/basePath`, `/restApiId`, `/stage`

**Output Schema:** Same as `create-base-path-mapping`.
