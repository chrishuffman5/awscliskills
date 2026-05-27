# Instances

### 3.1 `register-instances-with-load-balancer`

Adds the specified instances to the specified load balancer.

**Synopsis:**
```bash
aws elb register-instances-with-load-balancer \
    --load-balancer-name <value> \
    --instances <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instances` | **Yes** | list(string) | -- | Instance IDs to register |

**Output Schema:**
```json
{
    "Instances": [
        {
            "InstanceId": "string"
        }
    ]
}
```

---

### 3.2 `deregister-instances-from-load-balancer`

Deregisters the specified instances from the specified load balancer. After deregistration, the instance will stop receiving traffic.

**Synopsis:**
```bash
aws elb deregister-instances-from-load-balancer \
    --load-balancer-name <value> \
    --instances <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instances` | **Yes** | list(string) | -- | Instance IDs to deregister |

**Output Schema:**
```json
{
    "Instances": [
        {
            "InstanceId": "string"
        }
    ]
}
```

---

### 3.3 `describe-instance-health`

Describes the state of the specified instances with respect to the specified load balancer.

**Synopsis:**
```bash
aws elb describe-instance-health \
    --load-balancer-name <value> \
    [--instances <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instances` | No | list(string) | None | Instance IDs to check; omit for all registered instances |

**Output Schema:**
```json
{
    "InstanceStates": [
        {
            "InstanceId": "string",
            "State": "InService|OutOfService|Unknown",
            "ReasonCode": "ELB|Instance|N/A",
            "Description": "string"
        }
    ]
}
```

---

### 3.4 `configure-health-check`

Specifies the health check settings to use when evaluating the health state of registered instances.

**Synopsis:**
```bash
aws elb configure-health-check \
    --load-balancer-name <value> \
    --health-check <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--health-check` | **Yes** | structure | -- | Health check configuration. Shorthand: `Target=string,Interval=integer,Timeout=integer,UnhealthyThreshold=integer,HealthyThreshold=integer` |

**Health Check Structure:**
```json
{
    "Target": "string",
    "Interval": "integer",
    "Timeout": "integer",
    "UnhealthyThreshold": "integer",
    "HealthyThreshold": "integer"
}
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Target` | **Yes** | string | Ping target: `Protocol:Port[/PathToPing]` (e.g., `HTTP:80/health`, `TCP:80`) |
| `Interval` | **Yes** | integer | Seconds between health checks (5-300) |
| `Timeout` | **Yes** | integer | Seconds to wait for a response (2-60, must be less than Interval) |
| `UnhealthyThreshold` | **Yes** | integer | Consecutive failures before marking unhealthy (2-10) |
| `HealthyThreshold` | **Yes** | integer | Consecutive successes before marking healthy (2-10) |

**Output Schema:**
```json
{
    "HealthCheck": {
        "Target": "string",
        "Interval": "integer",
        "Timeout": "integer",
        "UnhealthyThreshold": "integer",
        "HealthyThreshold": "integer"
    }
}
```
