# Marketplace

### `create-marketplace-model-endpoint`

Creates an endpoint for a model from Amazon Bedrock Marketplace. The endpoint is hosted by Amazon SageMaker.

**Synopsis:**
```bash
aws bedrock create-marketplace-model-endpoint \
    --model-source-identifier <value> \
    --endpoint-config <value> \
    --endpoint-name <value> \
    [--accept-eula | --no-accept-eula] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-source-identifier` | **Yes** | string | -- | ARN of the marketplace model (max 2048 chars) |
| `--endpoint-config` | **Yes** | structure | -- | SageMaker endpoint configuration |
| `--endpoint-name` | **Yes** | string | -- | Endpoint name (1-30 chars, unique per account/region) |
| `--accept-eula` | No | boolean | false | Accept the EULA for the model |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Endpoint Config Structure:**
```json
{
    "sageMaker": {
        "initialInstanceCount": 1,
        "instanceType": "ml.g5.xlarge",
        "executionRole": "arn:aws:iam::123456789012:role/SageMakerRole",
        "kmsEncryptionKey": "arn:aws:kms:...",
        "vpc": {
            "subnetIds": ["subnet-xxx"],
            "securityGroupIds": ["sg-xxx"]
        }
    }
}
```

**Output Schema:**
```json
{
    "marketplaceModelEndpoint": {
        "endpointArn": "string",
        "modelSourceIdentifier": "string",
        "status": "REGISTERED|INCOMPATIBLE_ENDPOINT",
        "statusMessage": "string",
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "endpointConfig": {
            "sageMaker": {
                "initialInstanceCount": "integer",
                "instanceType": "string",
                "executionRole": "string",
                "kmsEncryptionKey": "string",
                "vpc": {
                    "subnetIds": ["string"],
                    "securityGroupIds": ["string"]
                }
            }
        },
        "endpointStatus": "string",
        "endpointStatusMessage": "string"
    }
}
```

---

### `get-marketplace-model-endpoint`

Gets details of a marketplace model endpoint.

**Synopsis:**
```bash
aws bedrock get-marketplace-model-endpoint \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | Endpoint ARN |

**Output Schema:**
```json
{
    "marketplaceModelEndpoint": {
        "endpointArn": "string",
        "modelSourceIdentifier": "string",
        "status": "REGISTERED|INCOMPATIBLE_ENDPOINT",
        "statusMessage": "string",
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "endpointConfig": {...},
        "endpointStatus": "string",
        "endpointStatusMessage": "string"
    }
}
```

---

### `list-marketplace-model-endpoints`

Lists marketplace model endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-marketplace-model-endpoints \
    [--model-source-equals <value>] \
    [--name-contains <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-source-equals` | No | string | None | Filter by model source |
| `--name-contains` | No | string | None | Filter by name substring |

**Output Schema:**
```json
{
    "marketplaceModelEndpoints": [
        {
            "endpointArn": "string",
            "modelSourceIdentifier": "string",
            "status": "REGISTERED|INCOMPATIBLE_ENDPOINT",
            "createdAt": "timestamp",
            "updatedAt": "timestamp",
            "endpointStatus": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-marketplace-model-endpoint`

Updates a marketplace model endpoint configuration.

**Synopsis:**
```bash
aws bedrock update-marketplace-model-endpoint \
    --endpoint-arn <value> \
    --endpoint-config <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | Endpoint ARN |
| `--endpoint-config` | **Yes** | structure | -- | Updated SageMaker endpoint config |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "marketplaceModelEndpoint": {
        "endpointArn": "string",
        "modelSourceIdentifier": "string",
        "status": "string",
        "endpointConfig": {...},
        "endpointStatus": "string",
        "createdAt": "timestamp",
        "updatedAt": "timestamp"
    }
}
```

---

### `delete-marketplace-model-endpoint`

Deletes a marketplace model endpoint.

**Synopsis:**
```bash
aws bedrock delete-marketplace-model-endpoint \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | Endpoint ARN |

**Output:** None (HTTP 200 on success)

---

### `register-marketplace-model-endpoint`

Registers an existing SageMaker endpoint as a Bedrock marketplace model endpoint.

**Synopsis:**
```bash
aws bedrock register-marketplace-model-endpoint \
    --endpoint-identifier <value> \
    --model-source-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-identifier` | **Yes** | string | -- | SageMaker endpoint ARN |
| `--model-source-identifier` | **Yes** | string | -- | Marketplace model ARN |

**Output Schema:**
```json
{
    "marketplaceModelEndpoint": {
        "endpointArn": "string",
        "modelSourceIdentifier": "string",
        "status": "REGISTERED|INCOMPATIBLE_ENDPOINT",
        "createdAt": "timestamp",
        "updatedAt": "timestamp"
    }
}
```

---

### `deregister-marketplace-model-endpoint`

Deregisters a marketplace model endpoint (does not delete the SageMaker endpoint).

**Synopsis:**
```bash
aws bedrock deregister-marketplace-model-endpoint \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | Endpoint ARN to deregister |

**Output:** None (HTTP 200 on success)
