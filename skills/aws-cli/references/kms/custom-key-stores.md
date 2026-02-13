# Custom Key Stores

### 7.1 `create-custom-key-store`

Creates a custom key store backed by AWS CloudHSM or an external key manager.

**Synopsis:**
```bash
aws kms create-custom-key-store \
    --custom-key-store-name <value> \
    [--cloud-hsm-cluster-id <value>] \
    [--trust-anchor-certificate <value>] \
    [--key-store-password <value>] \
    [--custom-key-store-type <value>] \
    [--xks-proxy-uri-endpoint <value>] \
    [--xks-proxy-uri-path <value>] \
    [--xks-proxy-connectivity <value>] \
    [--xks-proxy-authentication-credential <value>] \
    [--xks-proxy-vpc-endpoint-service-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-key-store-name` | **Yes** | string | -- | Unique name (1-256 chars) |
| `--cloud-hsm-cluster-id` | Cond. | string | -- | Required for `AWS_CLOUDHSM` type (19-24 chars) |
| `--trust-anchor-certificate` | Cond. | string | -- | Required for `AWS_CLOUDHSM` type. CA cert content (1-5000 chars) |
| `--key-store-password` | Cond. | string | -- | Required for `AWS_CLOUDHSM` type. kmsuser password (7-32 chars) |
| `--custom-key-store-type` | No | string | `AWS_CLOUDHSM` | Values: `AWS_CLOUDHSM`, `EXTERNAL_KEY_STORE` |
| `--xks-proxy-uri-endpoint` | Cond. | string | -- | Required for `EXTERNAL_KEY_STORE`. HTTPS endpoint (10-128 chars) |
| `--xks-proxy-uri-path` | Cond. | string | -- | Required for `EXTERNAL_KEY_STORE`. Must end with `/kms/xks/v1` (10-128 chars) |
| `--xks-proxy-connectivity` | Cond. | string | -- | Required for `EXTERNAL_KEY_STORE`. Values: `PUBLIC_ENDPOINT`, `VPC_ENDPOINT_SERVICE` |
| `--xks-proxy-authentication-credential` | Cond. | structure | -- | Required for `EXTERNAL_KEY_STORE`. Shorthand: `AccessKeyId=string,RawSecretAccessKey=string` |
| `--xks-proxy-vpc-endpoint-service-name` | Cond. | string | -- | Required when connectivity is `VPC_ENDPOINT_SERVICE` (20-64 chars) |

**Output Schema:**
```json
{
    "CustomKeyStoreId": "string"
}
```

---

### 7.2 `describe-custom-key-stores`

Returns information about custom key stores. **Paginated.**

**Synopsis:**
```bash
aws kms describe-custom-key-stores \
    [--custom-key-store-id <value>] \
    [--custom-key-store-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-key-store-id` | No | string | all stores | Filter by ID (1-64 chars) |
| `--custom-key-store-name` | No | string | all stores | Filter by name (1-256 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CustomKeyStores": [
        {
            "CustomKeyStoreId": "string",
            "CustomKeyStoreName": "string",
            "CloudHsmClusterId": "string",
            "TrustAnchorCertificate": "string",
            "ConnectionState": "CONNECTED|CONNECTING|FAILED|DISCONNECTED|DISCONNECTING",
            "ConnectionErrorCode": "string",
            "CreationDate": "timestamp",
            "CustomKeyStoreType": "AWS_CLOUDHSM|EXTERNAL_KEY_STORE",
            "XksProxyConfiguration": {
                "Connectivity": "PUBLIC_ENDPOINT|VPC_ENDPOINT_SERVICE",
                "AccessKeyId": "string",
                "UriEndpoint": "string",
                "UriPath": "string",
                "VpcEndpointServiceName": "string"
            }
        }
    ],
    "NextMarker": "string",
    "Truncated": true|false
}
```

---

### 7.3 `connect-custom-key-store`

Connects a custom key store to its backing key manager (CloudHSM cluster or external key store proxy).

**Synopsis:**
```bash
aws kms connect-custom-key-store --custom-key-store-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-key-store-id` | **Yes** | string | -- | Custom key store ID (1-64 chars) |

**Output:** None

---

### 7.4 `disconnect-custom-key-store`

Disconnects a custom key store from its backing key manager. Keys in the store become unusable.

**Synopsis:**
```bash
aws kms disconnect-custom-key-store --custom-key-store-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-key-store-id` | **Yes** | string | -- | Custom key store ID (1-64 chars) |

**Output:** None

---

### 7.5 `update-custom-key-store`

Updates properties of a custom key store. Must be disconnected first.

**Synopsis:**
```bash
aws kms update-custom-key-store \
    --custom-key-store-id <value> \
    [--new-custom-key-store-name <value>] \
    [--key-store-password <value>] \
    [--cloud-hsm-cluster-id <value>] \
    [--xks-proxy-uri-endpoint <value>] \
    [--xks-proxy-uri-path <value>] \
    [--xks-proxy-connectivity <value>] \
    [--xks-proxy-authentication-credential <value>] \
    [--xks-proxy-vpc-endpoint-service-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-key-store-id` | **Yes** | string | -- | Custom key store ID (1-64 chars) |
| `--new-custom-key-store-name` | No | string | -- | New name (1-256 chars) |
| `--key-store-password` | No | string | -- | New kmsuser password for CloudHSM (7-32 chars) |
| `--cloud-hsm-cluster-id` | No | string | -- | New CloudHSM cluster ID (19-24 chars) |
| `--xks-proxy-uri-endpoint` | No | string | -- | New XKS proxy endpoint (10-128 chars) |
| `--xks-proxy-uri-path` | No | string | -- | New XKS proxy path (10-128 chars) |
| `--xks-proxy-connectivity` | No | string | -- | `PUBLIC_ENDPOINT` or `VPC_ENDPOINT_SERVICE` |
| `--xks-proxy-authentication-credential` | No | structure | -- | New XKS proxy credentials |
| `--xks-proxy-vpc-endpoint-service-name` | No | string | -- | New VPC endpoint service name (20-64 chars) |

**Output:** None

---

### 7.6 `delete-custom-key-store`

Deletes a custom key store. Must be disconnected and contain no KMS keys.

**Synopsis:**
```bash
aws kms delete-custom-key-store --custom-key-store-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-key-store-id` | **Yes** | string | -- | Custom key store ID (1-64 chars) |

**Output:** None

---
