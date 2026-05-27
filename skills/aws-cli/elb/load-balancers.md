# Load Balancers

### 1.1 `create-load-balancer`

Creates a Classic Load Balancer.

**Synopsis:**
```bash
aws elb create-load-balancer \
    --load-balancer-name <value> \
    --listeners <value> \
    [--availability-zones <value>] \
    [--subnets <value>] \
    [--security-groups <value>] \
    [--scheme <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer (1-32 chars, letters/numbers/hyphens) |
| `--listeners` | **Yes** | list | -- | Listeners for the load balancer. Shorthand: `Protocol=string,LoadBalancerPort=integer,InstanceProtocol=string,InstancePort=integer,SSLCertificateId=string ...` |
| `--availability-zones` | No | list(string) | None | One or more AZs (required for EC2-Classic or default VPC) |
| `--subnets` | No | list(string) | None | One or more subnet IDs (for VPC load balancers) |
| `--security-groups` | No | list(string) | None | Security group IDs (for VPC load balancers) |
| `--scheme` | No | string | `internet-facing` | `internet-facing` or `internal` |
| `--tags` | No | list | None | Tags for the load balancer. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "DNSName": "string"
}
```

---

### 1.2 `delete-load-balancer`

Deletes the specified Classic Load Balancer. All registered instances are deregistered and the load balancer stops routing traffic.

**Synopsis:**
```bash
aws elb delete-load-balancer \
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
{}
```

---

### 1.3 `describe-load-balancers`

Describes the specified Classic Load Balancers. If no names are specified, describes all load balancers. **Paginated operation.**

**Synopsis:**
```bash
aws elb describe-load-balancers \
    [--load-balancer-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-names` | No | list(string) | None | Names of the load balancers to describe |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LoadBalancerDescriptions": [
        {
            "LoadBalancerName": "string",
            "DNSName": "string",
            "CanonicalHostedZoneName": "string",
            "CanonicalHostedZoneNameID": "string",
            "ListenerDescriptions": [
                {
                    "Listener": {
                        "Protocol": "string",
                        "LoadBalancerPort": "integer",
                        "InstanceProtocol": "string",
                        "InstancePort": "integer",
                        "SSLCertificateId": "string"
                    },
                    "PolicyNames": ["string"]
                }
            ],
            "Policies": {
                "AppCookieStickinessPolicies": [
                    {
                        "PolicyName": "string",
                        "CookieName": "string"
                    }
                ],
                "LBCookieStickinessPolicies": [
                    {
                        "PolicyName": "string",
                        "CookieExpirationPeriod": "long"
                    }
                ],
                "OtherPolicies": ["string"]
            },
            "BackendServerDescriptions": [
                {
                    "InstancePort": "integer",
                    "PolicyNames": ["string"]
                }
            ],
            "AvailabilityZones": ["string"],
            "Subnets": ["string"],
            "VPCId": "string",
            "Instances": [
                {
                    "InstanceId": "string"
                }
            ],
            "HealthCheck": {
                "Target": "string",
                "Interval": "integer",
                "Timeout": "integer",
                "UnhealthyThreshold": "integer",
                "HealthyThreshold": "integer"
            },
            "SourceSecurityGroup": {
                "OwnerAlias": "string",
                "GroupName": "string"
            },
            "SecurityGroups": ["string"],
            "CreatedTime": "timestamp",
            "Scheme": "string"
        }
    ],
    "NextMarker": "string"
}
```

---

### 1.4 `describe-load-balancer-attributes`

Describes the attributes of the specified load balancer.

**Synopsis:**
```bash
aws elb describe-load-balancer-attributes \
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
    "LoadBalancerAttributes": {
        "CrossZoneLoadBalancing": {
            "Enabled": "boolean"
        },
        "AccessLog": {
            "Enabled": "boolean",
            "S3BucketName": "string",
            "EmitInterval": "integer",
            "S3BucketPrefix": "string"
        },
        "ConnectionDraining": {
            "Enabled": "boolean",
            "Timeout": "integer"
        },
        "ConnectionSettings": {
            "IdleTimeout": "integer"
        },
        "AdditionalAttributes": [
            {
                "Key": "string",
                "Value": "string"
            }
        ]
    }
}
```

---

### 1.5 `modify-load-balancer-attributes`

Modifies attributes of the specified load balancer.

**Synopsis:**
```bash
aws elb modify-load-balancer-attributes \
    --load-balancer-name <value> \
    --load-balancer-attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--load-balancer-attributes` | **Yes** | structure | -- | Attributes to modify |

**Attributes Structure:**
```json
{
    "CrossZoneLoadBalancing": {
        "Enabled": true|false
    },
    "AccessLog": {
        "Enabled": true|false,
        "S3BucketName": "string",
        "EmitInterval": 5|60,
        "S3BucketPrefix": "string"
    },
    "ConnectionDraining": {
        "Enabled": true|false,
        "Timeout": 300
    },
    "ConnectionSettings": {
        "IdleTimeout": 60
    },
    "AdditionalAttributes": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "LoadBalancerName": "string",
    "LoadBalancerAttributes": {
        "CrossZoneLoadBalancing": {
            "Enabled": "boolean"
        },
        "AccessLog": {
            "Enabled": "boolean",
            "S3BucketName": "string",
            "EmitInterval": "integer",
            "S3BucketPrefix": "string"
        },
        "ConnectionDraining": {
            "Enabled": "boolean",
            "Timeout": "integer"
        },
        "ConnectionSettings": {
            "IdleTimeout": "integer"
        },
        "AdditionalAttributes": [
            {
                "Key": "string",
                "Value": "string"
            }
        ]
    }
}
```

---

### 1.6 `describe-account-limits`

Describes the current Elastic Load Balancing resource limits for your AWS account.

**Synopsis:**
```bash
aws elb describe-account-limits \
    [--marker <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker from previous response |
| `--page-size` | No | integer | None | Maximum number of results per call |

**Output Schema:**
```json
{
    "Limits": [
        {
            "Name": "string",
            "Max": "string"
        }
    ],
    "NextMarker": "string"
}
```
