# Services

### 2.1 `create-service`

Creates a service within a namespace. Services define how instances are discovered (via DNS, API, or both).

**Synopsis:**
```bash
aws servicediscovery create-service \
    --name <value> \
    [--namespace-id <value>] \
    [--description <value>] \
    [--dns-config <value>] \
    [--health-check-config <value>] \
    [--health-check-custom-config <value>] \
    [--tags <value>] \
    [--type <value>] \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The service name (1-127 chars) |
| `--namespace-id` | No | string | None | The namespace ID or ARN (max 255 chars) |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--dns-config` | No | structure | None | DNS configuration (see below) |
| `--health-check-config` | No | structure | None | Route 53 health check config (see below) |
| `--health-check-custom-config` | No | structure | None | Custom health check config (see below) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |
| `--type` | No | string | None | Service type. Use `HTTP` for API-only discovery |
| `--creator-request-id` | No | string | None | Idempotency token (max 64 chars) |

**dns-config Structure:**
```json
{
    "RoutingPolicy": "MULTIVALUE|WEIGHTED",
    "DnsRecords": [
        {"Type": "A|AAAA|SRV|CNAME", "TTL": "long"}
    ]
}
```

**health-check-config Structure:**
```json
{
    "Type": "HTTP|HTTPS|TCP",
    "ResourcePath": "string",
    "FailureThreshold": "integer (1-10)"
}
```

**health-check-custom-config Structure:**
```json
{
    "FailureThreshold": "integer (1-10)"
}
```

**Output Schema:**
```json
{
    "Service": {
        "Id": "string",
        "Arn": "string",
        "ResourceOwner": "string",
        "Name": "string",
        "NamespaceId": "string",
        "Description": "string",
        "InstanceCount": "integer",
        "DnsConfig": {
            "NamespaceId": "string",
            "RoutingPolicy": "MULTIVALUE|WEIGHTED",
            "DnsRecords": [{"Type": "string", "TTL": "long"}]
        },
        "Type": "HTTP|DNS_HTTP|DNS",
        "HealthCheckConfig": {
            "Type": "HTTP|HTTPS|TCP",
            "ResourcePath": "string",
            "FailureThreshold": "integer"
        },
        "HealthCheckCustomConfig": {"FailureThreshold": "integer"},
        "CreateDate": "timestamp",
        "CreatorRequestId": "string",
        "CreatedByAccount": "string"
    }
}
```

---

### 2.2 `delete-service`

Deletes a service. The service must have no registered instances.

**Synopsis:**
```bash
aws servicediscovery delete-service \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The service ID or ARN (max 255 chars) |

**Output Schema:**

No output on success.

---

### 2.3 `get-service`

Gets the settings for a specified service.

**Synopsis:**
```bash
aws servicediscovery get-service \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The service ID or ARN (max 255 chars) |

**Output Schema:**
Same as `create-service` output.

---

### 2.4 `list-services`

Lists all services in the account. **Paginated.**

**Synopsis:**
```bash
aws servicediscovery list-services \
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
| `--filters` | No | list | None | Filter by `NAMESPACE_ID` or `RESOURCE_OWNER`. Shorthand: `Name=string,Values=string,string,Condition=EQ\|IN\|BETWEEN\|BEGINS_WITH` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Services": [
        {
            "Id": "string",
            "Arn": "string",
            "ResourceOwner": "string",
            "Name": "string",
            "NamespaceId": "string",
            "Description": "string",
            "InstanceCount": "integer",
            "DnsConfig": {},
            "Type": "HTTP|DNS_HTTP|DNS",
            "HealthCheckConfig": {},
            "HealthCheckCustomConfig": {},
            "CreateDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-service`

Updates the settings for a service (description, DNS config, health check config).

**Synopsis:**
```bash
aws servicediscovery update-service \
    --id <value> \
    --service <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The service ID (max 64 chars) |
| `--service` | **Yes** | structure | -- | Updated service config. Contains `Description`, `DnsConfig`, and `HealthCheckConfig` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 2.6 `get-service-attributes`

Gets the custom attributes for a service.

**Synopsis:**
```bash
aws servicediscovery get-service-attributes \
    --service-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID (max 64 chars) |

**Output Schema:**
```json
{
    "ServiceAttributes": {
        "ServiceArn": "string",
        "Attributes": {"string": "string"}
    }
}
```

---

### 2.7 `update-service-attributes`

Updates custom attributes for a service.

**Synopsis:**
```bash
aws servicediscovery update-service-attributes \
    --service-id <value> \
    --attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID (max 64 chars) |
| `--attributes` | **Yes** | map | -- | Key-value pairs of custom attributes |

**Output Schema:**

No output on success.

---

### 2.8 `delete-service-attributes`

Deletes custom attributes from a service.

**Synopsis:**
```bash
aws servicediscovery delete-service-attributes \
    --service-id <value> \
    --attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID (max 64 chars) |
| `--attributes` | **Yes** | list(string) | -- | The attribute keys to delete |

**Output Schema:**

No output on success.
