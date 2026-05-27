# Load Balancers

### 8.1 `attach-load-balancers`

Attaches one or more Classic Load Balancers to the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling attach-load-balancers \
    --auto-scaling-group-name <value> \
    --load-balancer-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--load-balancer-names` | **Yes** | list(string) | -- | Classic Load Balancer names |

**Output:** No output on success (empty JSON `{}`).

---

### 8.2 `detach-load-balancers`

Detaches one or more Classic Load Balancers from the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling detach-load-balancers \
    --auto-scaling-group-name <value> \
    --load-balancer-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--load-balancer-names` | **Yes** | list(string) | -- | Classic Load Balancer names |

**Output:** No output on success (empty JSON `{}`).

---

### 8.3 `describe-load-balancers`

Describes the Classic Load Balancers for the specified Auto Scaling group. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-load-balancers \
    --auto-scaling-group-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "LoadBalancers": [
        {
            "LoadBalancerName": "string",
            "State": "Adding|Added|InService|Removing|Removed"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.4 `attach-load-balancer-target-groups`

Attaches one or more ALB/NLB target groups to the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling attach-load-balancer-target-groups \
    --auto-scaling-group-name <value> \
    --target-group-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--target-group-arns` | **Yes** | list(string) | -- | Target group ARNs |

**Output:** No output on success (empty JSON `{}`).

---

### 8.5 `detach-load-balancer-target-groups`

Detaches one or more ALB/NLB target groups from the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling detach-load-balancer-target-groups \
    --auto-scaling-group-name <value> \
    --target-group-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--target-group-arns` | **Yes** | list(string) | -- | Target group ARNs |

**Output:** No output on success (empty JSON `{}`).

---

### 8.6 `describe-load-balancer-target-groups`

Describes the ALB/NLB target groups for the specified Auto Scaling group. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-load-balancer-target-groups \
    --auto-scaling-group-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "LoadBalancerTargetGroups": [
        {
            "LoadBalancerTargetGroupARN": "string",
            "State": "Adding|Added|InService|Removing|Removed"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.7 `attach-traffic-sources`

Attaches one or more traffic sources to the specified Auto Scaling group. Supports ELB, VPC Lattice, and other traffic source types.

**Synopsis:**
```bash
aws autoscaling attach-traffic-sources \
    --auto-scaling-group-name <value> \
    --traffic-sources <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--traffic-sources` | **Yes** | list | -- | Traffic sources. Shorthand: `Identifier=string,Type=string ...` |

**Output:** No output on success (empty JSON `{}`).

---

### 8.8 `detach-traffic-sources`

Detaches one or more traffic sources from the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling detach-traffic-sources \
    --auto-scaling-group-name <value> \
    --traffic-sources <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--traffic-sources` | **Yes** | list | -- | Traffic sources to detach |

**Output:** No output on success (empty JSON `{}`).

---

### 8.9 `describe-traffic-sources`

Describes the traffic sources for the specified Auto Scaling group. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-traffic-sources \
    --auto-scaling-group-name <value> \
    [--traffic-source-type <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--traffic-source-type` | No | string | None | Filter by type: `elb`, `elbv2`, `vpc-lattice` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "TrafficSources": [
        {
            "Identifier": "string",
            "State": "Adding|Added|InService|Removing|Removed",
            "Type": "string"
        }
    ],
    "NextToken": "string"
}
```
