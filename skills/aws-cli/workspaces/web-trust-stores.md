# Web Trust Stores

> Commands use `aws workspaces-web` CLI prefix.

### 13.1 `create-trust-store`

Creates a trust store resource that holds CA certificates for verifying server certificates.

**Synopsis:**
```bash
aws workspaces-web create-trust-store \
    --certificate-list <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-list` | **Yes** | list(blob) | -- | List of CA certificates (PEM-encoded, base64) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "trustStoreArn": "string"
}
```

---

### 13.2 `delete-trust-store`

Deletes a trust store.

**Synopsis:**
```bash
aws workspaces-web delete-trust-store \
    --trust-store-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | The ARN of the trust store to delete |

**Output Schema:**
```json
{}
```

---

### 13.3 `get-trust-store`

Gets a trust store.

**Synopsis:**
```bash
aws workspaces-web get-trust-store \
    --trust-store-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | The ARN of the trust store |

**Output Schema:**
```json
{
    "trustStore": {
        "trustStoreArn": "string",
        "associatedPortalArns": ["string"]
    }
}
```

---

### 13.4 `list-trust-stores`

Lists trust stores. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces-web list-trust-stores \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "trustStores": [
        {
            "trustStoreArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 13.5 `update-trust-store`

Updates a trust store.

**Synopsis:**
```bash
aws workspaces-web update-trust-store \
    --trust-store-arn <value> \
    [--certificates-to-add <value>] \
    [--certificates-to-delete <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | The ARN of the trust store to update |
| `--certificates-to-add` | No | list(blob) | None | Certificates to add (PEM-encoded, base64) |
| `--certificates-to-delete` | No | list(string) | None | Certificate thumbprints to delete |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "trustStoreArn": "string"
}
```

---

### 13.6 `associate-trust-store`

Associates a trust store with a web portal.

**Synopsis:**
```bash
aws workspaces-web associate-trust-store \
    --portal-arn <value> \
    --trust-store-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal |
| `--trust-store-arn` | **Yes** | string | -- | The ARN of the trust store |

**Output Schema:**
```json
{
    "portalArn": "string",
    "trustStoreArn": "string"
}
```

---

### 13.7 `disassociate-trust-store`

Disassociates a trust store from a web portal.

**Synopsis:**
```bash
aws workspaces-web disassociate-trust-store \
    --portal-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal to disassociate from |

**Output Schema:**
```json
{}
```
