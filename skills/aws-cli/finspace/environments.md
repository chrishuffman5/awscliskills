# Environments

## Legacy FinSpace Environments

### 1.1 `create-environment`

Creates a new legacy FinSpace environment.

**Synopsis:**
```bash
aws finspace create-environment \
    --name <value> \
    [--description <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--federation-mode <value>] \
    [--federation-parameters <value>] \
    [--superuser-parameters <value>] \
    [--data-bundles <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name (1-255 chars) |
| `--description` | No | string | None | Description (1-1000 chars) |
| `--kms-key-id` | No | string | AWS managed | KMS key for encryption |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |
| `--federation-mode` | No | string | `LOCAL` | Federation mode: `FEDERATED` or `LOCAL` |
| `--federation-parameters` | No | structure | None | Federation config (SAML) |
| `--superuser-parameters` | No | structure | None | Initial superuser |
| `--data-bundles` | No | list(string) | None | Data bundles to install |

**Output Schema:**
```json
{
    "environmentId": "string",
    "environmentArn": "string",
    "environmentUrl": "string"
}
```

---

### 1.2 `delete-environment`

Deletes a legacy FinSpace environment.

**Synopsis:**
```bash
aws finspace delete-environment \
    --environment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID to delete |

**Output:** None (HTTP 200 on success)

---

### 1.3 `get-environment`

Returns details of a legacy FinSpace environment.

**Synopsis:**
```bash
aws finspace get-environment \
    --environment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |

**Output Schema:**
```json
{
    "environment": {
        "name": "string",
        "environmentId": "string",
        "awsAccountId": "string",
        "status": "CREATE_REQUESTED|CREATING|CREATED|DELETE_REQUESTED|DELETING|DELETED|FAILED_CREATION|RETRY_DELETION|FAILED_DELETION|SUSPENDED",
        "environmentUrl": "string",
        "description": "string",
        "environmentArn": "string",
        "sageMakerStudioDomainUrl": "string",
        "kmsKeyId": "string",
        "dedicatedServiceAccountId": "string",
        "federationMode": "FEDERATED|LOCAL",
        "federationParameters": {
            "samlMetadataDocument": "string",
            "samlMetadataURL": "string",
            "applicationCallBackURL": "string",
            "federationURN": "string",
            "federationProviderName": "string",
            "attributeMap": {}
        }
    }
}
```

---

### 1.4 `list-environments`

Returns a list of legacy FinSpace environments. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-environments \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results per page |

**Output Schema:**
```json
{
    "environments": [
        {
            "name": "string",
            "environmentId": "string",
            "status": "string",
            "environmentUrl": "string",
            "description": "string",
            "environmentArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-environment`

Updates a legacy FinSpace environment.

**Synopsis:**
```bash
aws finspace update-environment \
    --environment-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--federation-mode <value>] \
    [--federation-parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--name` | No | string | -- | New name |
| `--description` | No | string | -- | New description |
| `--federation-mode` | No | string | -- | New federation mode |
| `--federation-parameters` | No | structure | -- | New federation config |

**Output Schema:** Same as `get-environment` output.

---

## KX Environments

### 1.6 `create-kx-environment`

Creates a new KX (kdb+) environment.

**Synopsis:**
```bash
aws finspace create-kx-environment \
    --name <value> \
    [--description <value>] \
    --kms-key-id <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name (1-255 chars) |
| `--kms-key-id` | **Yes** | string | -- | KMS key ARN for encryption |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "name": "string",
    "status": "CREATE_REQUESTED|CREATING|CREATED|DELETE_REQUESTED|DELETING|DELETED|FAILED_CREATION|RETRY_DELETION|FAILED_DELETION|UPDATE_NETWORK_REQUESTED|UPDATING_NETWORK|FAILED_UPDATING_NETWORK|SUSPENDED",
    "environmentId": "string",
    "description": "string",
    "environmentArn": "string",
    "kmsKeyId": "string",
    "creationTimestamp": "timestamp"
}
```

---

### 1.7 `delete-kx-environment`

Deletes a KX environment.

**Synopsis:**
```bash
aws finspace delete-kx-environment \
    --environment-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID to delete |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 1.8 `get-kx-environment`

Returns details of a KX environment.

**Synopsis:**
```bash
aws finspace get-kx-environment \
    --environment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |

**Output Schema:**
```json
{
    "name": "string",
    "environmentId": "string",
    "awsAccountId": "string",
    "status": "string",
    "tgwStatus": "NONE|UPDATE_REQUESTED|UPDATING|FAILED_UPDATE|SUCCESSFULLY_UPDATED",
    "dnsStatus": "NONE|UPDATE_REQUESTED|UPDATING|FAILED_UPDATE|SUCCESSFULLY_UPDATED",
    "errorMessage": "string",
    "description": "string",
    "environmentArn": "string",
    "kmsKeyId": "string",
    "dedicatedServiceAccountId": "string",
    "transitGatewayConfiguration": {
        "transitGatewayID": "string",
        "routableCIDRSpace": "string",
        "attachmentNetworkAclConfiguration": []
    },
    "customDNSConfiguration": [
        {
            "customDNSServerName": "string",
            "customDNSServerIP": "string"
        }
    ],
    "creationTimestamp": "timestamp",
    "updateTimestamp": "timestamp",
    "availabilityZoneIds": ["string"],
    "certificateAuthorityArn": "string"
}
```

---

### 1.9 `list-kx-environments`

Returns a list of KX environments. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-environments \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results per page |

**Output Schema:**
```json
{
    "environments": [
        {
            "name": "string",
            "environmentId": "string",
            "awsAccountId": "string",
            "status": "string",
            "description": "string",
            "environmentArn": "string",
            "kmsKeyId": "string",
            "creationTimestamp": "timestamp",
            "updateTimestamp": "timestamp",
            "availabilityZoneIds": ["string"],
            "certificateAuthorityArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.10 `update-kx-environment`

Updates the configuration of a KX environment.

**Synopsis:**
```bash
aws finspace update-kx-environment \
    --environment-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--name` | No | string | -- | New name |
| `--description` | No | string | -- | New description |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:** Same as `get-kx-environment` output.

---

### 1.11 `update-kx-environment-network`

Updates the network configuration for a KX environment, including transit gateway and DNS settings.

**Synopsis:**
```bash
aws finspace update-kx-environment-network \
    --environment-id <value> \
    [--transit-gateway-configuration <value>] \
    [--custom-dns-configuration <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--transit-gateway-configuration` | No | structure | -- | Transit gateway config |
| `--custom-dns-configuration` | No | list | -- | Custom DNS servers |
| `--client-token` | No | string | Auto | Idempotency token |

**Transit Gateway Configuration:**
```json
{
    "transitGatewayID": "string",
    "routableCIDRSpace": "string",
    "attachmentNetworkAclConfiguration": [
        {
            "ruleNumber": "integer",
            "protocol": "string",
            "ruleAction": "allow|deny",
            "portRange": {
                "from": "integer",
                "to": "integer"
            },
            "icmpTypeCode": {
                "type": "integer",
                "code": "integer"
            },
            "cidrBlock": "string"
        }
    ]
}
```

**Output Schema:** Same as `get-kx-environment` output.
