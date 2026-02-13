# Load Balancers

### 1.1 `create-load-balancer`

Creates an Application Load Balancer, Network Load Balancer, or Gateway Load Balancer.

**Synopsis:**
```bash
aws elbv2 create-load-balancer \
    --name <value> \
    [--subnets <value>] \
    [--subnet-mappings <value>] \
    [--security-groups <value>] \
    [--scheme <value>] \
    [--tags <value>] \
    [--type <value>] \
    [--ip-address-type <value>] \
    [--customer-owned-ipv4-pool <value>] \
    [--enable-prefix-for-ipv6-source-nat <value>] \
    [--ipam-pools <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Load balancer name. Max 32 chars, alphanumeric and hyphens only. Cannot begin/end with hyphen or start with `internal-` |
| `--subnets` | No | list | -- | Subnet IDs (one per AZ). ALB requires min 2 AZs. Mutually exclusive with `--subnet-mappings` |
| `--subnet-mappings` | No | list | -- | Subnet mappings with optional Elastic IPs, private IPs, IPv6 addresses. Mutually exclusive with `--subnets` |
| `--security-groups` | No | list | -- | Security group IDs. Applies to ALB and NLB |
| `--scheme` | No | string | `internet-facing` | Values: `internet-facing`, `internal`. Not applicable to GWLB |
| `--tags` | No | list | None | Key-value tags. Key max 128 chars, Value max 256 chars |
| `--type` | No | string | `application` | Values: `application`, `network`, `gateway` |
| `--ip-address-type` | No | string | `ipv4` | Values: `ipv4`, `dualstack`, `dualstack-without-public-ipv4` |
| `--customer-owned-ipv4-pool` | No | string | -- | CoIP pool ID (ALB on Outposts only) |
| `--enable-prefix-for-ipv6-source-nat` | No | string | `off` | NLB UDP listeners: `on` or `off` |
| `--ipam-pools` | No | structure | -- | IPAM pools for ALB (IPv4 IPAM pool ID) |

**Output Schema:**
```json
{
    "LoadBalancers": [
        {
            "LoadBalancerArn": "string",
            "DNSName": "string",
            "CanonicalHostedZoneId": "string",
            "CreatedTime": "timestamp",
            "LoadBalancerName": "string",
            "Scheme": "internet-facing|internal",
            "VpcId": "string",
            "State": {
                "Code": "active|provisioning|active_impaired|failed",
                "Reason": "string"
            },
            "Type": "application|network|gateway",
            "AvailabilityZones": [
                {
                    "ZoneName": "string",
                    "SubnetId": "string",
                    "OutpostId": "string",
                    "LoadBalancerAddresses": [
                        {
                            "IpAddress": "string",
                            "AllocationId": "string",
                            "PrivateIPv4Address": "string",
                            "IPv6Address": "string"
                        }
                    ],
                    "SourceNatIpv6Prefixes": ["string"]
                }
            ],
            "SecurityGroups": ["string"],
            "IpAddressType": "ipv4|dualstack|dualstack-without-public-ipv4",
            "CustomerOwnedIpv4Pool": "string",
            "EnforceSecurityGroupInboundRulesOnPrivateLinkTraffic": "string",
            "EnablePrefixForIpv6SourceNat": "on|off",
            "IpamPools": {
                "Ipv4IpamPoolId": "string"
            }
        }
    ]
}
```

---

### 1.2 `delete-load-balancer`

Deletes the specified load balancer and its attached listeners. Cannot delete if deletion protection is enabled.

**Synopsis:**
```bash
aws elbv2 delete-load-balancer \
    --load-balancer-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |

**Output Schema:** None (no output on success).

---

### 1.3 `describe-load-balancers`

Describes the specified load balancers or all load balancers. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-load-balancers \
    [--load-balancer-arns <value>] \
    [--names <value>] \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arns` | No | list | -- | ARNs of load balancers (max 20) |
| `--names` | No | list | -- | Names of load balancers |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token from previous response |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "LoadBalancers": [
        {
            "LoadBalancerArn": "string",
            "DNSName": "string",
            "CanonicalHostedZoneId": "string",
            "CreatedTime": "timestamp",
            "LoadBalancerName": "string",
            "Scheme": "internet-facing|internal",
            "VpcId": "string",
            "State": {
                "Code": "active|provisioning|active_impaired|failed",
                "Reason": "string"
            },
            "Type": "application|network|gateway",
            "AvailabilityZones": [
                {
                    "ZoneName": "string",
                    "SubnetId": "string",
                    "OutpostId": "string",
                    "LoadBalancerAddresses": [
                        {
                            "IpAddress": "string",
                            "AllocationId": "string",
                            "PrivateIPv4Address": "string",
                            "IPv6Address": "string"
                        }
                    ],
                    "SourceNatIpv6Prefixes": ["string"]
                }
            ],
            "SecurityGroups": ["string"],
            "IpAddressType": "ipv4|dualstack|dualstack-without-public-ipv4",
            "CustomerOwnedIpv4Pool": "string",
            "EnforceSecurityGroupInboundRulesOnPrivateLinkTraffic": "string",
            "EnablePrefixForIpv6SourceNat": "on|off",
            "IpamPools": {
                "Ipv4IpamPoolId": "string"
            }
        }
    ],
    "NextMarker": "string"
}
```

---

### 1.4 `modify-load-balancer-attributes`

Modifies the specified attributes of the specified load balancer.

**Synopsis:**
```bash
aws elbv2 modify-load-balancer-attributes \
    --load-balancer-arn <value> \
    --attributes <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |
| `--attributes` | **Yes** | list | -- | Attributes to modify (max 20). Shorthand: `Key=string,Value=string ...` |

**Common Attribute Keys:**

| Key | LB Type | Default | Description |
|-----|---------|---------|-------------|
| `deletion_protection.enabled` | All | `false` | Enable deletion protection |
| `load_balancing.cross_zone.enabled` | NLB/GWLB | `false` | Enable cross-zone load balancing |
| `access_logs.s3.enabled` | ALB/NLB | `false` | Enable S3 access logs |
| `access_logs.s3.bucket` | ALB/NLB | -- | S3 bucket for access logs |
| `access_logs.s3.prefix` | ALB/NLB | -- | S3 prefix for access logs |
| `idle_timeout.timeout_seconds` | ALB | `60` | Idle timeout (1-4000 seconds) |
| `routing.http2.enabled` | ALB | `true` | Enable HTTP/2 |
| `routing.http.desync_mitigation_mode` | ALB | `defensive` | Values: `monitor`, `defensive`, `strictest` |
| `routing.http.drop_invalid_header_fields.enabled` | ALB | `false` | Remove invalid HTTP headers |
| `routing.http.preserve_host_header.enabled` | ALB | `false` | Preserve Host header |
| `routing.http.xff_header_processing.mode` | ALB | `append` | Values: `append`, `preserve`, `remove` |
| `waf.fail_open.enabled` | ALB | `false` | Route requests when WAF unavailable |
| `connection_logs.s3.enabled` | ALB | `false` | Enable connection logs |
| `connection_logs.s3.bucket` | ALB | -- | S3 bucket for connection logs |
| `client_keep_alive.seconds` | ALB | `3600` | Client keep-alive (60-604800 seconds) |
| `dns_record.client_routing_policy` | NLB | -- | Values: `availability_zone_affinity`, `partial_availability_zone_affinity`, `any_availability_zone` |
| `ipv6.deny_all_igw_traffic` | ALB/NLB | `false` | Block IGW access |
| `zonal_shift.config.enabled` | ALB/NLB | `false` | Enable zonal shift |

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

### 1.5 `describe-load-balancer-attributes`

Describes the attributes for the specified load balancer.

**Synopsis:**
```bash
aws elbv2 describe-load-balancer-attributes \
    --load-balancer-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |

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

### 1.6 `set-subnets`

Enables an Availability Zone for the load balancer or changes the subnets.

**Synopsis:**
```bash
aws elbv2 set-subnets \
    --load-balancer-arn <value> \
    [--subnets <value>] \
    [--subnet-mappings <value>] \
    [--ip-address-type <value>] \
    [--enable-prefix-for-ipv6-source-nat <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |
| `--subnets` | No | list | -- | Subnet IDs. Mutually exclusive with `--subnet-mappings` |
| `--subnet-mappings` | No | list | -- | Subnet mappings with optional Elastic IPs |
| `--ip-address-type` | No | string | -- | Values: `ipv4`, `dualstack`, `dualstack-without-public-ipv4` |
| `--enable-prefix-for-ipv6-source-nat` | No | string | -- | NLB only: `on` or `off` |

**Output Schema:**
```json
{
    "AvailabilityZones": [
        {
            "ZoneName": "string",
            "SubnetId": "string",
            "OutpostId": "string",
            "LoadBalancerAddresses": [
                {
                    "IpAddress": "string",
                    "AllocationId": "string",
                    "PrivateIPv4Address": "string",
                    "IPv6Address": "string"
                }
            ],
            "SourceNatIpv6Prefixes": ["string"]
        }
    ],
    "IpAddressType": "ipv4|dualstack|dualstack-without-public-ipv4",
    "EnablePrefixForIpv6SourceNat": "on|off"
}
```

---

### 1.7 `set-security-groups`

Associates the specified security groups with the specified ALB or NLB. Replaces any existing associations.

**Synopsis:**
```bash
aws elbv2 set-security-groups \
    --load-balancer-arn <value> \
    --security-groups <value> \
    [--enforce-security-group-inbound-rules-on-private-link-traffic <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |
| `--security-groups` | **Yes** | list | -- | IDs of the security groups |
| `--enforce-security-group-inbound-rules-on-private-link-traffic` | No | string | -- | Values: `on`, `off`. Controls PrivateLink traffic SG enforcement |

**Output Schema:**
```json
{
    "SecurityGroupIds": ["string"],
    "EnforceSecurityGroupInboundRulesOnPrivateLinkTraffic": "on|off"
}
```

---

### 1.8 `set-ip-address-type`

Sets the type of IP addresses used by the subnets of the specified load balancer.

**Synopsis:**
```bash
aws elbv2 set-ip-address-type \
    --load-balancer-arn <value> \
    --ip-address-type <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |
| `--ip-address-type` | **Yes** | string | -- | Values: `ipv4`, `dualstack`, `dualstack-without-public-ipv4` |

**Output Schema:**
```json
{
    "IpAddressType": "ipv4|dualstack|dualstack-without-public-ipv4"
}
```

---

### 1.9 `get-resource-policy`

Retrieves the resource policy for a specified resource.

**Synopsis:**
```bash
aws elbv2 get-resource-policy \
    --resource-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 1.10 `describe-capacity-reservation`

Describes the capacity reservation status for the specified load balancer.

**Synopsis:**
```bash
aws elbv2 describe-capacity-reservation \
    --load-balancer-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |

**Output Schema:**
```json
{
    "LastModifiedTime": "timestamp",
    "DecreaseRequestsRemaining": integer,
    "MinimumLoadBalancerCapacity": {
        "CapacityUnits": integer
    },
    "CapacityReservationState": [
        {
            "Code": "provisioned|pending|rebalancing|failed",
            "Reason": "string"
        }
    ]
}
```

---

### 1.11 `modify-capacity-reservation`

Modifies the capacity reservation of the specified load balancer.

**Synopsis:**
```bash
aws elbv2 modify-capacity-reservation \
    --load-balancer-arn <value> \
    [--minimum-load-balancer-capacity <value>] \
    [--reset-capacity-reservation | --no-reset-capacity-reservation]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |
| `--minimum-load-balancer-capacity` | No | structure | -- | Minimum capacity. Shorthand: `CapacityUnits=integer` |
| `--reset-capacity-reservation` | No | boolean | -- | Reset the capacity reservation |

**Output Schema:**
```json
{
    "LastModifiedTime": "timestamp",
    "DecreaseRequestsRemaining": integer,
    "MinimumLoadBalancerCapacity": {
        "CapacityUnits": integer
    },
    "CapacityReservationState": [
        {
            "Code": "provisioned|pending|rebalancing|failed",
            "Reason": "string"
        }
    ]
}
```

---

### 1.12 `modify-ip-pools`

Modifies IP pools for the specified load balancer.

**Synopsis:**
```bash
aws elbv2 modify-ip-pools \
    --load-balancer-arn <value> \
    --ipam-pools <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |
| `--ipam-pools` | **Yes** | structure | -- | IPAM pools configuration. Shorthand: `Ipv4IpamPoolId=string` |

**Output Schema:**
```json
{
    "IpAddressType": "ipv4|dualstack|dualstack-without-public-ipv4",
    "IpamPools": {
        "Ipv4IpamPoolId": "string"
    }
}
```
