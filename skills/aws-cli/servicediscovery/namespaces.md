# Namespaces

### 1.1 `create-http-namespace`

Creates an HTTP namespace. Services registered in HTTP namespaces can only be discovered using the `discover-instances` API.

**Synopsis:**
```bash
aws servicediscovery create-http-namespace \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The namespace name (max 1024 chars) |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |
| `--creator-request-id` | No | string | None | Idempotency token (max 64 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 1.2 `create-private-dns-namespace`

Creates a private DNS namespace backed by a Route 53 private hosted zone. Services in this namespace can be discovered via DNS and the `discover-instances` API.

**Synopsis:**
```bash
aws servicediscovery create-private-dns-namespace \
    --name <value> \
    --vpc <value> \
    [--description <value>] \
    [--tags <value>] \
    [--properties <value>] \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The namespace name (max 253 chars, e.g., `example.local`) |
| `--vpc` | **Yes** | string | -- | The VPC ID to associate with the namespace (max 64 chars) |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--properties` | No | structure | None | DNS properties. Shorthand: `DnsProperties={SOA={TTL=long}}` |
| `--creator-request-id` | No | string | None | Idempotency token (max 64 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 1.3 `create-public-dns-namespace`

Creates a public DNS namespace backed by a Route 53 public hosted zone. Services can be discovered via DNS or the `discover-instances` API.

**Synopsis:**
```bash
aws servicediscovery create-public-dns-namespace \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--properties <value>] \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The namespace name (max 253 chars, e.g., `example.com`) |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--properties` | No | structure | None | DNS properties. Shorthand: `DnsProperties={SOA={TTL=long}}` |
| `--creator-request-id` | No | string | None | Idempotency token (max 64 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 1.4 `delete-namespace`

Deletes a namespace. The namespace must have no services.

**Synopsis:**
```bash
aws servicediscovery delete-namespace \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The namespace ID or ARN (max 255 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 1.5 `get-namespace`

Gets information about a namespace.

**Synopsis:**
```bash
aws servicediscovery get-namespace \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The namespace ID or ARN (max 255 chars) |

**Output Schema:**
```json
{
    "Namespace": {
        "Id": "string",
        "Arn": "string",
        "ResourceOwner": "string",
        "Name": "string",
        "Type": "DNS_PUBLIC|DNS_PRIVATE|HTTP",
        "Description": "string",
        "ServiceCount": "integer",
        "Properties": {
            "DnsProperties": {
                "HostedZoneId": "string",
                "SOA": {"TTL": "long"}
            },
            "HttpProperties": {
                "HttpName": "string"
            }
        },
        "CreateDate": "timestamp",
        "CreatorRequestId": "string"
    }
}
```

---

### 1.6 `list-namespaces`

Lists all namespaces in the account. **Paginated.**

**Synopsis:**
```bash
aws servicediscovery list-namespaces \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filter by `TYPE`, `NAME`, `HTTP_NAME`, or `RESOURCE_OWNER`. Shorthand: `Name=string,Values=string,string,Condition=EQ\|IN\|BETWEEN\|BEGINS_WITH` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Namespaces": [
        {
            "Id": "string",
            "Arn": "string",
            "ResourceOwner": "string",
            "Name": "string",
            "Type": "DNS_PUBLIC|DNS_PRIVATE|HTTP",
            "Description": "string",
            "ServiceCount": "integer",
            "Properties": {
                "DnsProperties": {"HostedZoneId": "string", "SOA": {"TTL": "long"}},
                "HttpProperties": {"HttpName": "string"}
            },
            "CreateDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.7 `update-http-namespace`

Updates an HTTP namespace description.

**Synopsis:**
```bash
aws servicediscovery update-http-namespace \
    --id <value> \
    --namespace <value> \
    [--updater-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The namespace ID (max 64 chars) |
| `--namespace` | **Yes** | structure | -- | Updated properties. Shorthand: `Description=string` |
| `--updater-request-id` | No | string | None | Idempotency token (max 64 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 1.8 `update-private-dns-namespace`

Updates a private DNS namespace description and SOA TTL.

**Synopsis:**
```bash
aws servicediscovery update-private-dns-namespace \
    --id <value> \
    --namespace <value> \
    [--updater-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The namespace ID (max 64 chars) |
| `--namespace` | **Yes** | structure | -- | Updated properties. Shorthand: `Description=string,Properties={DnsProperties={SOA={TTL=long}}}` |
| `--updater-request-id` | No | string | None | Idempotency token (max 64 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 1.9 `update-public-dns-namespace`

Updates a public DNS namespace description and SOA TTL.

**Synopsis:**
```bash
aws servicediscovery update-public-dns-namespace \
    --id <value> \
    --namespace <value> \
    [--updater-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The namespace ID (max 64 chars) |
| `--namespace` | **Yes** | structure | -- | Updated properties. Shorthand: `Description=string,Properties={DnsProperties={SOA={TTL=long}}}` |
| `--updater-request-id` | No | string | None | Idempotency token (max 64 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```
