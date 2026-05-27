# Subnets & Zones

### 5.1 `associate-subnets`

Associates additional subnets with the specified firewall. Each subnet must be in a different availability zone.

**Synopsis:**
```bash
aws network-firewall associate-subnets \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --subnet-mappings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--subnet-mappings` | **Yes** | list | -- | Subnets to associate. Shorthand: `SubnetId=string,IPAddressType=DUALSTACK\|IPV4\|IPV6` |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "SubnetMappings": [
        {
            "SubnetId": "string",
            "IPAddressType": "DUALSTACK|IPV4|IPV6"
        }
    ],
    "UpdateToken": "string"
}
```

---

### 5.2 `disassociate-subnets`

Removes subnet associations from the specified firewall. At least one subnet must remain.

**Synopsis:**
```bash
aws network-firewall disassociate-subnets \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --subnet-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--subnet-ids` | **Yes** | list(string) | -- | Subnet IDs to disassociate |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "SubnetMappings": [
        {
            "SubnetId": "string",
            "IPAddressType": "DUALSTACK|IPV4|IPV6"
        }
    ],
    "UpdateToken": "string"
}
```

---

### 5.3 `associate-availability-zones`

Associates availability zones with a transit gateway-attached firewall.

**Synopsis:**
```bash
aws network-firewall associate-availability-zones \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --availability-zone-mappings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--availability-zone-mappings` | **Yes** | list | -- | AZ mappings. Shorthand: `AvailabilityZone=string` |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "AvailabilityZoneMappings": [
        {
            "AvailabilityZone": "string"
        }
    ],
    "UpdateToken": "string"
}
```

---

### 5.4 `disassociate-availability-zones`

Removes availability zone associations from a transit gateway-attached firewall.

**Synopsis:**
```bash
aws network-firewall disassociate-availability-zones \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --availability-zone-mappings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--availability-zone-mappings` | **Yes** | list | -- | AZ mappings to remove |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "AvailabilityZoneMappings": [
        {
            "AvailabilityZone": "string"
        }
    ],
    "UpdateToken": "string"
}
```

---

### 5.5 `update-subnet-change-protection`

Enables or disables subnet change protection for the specified firewall.

**Synopsis:**
```bash
aws network-firewall update-subnet-change-protection \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --subnet-change-protection | --no-subnet-change-protection \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--subnet-change-protection` | **Yes** | boolean | -- | Enable or disable subnet change protection |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "SubnetChangeProtection": true|false,
    "UpdateToken": "string"
}
```
