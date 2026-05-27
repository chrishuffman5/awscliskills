# Target Groups

### 2.1 `create-target-group`

Creates a target group. Target groups route requests to registered targets.

**Synopsis:**
```bash
aws elbv2 create-target-group \
    --name <value> \
    [--protocol <value>] \
    [--protocol-version <value>] \
    [--port <value>] \
    [--vpc-id <value>] \
    [--health-check-protocol <value>] \
    [--health-check-port <value>] \
    [--health-check-enabled | --no-health-check-enabled] \
    [--health-check-path <value>] \
    [--health-check-interval-seconds <value>] \
    [--health-check-timeout-seconds <value>] \
    [--healthy-threshold-count <value>] \
    [--unhealthy-threshold-count <value>] \
    [--matcher <value>] \
    [--target-type <value>] \
    [--tags <value>] \
    [--ip-address-type <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Target group name. Max 32 chars, alphanumeric and hyphens |
| `--protocol` | No | string | -- | Values: `HTTP`, `HTTPS`, `TCP`, `TLS`, `UDP`, `TCP_UDP`, `GENEVE` |
| `--protocol-version` | No | string | `HTTP1` | Values: `HTTP1`, `HTTP2`, `GRPC` (HTTP/HTTPS only) |
| `--port` | No | integer | -- | Port for targets (1-65535) |
| `--vpc-id` | No | string | -- | VPC ID. Required unless target type is `lambda` |
| `--health-check-protocol` | No | string | `HTTP` (ALB), `TCP` (NLB) | Values: `HTTP`, `HTTPS`, `TCP`, `TLS` |
| `--health-check-port` | No | string | `traffic-port` | Port for health checks |
| `--health-check-enabled` | No | boolean | `true` | Enable/disable health checks |
| `--health-check-path` | No | string | `/` | Path for HTTP/HTTPS health checks (1-1024 chars) |
| `--health-check-interval-seconds` | No | integer | `30` | Interval between checks (5-300 seconds) |
| `--health-check-timeout-seconds` | No | integer | `6` (HTTP), `10` (TCP) | Timeout for check response (2-120 seconds) |
| `--healthy-threshold-count` | No | integer | `5` | Consecutive successes before healthy (2-10) |
| `--unhealthy-threshold-count` | No | integer | `2` | Consecutive failures before unhealthy (2-10) |
| `--matcher` | No | structure | `HttpCode=200` | Success codes. Shorthand: `HttpCode=string,GrpcCode=string` |
| `--target-type` | No | string | `instance` | Values: `instance`, `ip`, `lambda`, `alb` |
| `--tags` | No | list | None | Key-value tags |
| `--ip-address-type` | No | string | `ipv4` | Values: `ipv4`, `ipv6` |

**Output Schema:**
```json
{
    "TargetGroups": [
        {
            "TargetGroupArn": "string",
            "TargetGroupName": "string",
            "Protocol": "HTTP|HTTPS|TCP|TLS|UDP|TCP_UDP|GENEVE",
            "Port": integer,
            "VpcId": "string",
            "HealthCheckProtocol": "HTTP|HTTPS|TCP|TLS",
            "HealthCheckPort": "string",
            "HealthCheckEnabled": true|false,
            "HealthCheckIntervalSeconds": integer,
            "HealthCheckTimeoutSeconds": integer,
            "HealthyThresholdCount": integer,
            "UnhealthyThresholdCount": integer,
            "HealthCheckPath": "string",
            "Matcher": {
                "HttpCode": "string",
                "GrpcCode": "string"
            },
            "LoadBalancerArns": ["string"],
            "TargetType": "instance|ip|lambda|alb",
            "ProtocolVersion": "HTTP1|HTTP2|GRPC",
            "IpAddressType": "ipv4|ipv6"
        }
    ]
}
```

---

### 2.2 `delete-target-group`

Deletes the specified target group. Cannot delete a target group if it is referenced by any listener rules or if targets are still registered.

**Synopsis:**
```bash
aws elbv2 delete-target-group \
    --target-group-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-group-arn` | **Yes** | string | -- | ARN of the target group |

**Output Schema:** None (no output on success).

---

### 2.3 `describe-target-groups`

Describes the specified target groups or all target groups. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-target-groups \
    [--load-balancer-arn <value>] \
    [--target-group-arns <value>] \
    [--names <value>] \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | No | string | -- | ARN of the load balancer to filter by |
| `--target-group-arns` | No | list | -- | ARNs of target groups (max 20) |
| `--names` | No | list | -- | Names of target groups |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "TargetGroups": [
        {
            "TargetGroupArn": "string",
            "TargetGroupName": "string",
            "Protocol": "HTTP|HTTPS|TCP|TLS|UDP|TCP_UDP|GENEVE",
            "Port": integer,
            "VpcId": "string",
            "HealthCheckProtocol": "string",
            "HealthCheckPort": "string",
            "HealthCheckEnabled": true|false,
            "HealthCheckIntervalSeconds": integer,
            "HealthCheckTimeoutSeconds": integer,
            "HealthyThresholdCount": integer,
            "UnhealthyThresholdCount": integer,
            "HealthCheckPath": "string",
            "Matcher": {
                "HttpCode": "string",
                "GrpcCode": "string"
            },
            "LoadBalancerArns": ["string"],
            "TargetType": "instance|ip|lambda|alb",
            "ProtocolVersion": "HTTP1|HTTP2|GRPC",
            "IpAddressType": "ipv4|ipv6"
        }
    ],
    "NextMarker": "string"
}
```

---

### 2.4 `modify-target-group`

Modifies the health checks used for the targets in a target group.

**Synopsis:**
```bash
aws elbv2 modify-target-group \
    --target-group-arn <value> \
    [--health-check-protocol <value>] \
    [--health-check-port <value>] \
    [--health-check-path <value>] \
    [--health-check-enabled | --no-health-check-enabled] \
    [--health-check-interval-seconds <value>] \
    [--health-check-timeout-seconds <value>] \
    [--healthy-threshold-count <value>] \
    [--unhealthy-threshold-count <value>] \
    [--matcher <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-group-arn` | **Yes** | string | -- | ARN of the target group |
| `--health-check-protocol` | No | string | -- | Values: `HTTP`, `HTTPS`, `TCP`, `TLS` |
| `--health-check-port` | No | string | -- | Port for health checks |
| `--health-check-path` | No | string | -- | Path for HTTP/HTTPS health checks (1-1024 chars) |
| `--health-check-enabled` | No | boolean | -- | Enable/disable health checks |
| `--health-check-interval-seconds` | No | integer | -- | Interval between checks (5-300 seconds) |
| `--health-check-timeout-seconds` | No | integer | -- | Timeout for check response (2-120 seconds) |
| `--healthy-threshold-count` | No | integer | -- | Consecutive successes before healthy (2-10) |
| `--unhealthy-threshold-count` | No | integer | -- | Consecutive failures before unhealthy (2-10) |
| `--matcher` | No | structure | -- | Success codes. Shorthand: `HttpCode=string,GrpcCode=string` |

**Output Schema:**
```json
{
    "TargetGroups": [
        {
            "TargetGroupArn": "string",
            "TargetGroupName": "string",
            "Protocol": "string",
            "Port": integer,
            "VpcId": "string",
            "HealthCheckProtocol": "string",
            "HealthCheckPort": "string",
            "HealthCheckEnabled": true|false,
            "HealthCheckIntervalSeconds": integer,
            "HealthCheckTimeoutSeconds": integer,
            "HealthyThresholdCount": integer,
            "UnhealthyThresholdCount": integer,
            "HealthCheckPath": "string",
            "Matcher": {
                "HttpCode": "string",
                "GrpcCode": "string"
            },
            "LoadBalancerArns": ["string"],
            "TargetType": "instance|ip|lambda|alb",
            "ProtocolVersion": "HTTP1|HTTP2|GRPC",
            "IpAddressType": "ipv4|ipv6"
        }
    ]
}
```

---

### 2.5 `modify-target-group-attributes`

Modifies the specified attributes of the specified target group.

**Synopsis:**
```bash
aws elbv2 modify-target-group-attributes \
    --target-group-arn <value> \
    --attributes <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-group-arn` | **Yes** | string | -- | ARN of the target group |
| `--attributes` | **Yes** | list | -- | Attributes to modify. Shorthand: `Key=string,Value=string ...` |

**Common Target Group Attribute Keys:**

| Key | Default | Description |
|-----|---------|-------------|
| `deregistration_delay.timeout_seconds` | `300` | Deregistration delay (0-3600 seconds) |
| `stickiness.enabled` | `false` | Enable sticky sessions |
| `stickiness.type` | `lb_cookie` | Values: `lb_cookie`, `app_cookie`, `source_ip`, `source_ip_dest_ip`, `source_ip_dest_ip_proto` |
| `stickiness.lb_cookie.duration_seconds` | `86400` | Cookie duration (1-604800 seconds) |
| `stickiness.app_cookie.cookie_name` | -- | Application cookie name |
| `stickiness.app_cookie.duration_seconds` | `86400` | Cookie duration (1-604800 seconds) |
| `slow_start.duration_seconds` | `0` | Slow start duration (0 or 30-900 seconds) |
| `load_balancing.algorithm.type` | `round_robin` | Values: `round_robin`, `least_outstanding_requests`, `weighted_random` |
| `target_group_health.dns_failover.minimum_healthy_targets.count` | `1` | Minimum healthy targets for DNS failover |
| `target_group_health.dns_failover.minimum_healthy_targets.percentage` | `off` | Minimum healthy percentage for DNS failover |
| `target_group_health.unhealthy_state_routing.minimum_healthy_targets.count` | `1` | Minimum healthy for routing failover |
| `preserve_client_ip.enabled` | `true` (NLB) | Preserve client IP |
| `proxy_protocol_v2.enabled` | `false` | Enable proxy protocol v2 (NLB) |
| `deregistration_delay.connection_termination.enabled` | `false` | Terminate connections on deregistration (NLB) |
| `lambda.multi_value_headers.enabled` | `false` | Enable multi-value headers (Lambda targets) |

**Output Schema:**
```json
{
    "Attributes": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 2.6 `describe-target-group-attributes`

Describes the attributes for the specified target group.

**Synopsis:**
```bash
aws elbv2 describe-target-group-attributes \
    --target-group-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-group-arn` | **Yes** | string | -- | ARN of the target group |

**Output Schema:**
```json
{
    "Attributes": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 2.7 `register-targets`

Registers the specified targets with the specified target group.

**Synopsis:**
```bash
aws elbv2 register-targets \
    --target-group-arn <value> \
    --targets <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-group-arn` | **Yes** | string | -- | ARN of the target group |
| `--targets` | **Yes** | list | -- | Targets to register. Shorthand: `Id=string,Port=integer,AvailabilityZone=string ...` |

**Target Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Id` | **Yes** | string | Instance ID, IP address, Lambda ARN, or ALB ARN |
| `Port` | No | integer | Port (1-65535). Not used for Lambda targets |
| `AvailabilityZone` | No | string | AZ or `all`. For IP and Lambda targets |

**Output Schema:** None (no output on success).

---

### 2.8 `deregister-targets`

Deregisters the specified targets from the specified target group. After deregistration, the target enters a draining state.

**Synopsis:**
```bash
aws elbv2 deregister-targets \
    --target-group-arn <value> \
    --targets <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-group-arn` | **Yes** | string | -- | ARN of the target group |
| `--targets` | **Yes** | list | -- | Targets to deregister. Shorthand: `Id=string,Port=integer,AvailabilityZone=string ...` |

**Output Schema:** None (no output on success).

---

### 2.9 `describe-target-health`

Describes the health of the specified targets or all targets for the specified target group.

**Synopsis:**
```bash
aws elbv2 describe-target-health \
    --target-group-arn <value> \
    [--targets <value>] \
    [--include <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-group-arn` | **Yes** | string | -- | ARN of the target group |
| `--targets` | No | list | -- | Specific targets to describe |
| `--include` | No | list | -- | Additional info. Values: `AnomalyDetection`, `All` |

**Output Schema:**
```json
{
    "TargetHealthDescriptions": [
        {
            "Target": {
                "Id": "string",
                "Port": integer,
                "AvailabilityZone": "string"
            },
            "HealthCheckPort": "string",
            "TargetHealth": {
                "State": "initial|healthy|unhealthy|unhealthy.draining|unused|draining|unavailable",
                "Reason": "string",
                "Description": "string"
            },
            "AnomalyDetection": {
                "Result": "anomalous|normal",
                "MitigationInEffect": "yes|no"
            },
            "AdministrativeOverride": {
                "State": "string",
                "Reason": "string",
                "Description": "string"
            }
        }
    ]
}
```

**Health State Reason Codes:**

| State | Reason | Description |
|-------|--------|-------------|
| `initial` | `Elb.RegistrationInProgress` | Target registration in progress |
| `initial` | `Elb.InitialHealthChecking` | Health checks in progress |
| `unhealthy` | `Target.ResponseCodeMismatch` | Unexpected HTTP response code |
| `unhealthy` | `Target.Timeout` | Health check timed out |
| `unhealthy` | `Target.FailedHealthChecks` | Connection error or malformed response |
| `unhealthy` | `Elb.InternalError` | Internal health check failure |
| `unused` | `Target.NotRegistered` | Target not registered |
| `unused` | `Target.NotInUse` | Target group not used by load balancer |
| `unused` | `Target.InvalidState` | Target stopped or terminated |
| `unused` | `Target.IpUnusable` | IP reserved for load balancer |
| `draining` | `Target.DeregistrationInProgress` | Deregistration in progress |
| `unavailable` | `Target.HealthCheckDisabled` | Health checks disabled |

---
