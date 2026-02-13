# Health Checks

### 3.1 `create-health-check`

Creates a health check that monitors an endpoint, other health checks (calculated), or a CloudWatch alarm.

**Synopsis:**
```bash
aws route53 create-health-check \
    --caller-reference <value> \
    --health-check-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--caller-reference` | **Yes** | string | -- | Unique string for retry safety (1-64 chars) |
| `--health-check-config` | **Yes** | structure | -- | Health check configuration. Supports `file://` syntax |

**Health Check Config Structure:**
```json
{
    "IPAddress": "string",
    "Port": "integer",
    "Type": "HTTP|HTTPS|HTTP_STR_MATCH|HTTPS_STR_MATCH|TCP|CALCULATED|CLOUDWATCH_METRIC|RECOVERY_CONTROL",
    "ResourcePath": "string",
    "FullyQualifiedDomainName": "string",
    "SearchString": "string",
    "RequestInterval": "integer",
    "FailureThreshold": "integer",
    "MeasureLatency": true|false,
    "Inverted": true|false,
    "Disabled": true|false,
    "HealthThreshold": "integer",
    "ChildHealthChecks": ["string"],
    "EnableSNI": true|false,
    "Regions": ["string"],
    "AlarmIdentifier": {
        "Region": "string",
        "Name": "string"
    },
    "InsufficientDataHealthStatus": "Healthy|Unhealthy|LastKnownStatus",
    "RoutingControlArn": "string"
}
```

**Health Check Config Field Constraints:**

| Field | Constraints |
|-------|-------------|
| `IPAddress` | Max 45 chars (IPv4 or IPv6) |
| `Port` | 1-65535 |
| `Type` | **Required** |
| `ResourcePath` | Max 255 chars |
| `FullyQualifiedDomainName` | Max 255 chars |
| `SearchString` | Max 255 chars (first 5120 bytes of response body searched) |
| `RequestInterval` | 10 or 30 (default 30). 10-second intervals cost extra |
| `FailureThreshold` | 1-10 (default 3) |
| `HealthThreshold` | 0-256 (for CALCULATED type) |
| `ChildHealthChecks` | Max 256 items (for CALCULATED type) |
| `Regions` | Min 3, max 64. Values: `us-east-1`, `us-west-1`, `us-west-2`, `eu-west-1`, `ap-southeast-1`, `ap-southeast-2`, `ap-northeast-1`, `sa-east-1` |
| `RoutingControlArn` | 1-255 chars (for RECOVERY_CONTROL type) |

**Output Schema:**
```json
{
    "HealthCheck": {
        "Id": "string",
        "CallerReference": "string",
        "LinkedService": {
            "ServicePrincipal": "string",
            "Description": "string"
        },
        "HealthCheckConfig": {
            "IPAddress": "string",
            "Port": "integer",
            "Type": "string",
            "ResourcePath": "string",
            "FullyQualifiedDomainName": "string",
            "SearchString": "string",
            "RequestInterval": "integer",
            "FailureThreshold": "integer",
            "MeasureLatency": true|false,
            "Inverted": true|false,
            "Disabled": true|false,
            "HealthThreshold": "integer",
            "ChildHealthChecks": ["string"],
            "EnableSNI": true|false,
            "Regions": ["string"],
            "AlarmIdentifier": {
                "Region": "string",
                "Name": "string"
            },
            "InsufficientDataHealthStatus": "string",
            "RoutingControlArn": "string"
        },
        "HealthCheckVersion": "long",
        "CloudWatchAlarmConfiguration": {
            "EvaluationPeriods": "integer",
            "Threshold": "double",
            "ComparisonOperator": "GreaterThanOrEqualToThreshold|GreaterThanThreshold|LessThanThreshold|LessThanOrEqualToThreshold",
            "Period": "integer",
            "MetricName": "string",
            "Namespace": "string",
            "Statistic": "Average|Sum|SampleCount|Maximum|Minimum",
            "Dimensions": [
                {
                    "Name": "string",
                    "Value": "string"
                }
            ]
        }
    },
    "Location": "string"
}
```

---

### 3.2 `delete-health-check`

Deletes a health check. Route 53 does not prevent deletion of health checks associated with records; DNS failover may stop working.

**Synopsis:**
```bash
aws route53 delete-health-check \
    --health-check-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--health-check-id` | **Yes** | string | -- | Health check ID (max 64 chars) |

**Output:** None on success.

---

### 3.3 `get-health-check`

Gets information about a specified health check.

**Synopsis:**
```bash
aws route53 get-health-check \
    --health-check-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--health-check-id` | **Yes** | string | -- | Health check ID (max 64 chars) |

**Output Schema:**
```json
{
    "HealthCheck": {
        "Id": "string",
        "CallerReference": "string",
        "LinkedService": {
            "ServicePrincipal": "string",
            "Description": "string"
        },
        "HealthCheckConfig": { "..." },
        "HealthCheckVersion": "long",
        "CloudWatchAlarmConfiguration": { "..." }
    }
}
```

---

### 3.4 `list-health-checks`

Lists all health checks in the account. **Paginated operation.**

**Synopsis:**
```bash
aws route53 list-health-checks \
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
| `--page-size` | No | string | None | Items per API call |
| `--max-items` | No | string | None | Total items to return |

**Output Schema:**
```json
{
    "HealthChecks": [
        {
            "Id": "string",
            "CallerReference": "string",
            "LinkedService": {
                "ServicePrincipal": "string",
                "Description": "string"
            },
            "HealthCheckConfig": { "..." },
            "HealthCheckVersion": "long",
            "CloudWatchAlarmConfiguration": { "..." }
        }
    ],
    "Marker": "string",
    "IsTruncated": true|false,
    "NextMarker": "string",
    "MaxItems": "string"
}
```

---

### 3.5 `update-health-check`

Updates an existing health check. You cannot change the `Type` after creation.

**Synopsis:**
```bash
aws route53 update-health-check \
    --health-check-id <value> \
    [--health-check-version <value>] \
    [--ip-address <value>] \
    [--port <value>] \
    [--resource-path <value>] \
    [--fully-qualified-domain-name <value>] \
    [--search-string <value>] \
    [--failure-threshold <value>] \
    [--inverted | --no-inverted] \
    [--disabled | --no-disabled] \
    [--health-threshold <value>] \
    [--child-health-checks <value>] \
    [--enable-sni | --no-enable-sni] \
    [--regions <value>] \
    [--alarm-identifier <value>] \
    [--insufficient-data-health-status <value>] \
    [--reset-elements <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--health-check-id` | **Yes** | string | -- | Health check ID (max 64 chars) |
| `--health-check-version` | No | long | None | Version counter for optimistic locking (min 1) |
| `--ip-address` | No | string | None | Endpoint IP (max 45 chars) |
| `--port` | No | integer | None | Endpoint port (1-65535) |
| `--resource-path` | No | string | None | URL path (max 255 chars) |
| `--fully-qualified-domain-name` | No | string | None | Endpoint FQDN (max 255 chars) |
| `--search-string` | No | string | None | Response body search string (max 255 chars) |
| `--failure-threshold` | No | integer | None | Consecutive failures to trigger (1-10) |
| `--inverted` / `--no-inverted` | No | boolean | None | Invert health check status |
| `--disabled` / `--no-disabled` | No | boolean | None | Disable health check |
| `--health-threshold` | No | integer | None | Healthy child count for CALCULATED (0-256) |
| `--child-health-checks` | No | list(string) | None | Child health check IDs (max 256) |
| `--enable-sni` / `--no-enable-sni` | No | boolean | None | Send FQDN in TLS handshake |
| `--regions` | No | list(string) | None | Health checker regions (min 3, max 64) |
| `--alarm-identifier` | No | structure | None | CloudWatch alarm: `Region=string,Name=string` |
| `--insufficient-data-health-status` | No | string | None | `Healthy`, `Unhealthy`, `LastKnownStatus` |
| `--reset-elements` | No | list(string) | None | Elements to reset: `FullyQualifiedDomainName`, `Regions`, `ResourcePath`, `ChildHealthChecks` |

**Output Schema:**
```json
{
    "HealthCheck": {
        "Id": "string",
        "CallerReference": "string",
        "LinkedService": {
            "ServicePrincipal": "string",
            "Description": "string"
        },
        "HealthCheckConfig": { "..." },
        "HealthCheckVersion": "long",
        "CloudWatchAlarmConfiguration": { "..." }
    }
}
```

---

### 3.6 `get-health-check-status`

Gets the current status from each Route 53 health checker region.

**Synopsis:**
```bash
aws route53 get-health-check-status \
    --health-check-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--health-check-id` | **Yes** | string | -- | Health check ID (max 64 chars) |

**Output Schema:**
```json
{
    "HealthCheckObservations": [
        {
            "Region": "string",
            "IPAddress": "string",
            "StatusReport": {
                "Status": "string",
                "CheckedTime": "timestamp"
            }
        }
    ]
}
```

---

### 3.7 `get-health-check-last-failure-reason`

Gets the reason for the most recent failure of each health checker region.

**Synopsis:**
```bash
aws route53 get-health-check-last-failure-reason \
    --health-check-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--health-check-id` | **Yes** | string | -- | Health check ID (max 64 chars) |

**Output Schema:**
```json
{
    "HealthCheckObservations": [
        {
            "Region": "string",
            "IPAddress": "string",
            "StatusReport": {
                "Status": "string",
                "CheckedTime": "timestamp"
            }
        }
    ]
}
```

---

### 3.8 `get-health-check-count`

Returns the total number of health checks in the account.

**Synopsis:**
```bash
aws route53 get-health-check-count \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (only global options).

**Output Schema:**
```json
{
    "HealthCheckCount": "long"
}
```

---

### 3.9 `get-checker-ip-ranges`

Gets the IP ranges used by Route 53 health checkers. Useful for firewall allowlisting.

**Synopsis:**
```bash
aws route53 get-checker-ip-ranges \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (only global options).

**Output Schema:**
```json
{
    "CheckerIpRanges": ["string"]
}
```

---
