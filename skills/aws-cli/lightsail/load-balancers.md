# Load Balancers

### 4.1 `create-load-balancer`

Creates a Lightsail load balancer.

**Synopsis:**
```bash
aws lightsail create-load-balancer \
    --load-balancer-name <value> \
    --instance-port <value> \
    [--health-check-path <value>] \
    [--certificate-name <value>] \
    [--certificate-domain-name <value>] \
    [--certificate-alternative-names <value>] \
    [--tags <value>] \
    [--ip-address-type <value>] \
    [--tls-policy-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name for the load balancer |
| `--instance-port` | **Yes** | integer | -- | Instance port (e.g., 80) |
| `--health-check-path` | No | string | `/` | Health check path |
| `--certificate-name` | No | string | None | TLS certificate name (enables HTTPS) |
| `--certificate-domain-name` | No | string | None | Domain for the TLS certificate |
| `--certificate-alternative-names` | No | list(string) | None | SAN domains for the TLS certificate |
| `--tags` | No | list | None | Tags |
| `--ip-address-type` | No | string | `dualstack` | IP address type: `dualstack`, `ipv4`, `ipv6` |
| `--tls-policy-name` | No | string | None | TLS security policy name |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "LoadBalancer",
            "operationType": "CreateLoadBalancer",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 4.2 `delete-load-balancer`

Deletes a Lightsail load balancer and all associated TLS certificates.

**Synopsis:**
```bash
aws lightsail delete-load-balancer \
    --load-balancer-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer to delete |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "LoadBalancer",
            "operationType": "DeleteLoadBalancer",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 4.3 `get-load-balancer`

Returns information about a specific load balancer.

**Synopsis:**
```bash
aws lightsail get-load-balancer \
    --load-balancer-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |

**Output Schema:**
```json
{
    "loadBalancer": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "LoadBalancer",
        "tags": [],
        "dnsName": "string",
        "state": "active|provisioning|active_impaired|failed|unknown",
        "protocol": "HTTP_HTTPS|HTTP",
        "publicPorts": ["integer"],
        "healthCheckPath": "string",
        "instancePort": "integer",
        "instanceHealthSummary": [
            {
                "instanceName": "string",
                "instanceHealth": "initial|healthy|unhealthy|unused|draining|unavailable",
                "instanceHealthReason": "string"
            }
        ],
        "tlsCertificateSummaries": [
            {
                "name": "string",
                "isAttached": true|false
            }
        ],
        "configurationOptions": {
            "string": "string"
        },
        "ipAddressType": "dualstack|ipv4|ipv6",
        "httpsRedirectionEnabled": true|false,
        "tlsPolicyName": "string"
    }
}
```

---

### 4.4 `get-load-balancers`

Returns information about all load balancers. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-load-balancers \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "loadBalancers": [
        {
            "name": "string",
            "arn": "string",
            "dnsName": "string",
            "state": "string",
            "instancePort": "integer",
            "healthCheckPath": "string"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 4.5 `get-load-balancer-metric-data`

Returns metric data for a load balancer.

**Synopsis:**
```bash
aws lightsail get-load-balancer-metric-data \
    --load-balancer-name <value> \
    --metric-name <value> \
    --period <value> \
    --start-time <value> \
    --end-time <value> \
    --unit <value> \
    --statistics <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--metric-name` | **Yes** | string | -- | Metric: `ClientTLSNegotiationErrorCount`, `HealthyHostCount`, `UnhealthyHostCount`, `HTTPCode_LB_4XX_Count`, `HTTPCode_LB_5XX_Count`, `HTTPCode_Instance_2XX_Count`, `HTTPCode_Instance_3XX_Count`, `HTTPCode_Instance_4XX_Count`, `HTTPCode_Instance_5XX_Count`, `InstanceResponseTime`, `RejectedConnectionCount`, `RequestCount` |
| `--period` | **Yes** | integer | -- | Granularity in seconds |
| `--start-time` | **Yes** | timestamp | -- | Start time |
| `--end-time` | **Yes** | timestamp | -- | End time |
| `--unit` | **Yes** | string | -- | Unit for the metric |
| `--statistics` | **Yes** | list(string) | -- | Statistics: `Minimum`, `Maximum`, `Sum`, `Average`, `SampleCount` |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricData": [
        {
            "average": "double",
            "maximum": "double",
            "minimum": "double",
            "sampleCount": "double",
            "sum": "double",
            "timestamp": "timestamp",
            "unit": "string"
        }
    ]
}
```

---

### 4.6 `attach-instances-to-load-balancer`

Attaches instances to a load balancer.

**Synopsis:**
```bash
aws lightsail attach-instances-to-load-balancer \
    --load-balancer-name <value> \
    --instance-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instance-names` | **Yes** | list(string) | -- | Instance names to attach |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "LoadBalancer",
            "operationType": "AttachInstancesToLoadBalancer",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 4.7 `detach-instances-from-load-balancer`

Detaches instances from a load balancer.

**Synopsis:**
```bash
aws lightsail detach-instances-from-load-balancer \
    --load-balancer-name <value> \
    --instance-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instance-names` | **Yes** | list(string) | -- | Instance names to detach |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "LoadBalancer",
            "operationType": "DetachInstancesFromLoadBalancer",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 4.8 `create-load-balancer-tls-certificate`

Creates a TLS certificate for a load balancer.

**Synopsis:**
```bash
aws lightsail create-load-balancer-tls-certificate \
    --load-balancer-name <value> \
    --certificate-name <value> \
    --certificate-domain-name <value> \
    [--certificate-alternative-names <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Load balancer name |
| `--certificate-name` | **Yes** | string | -- | Certificate name |
| `--certificate-domain-name` | **Yes** | string | -- | Primary domain |
| `--certificate-alternative-names` | No | list(string) | None | Subject alternative names |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "LoadBalancerTlsCertificate",
            "operationType": "CreateLoadBalancerTlsCertificate",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 4.9 `delete-load-balancer-tls-certificate`

Deletes a TLS certificate from a load balancer.

**Synopsis:**
```bash
aws lightsail delete-load-balancer-tls-certificate \
    --load-balancer-name <value> \
    --certificate-name <value> \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Load balancer name |
| `--certificate-name` | **Yes** | string | -- | Certificate name |
| `--force` | No | boolean | false | Force deletion even if in use |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "LoadBalancerTlsCertificate",
            "operationType": "DeleteLoadBalancerTlsCertificate",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 4.10 `attach-load-balancer-tls-certificate`

Attaches a TLS certificate to a load balancer (enables HTTPS).

**Synopsis:**
```bash
aws lightsail attach-load-balancer-tls-certificate \
    --load-balancer-name <value> \
    --certificate-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Load balancer name |
| `--certificate-name` | **Yes** | string | -- | Certificate name to attach |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "LoadBalancerTlsCertificate",
            "operationType": "AttachLoadBalancerTlsCertificate",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 4.11 `update-load-balancer-attribute`

Updates a load balancer attribute.

**Synopsis:**
```bash
aws lightsail update-load-balancer-attribute \
    --load-balancer-name <value> \
    --attribute-name <value> \
    --attribute-value <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Load balancer name |
| `--attribute-name` | **Yes** | string | -- | Attribute: `HealthCheckPath`, `SessionStickinessEnabled`, `SessionStickiness_LB_CookieDurationSeconds`, `HttpsRedirectionEnabled`, `TlsPolicyName` |
| `--attribute-value` | **Yes** | string | -- | Attribute value |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "LoadBalancer",
            "operationType": "UpdateLoadBalancerAttribute",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 4.12 `get-load-balancer-tls-certificates`

Returns TLS certificates for a specific load balancer.

**Synopsis:**
```bash
aws lightsail get-load-balancer-tls-certificates \
    --load-balancer-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Load balancer name |

**Output Schema:**
```json
{
    "tlsCertificates": [
        {
            "name": "string",
            "arn": "string",
            "supportCode": "string",
            "createdAt": "timestamp",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            },
            "resourceType": "LoadBalancerTlsCertificate",
            "tags": [],
            "loadBalancerName": "string",
            "isAttached": true|false,
            "status": "PENDING_VALIDATION|ISSUED|INACTIVE|EXPIRED|VALIDATION_TIMED_OUT|REVOKED|FAILED|UNKNOWN",
            "domainName": "string",
            "domainValidationRecords": [
                {
                    "name": "string",
                    "type": "string",
                    "value": "string",
                    "validationStatus": "PENDING_VALIDATION|FAILED|SUCCESS",
                    "domainName": "string",
                    "dnsRecordCreationState": {
                        "code": "SUCCEEDED|STARTED|FAILED",
                        "message": "string"
                    }
                }
            ],
            "subject": "string",
            "issuer": "string",
            "notBefore": "timestamp",
            "notAfter": "timestamp",
            "subjectAlternativeNames": ["string"],
            "serial": "string",
            "signatureAlgorithm": "string"
        }
    ]
}
```

---

### 4.13 `get-load-balancer-tls-policies`

Returns available TLS security policies for load balancers.

**Synopsis:**
```bash
aws lightsail get-load-balancer-tls-policies \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "tlsPolicies": [
        {
            "name": "string",
            "isDefault": true|false,
            "description": "string",
            "protocols": ["string"],
            "ciphers": ["string"]
        }
    ],
    "nextPageToken": "string"
}
```
