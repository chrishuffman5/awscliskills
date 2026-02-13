# Endpoint Groups

### 3.1 `create-endpoint-group`

Creates an endpoint group for a listener. Each listener can have one endpoint group per AWS Region.

**Synopsis:**
```bash
aws globalaccelerator create-endpoint-group \
    --listener-arn <value> \
    --endpoint-group-region <value> \
    [--endpoint-configurations <value>] \
    [--traffic-dial-percentage <value>] \
    [--health-check-port <value>] \
    [--health-check-protocol <value>] \
    [--health-check-path <value>] \
    [--health-check-interval-seconds <value>] \
    [--threshold-count <value>] \
    [--idempotency-token <value>] \
    [--port-overrides <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--endpoint-group-region` | **Yes** | string | -- | AWS Region for the endpoint group |
| `--endpoint-configurations` | No | list | None | Endpoint objects (0-10). Shorthand: `EndpointId=string,Weight=integer,ClientIPPreservationEnabled=boolean,AttachmentArn=string ...` |
| `--traffic-dial-percentage` | No | float | 100 | Percentage of traffic to this region (0-100) |
| `--health-check-port` | No | integer | listener port | Port for health checks (1-65535) |
| `--health-check-protocol` | No | string | `TCP` | Health check protocol: `TCP`, `HTTP`, `HTTPS` |
| `--health-check-path` | No | string | `/` | Path for HTTP/HTTPS health checks |
| `--health-check-interval-seconds` | No | integer | 30 | Time between health checks: `10` or `30` seconds |
| `--threshold-count` | No | integer | 3 | Consecutive checks to change endpoint state (1-10) |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--port-overrides` | No | list | None | Port mappings (0-10). Shorthand: `ListenerPort=integer,EndpointPort=integer ...` |

**Endpoint Configuration Fields:**

| Field | Type | Description |
|-------|------|-------------|
| `EndpointId` | string | ARN (ALB/NLB), Elastic IP allocation ID, or EC2 instance ID |
| `Weight` | integer | Traffic proportion weight (0-255) |
| `ClientIPPreservationEnabled` | boolean | Preserve client IP (default true for ALB) |
| `AttachmentArn` | string | Cross-account attachment ARN |

**Output Schema:**
```json
{
    "EndpointGroup": {
        "EndpointGroupArn": "string",
        "EndpointGroupRegion": "string",
        "EndpointDescriptions": [
            {
                "EndpointId": "string",
                "Weight": "integer",
                "HealthState": "INITIAL|HEALTHY|UNHEALTHY",
                "HealthReason": "string",
                "ClientIPPreservationEnabled": "boolean"
            }
        ],
        "TrafficDialPercentage": "float",
        "HealthCheckPort": "integer",
        "HealthCheckProtocol": "TCP|HTTP|HTTPS",
        "HealthCheckPath": "string",
        "HealthCheckIntervalSeconds": "integer",
        "ThresholdCount": "integer",
        "PortOverrides": [
            {
                "ListenerPort": "integer",
                "EndpointPort": "integer"
            }
        ]
    }
}
```

---

### 3.2 `delete-endpoint-group`

Deletes an endpoint group.

**Synopsis:**
```bash
aws globalaccelerator delete-endpoint-group \
    --endpoint-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group to delete |

**Output:** None on success.

---

### 3.3 `describe-endpoint-group`

Gets details about an endpoint group.

**Synopsis:**
```bash
aws globalaccelerator describe-endpoint-group \
    --endpoint-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |

**Output Schema:** Same as `create-endpoint-group`.

---

### 3.4 `list-endpoint-groups`

Lists endpoint groups for a listener. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-endpoint-groups \
    --listener-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EndpointGroups": [
        {
            "EndpointGroupArn": "string",
            "EndpointGroupRegion": "string",
            "EndpointDescriptions": [],
            "TrafficDialPercentage": "float",
            "HealthCheckPort": "integer",
            "HealthCheckProtocol": "string",
            "HealthCheckPath": "string",
            "HealthCheckIntervalSeconds": "integer",
            "ThresholdCount": "integer",
            "PortOverrides": []
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-endpoint-group`

Updates endpoint group settings.

**Synopsis:**
```bash
aws globalaccelerator update-endpoint-group \
    --endpoint-group-arn <value> \
    [--endpoint-configurations <value>] \
    [--traffic-dial-percentage <value>] \
    [--health-check-port <value>] \
    [--health-check-protocol <value>] \
    [--health-check-path <value>] \
    [--health-check-interval-seconds <value>] \
    [--threshold-count <value>] \
    [--port-overrides <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |
| `--endpoint-configurations` | No | list | None | Updated endpoint list |
| `--traffic-dial-percentage` | No | float | None | Traffic percentage (0-100) |
| `--health-check-port` | No | integer | None | Health check port |
| `--health-check-protocol` | No | string | None | `TCP`, `HTTP`, `HTTPS` |
| `--health-check-path` | No | string | None | Health check path |
| `--health-check-interval-seconds` | No | integer | None | `10` or `30` seconds |
| `--threshold-count` | No | integer | None | Consecutive checks (1-10) |
| `--port-overrides` | No | list | None | Port mapping overrides |

**Output Schema:** Same as `create-endpoint-group`.

---

### 3.6 `add-endpoints`

Adds endpoints to an existing endpoint group.

**Synopsis:**
```bash
aws globalaccelerator add-endpoints \
    --endpoint-configurations <value> \
    --endpoint-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-configurations` | **Yes** | list | -- | Endpoints to add (0-10) |
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |

**Output Schema:**
```json
{
    "EndpointDescriptions": [
        {
            "EndpointId": "string",
            "Weight": "integer",
            "HealthState": "INITIAL|HEALTHY|UNHEALTHY",
            "HealthReason": "string",
            "ClientIPPreservationEnabled": "boolean"
        }
    ],
    "EndpointGroupArn": "string"
}
```

---

### 3.7 `remove-endpoints`

Removes endpoints from an endpoint group.

**Synopsis:**
```bash
aws globalaccelerator remove-endpoints \
    --endpoint-identifiers <value> \
    --endpoint-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-identifiers` | **Yes** | list | -- | Endpoints to remove. Shorthand: `EndpointId=string,ClientIPPreservationEnabled=boolean ...` |
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |

**Output:** None on success.
