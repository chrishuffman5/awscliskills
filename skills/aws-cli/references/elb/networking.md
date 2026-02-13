# Networking

### 5.1 `apply-security-groups-to-load-balancer`

Associates one or more security groups with your load balancer in a VPC. The specified security groups override the previously associated security groups.

**Synopsis:**
```bash
aws elb apply-security-groups-to-load-balancer \
    --load-balancer-name <value> \
    --security-groups <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--security-groups` | **Yes** | list(string) | -- | Security group IDs to associate |

**Output Schema:**
```json
{
    "SecurityGroups": ["string"]
}
```

---

### 5.2 `attach-load-balancer-to-subnets`

Adds one or more subnets to the set of configured subnets for the specified load balancer.

**Synopsis:**
```bash
aws elb attach-load-balancer-to-subnets \
    --load-balancer-name <value> \
    --subnets <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--subnets` | **Yes** | list(string) | -- | Subnet IDs to add |

**Output Schema:**
```json
{
    "Subnets": ["string"]
}
```

---

### 5.3 `detach-load-balancer-from-subnets`

Removes the specified subnets from the set of configured subnets for the load balancer. There must be at least one remaining subnet.

**Synopsis:**
```bash
aws elb detach-load-balancer-from-subnets \
    --load-balancer-name <value> \
    --subnets <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--subnets` | **Yes** | list(string) | -- | Subnet IDs to remove |

**Output Schema:**
```json
{
    "Subnets": ["string"]
}
```

---

### 5.4 `enable-availability-zones-for-load-balancer`

Adds the specified Availability Zones to the set of Availability Zones for the specified load balancer.

**Synopsis:**
```bash
aws elb enable-availability-zones-for-load-balancer \
    --load-balancer-name <value> \
    --availability-zones <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--availability-zones` | **Yes** | list(string) | -- | Availability Zones to enable (e.g., `us-east-1a`) |

**Output Schema:**
```json
{
    "AvailabilityZones": ["string"]
}
```

---

### 5.5 `disable-availability-zones-for-load-balancer`

Removes the specified Availability Zones from the set of Availability Zones for the specified load balancer. There must be at least one remaining Availability Zone.

**Synopsis:**
```bash
aws elb disable-availability-zones-for-load-balancer \
    --load-balancer-name <value> \
    --availability-zones <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--availability-zones` | **Yes** | list(string) | -- | Availability Zones to disable |

**Output Schema:**
```json
{
    "AvailabilityZones": ["string"]
}
```
