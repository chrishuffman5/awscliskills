# Instances

### 3.1 `register-instance`

Creates or updates an instance within a service. When you register an instance, Cloud Map creates DNS records and/or health checks based on the service configuration.

**Synopsis:**
```bash
aws servicediscovery register-instance \
    --service-id <value> \
    --instance-id <value> \
    --attributes <value> \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID or ARN (max 255 chars) |
| `--instance-id` | **Yes** | string | -- | Unique instance identifier (max 64 chars) |
| `--attributes` | **Yes** | map | -- | Instance attributes (see common attributes in index.md). Total size max 5000 chars |
| `--creator-request-id` | No | string | None | Idempotency token (max 64 chars) |

**Common Attributes:**

| Key | Description |
|-----|-------------|
| `AWS_INSTANCE_IPV4` | IPv4 address (required for A records) |
| `AWS_INSTANCE_IPV6` | IPv6 address (required for AAAA records) |
| `AWS_INSTANCE_PORT` | Port number (required for SRV records) |
| `AWS_INSTANCE_CNAME` | CNAME target (required for CNAME records) |
| `AWS_EC2_INSTANCE_ID` | EC2 instance ID (creates Route 53 alias) |
| `AWS_ALIAS_DNS_NAME` | Alias DNS name for Route 53 alias records |
| `AWS_INIT_HEALTH_STATUS` | Initial health: `HEALTHY` or `UNHEALTHY` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 3.2 `deregister-instance`

Deletes a registered instance and the associated DNS records and health checks.

**Synopsis:**
```bash
aws servicediscovery deregister-instance \
    --service-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID or ARN (max 255 chars) |
| `--instance-id` | **Yes** | string | -- | The instance ID (max 64 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 3.3 `get-instance`

Gets information about a specific instance.

**Synopsis:**
```bash
aws servicediscovery get-instance \
    --service-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID or ARN (max 255 chars) |
| `--instance-id` | **Yes** | string | -- | The instance ID (max 64 chars) |

**Output Schema:**
```json
{
    "Instance": {
        "Id": "string",
        "CreatorRequestId": "string",
        "Attributes": {"string": "string"}
    }
}
```

---

### 3.4 `list-instances`

Lists the instances registered with a service. **Paginated.**

**Synopsis:**
```bash
aws servicediscovery list-instances \
    --service-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID or ARN (max 255 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Instances": [
        {
            "Id": "string",
            "Attributes": {"string": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `get-instances-health-status`

Gets the health status for the instances registered with a service.

**Synopsis:**
```bash
aws servicediscovery get-instances-health-status \
    --service-id <value> \
    [--instances <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID or ARN (max 255 chars) |
| `--instances` | No | list(string) | None | Specific instance IDs to query (max 100) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Status": {
        "instance-id": "HEALTHY|UNHEALTHY|UNKNOWN"
    },
    "NextToken": "string"
}
```

---

### 3.6 `update-instance-custom-health-status`

Submits a health status update for a custom health check. Only works with services that have `HealthCheckCustomConfig`.

**Synopsis:**
```bash
aws servicediscovery update-instance-custom-health-status \
    --service-id <value> \
    --instance-id <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-id` | **Yes** | string | -- | The service ID (max 64 chars) |
| `--instance-id` | **Yes** | string | -- | The instance ID (max 64 chars) |
| `--status` | **Yes** | string | -- | The health status: `HEALTHY` or `UNHEALTHY` |

**Output Schema:**

No output on success.

---

### 3.7 `discover-instances`

Discovers instances registered with a namespace. This is the primary API for service discovery at runtime.

**Synopsis:**
```bash
aws servicediscovery discover-instances \
    --namespace-name <value> \
    --service-name <value> \
    [--max-results <value>] \
    [--query-parameters <value>] \
    [--optional-parameters <value>] \
    [--health-status <value>] \
    [--owner-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | The HttpName of the namespace (max 1024 chars) |
| `--service-name` | **Yes** | string | -- | The service name (1-127 chars) |
| `--max-results` | No | integer | 100 | Maximum instances to return (1-1000) |
| `--query-parameters` | No | map | None | Key-value pairs to filter by custom attributes (all must match) |
| `--optional-parameters` | No | map | None | Optional attribute filters |
| `--health-status` | No | string | None | Filter: `HEALTHY`, `UNHEALTHY`, `ALL`, or `HEALTHY_OR_ELSE_ALL` |
| `--owner-account` | No | string | None | Account ID for shared namespaces (12 digits) |

**Output Schema:**
```json
{
    "Instances": [
        {
            "InstanceId": "string",
            "NamespaceName": "string",
            "ServiceName": "string",
            "HealthStatus": "HEALTHY|UNHEALTHY|UNKNOWN",
            "Attributes": {"string": "string"}
        }
    ],
    "InstancesRevision": "long"
}
```

---

### 3.8 `discover-instances-revision`

Returns the revision number of instances discovered for a namespace and service, without returning the actual instances.

**Synopsis:**
```bash
aws servicediscovery discover-instances-revision \
    --namespace-name <value> \
    --service-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | The HttpName of the namespace (max 1024 chars) |
| `--service-name` | **Yes** | string | -- | The service name (1-127 chars) |

**Output Schema:**
```json
{
    "InstancesRevision": "long"
}
```
