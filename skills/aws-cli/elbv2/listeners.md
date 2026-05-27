# Listeners

### 3.1 `create-listener`

Creates a listener for the specified load balancer.

**Synopsis:**
```bash
aws elbv2 create-listener \
    --load-balancer-arn <value> \
    --default-actions <value> \
    [--protocol <value>] \
    [--port <value>] \
    [--ssl-policy <value>] \
    [--certificates <value>] \
    [--alpn-policy <value>] \
    [--tags <value>] \
    [--mutual-authentication <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | **Yes** | string | -- | ARN of the load balancer |
| `--default-actions` | **Yes** | list | -- | Default actions. Must include exactly one routing action (`forward`, `fixed-response`, or `redirect`) |
| `--protocol` | No | string | -- | ALB: `HTTP`, `HTTPS`. NLB: `TCP`, `TLS`, `UDP`, `TCP_UDP` |
| `--port` | No | integer | -- | Port (1-65535). Not applicable for GWLB |
| `--ssl-policy` | No | string | -- | SSL security policy (HTTPS/TLS listeners) |
| `--certificates` | No | list | -- | Default certificate. Shorthand: `CertificateArn=string` |
| `--alpn-policy` | No | list | -- | TLS listeners: `HTTP1Only`, `HTTP2Only`, `HTTP2Optional`, `HTTP2Preferred`, `None` |
| `--tags` | No | list | None | Key-value tags |
| `--mutual-authentication` | No | structure | -- | Mutual TLS config for HTTPS listeners |

**Default Actions Structure (common types):**

| Action Type | Key Fields | Description |
|-------------|------------|-------------|
| `forward` | `TargetGroupArn` or `ForwardConfig` | Forward to target group(s) |
| `redirect` | `RedirectConfig` (Protocol, Port, Host, Path, Query, StatusCode) | Redirect request |
| `fixed-response` | `FixedResponseConfig` (StatusCode, ContentType, MessageBody) | Return fixed response |
| `authenticate-oidc` | `AuthenticateOidcConfig` | OIDC authentication (HTTPS only) |
| `authenticate-cognito` | `AuthenticateCognitoConfig` | Cognito authentication (HTTPS only) |

**Output Schema:**
```json
{
    "Listeners": [
        {
            "ListenerArn": "string",
            "LoadBalancerArn": "string",
            "Port": integer,
            "Protocol": "HTTP|HTTPS|TCP|TLS|UDP|TCP_UDP|GENEVE",
            "Certificates": [
                {
                    "CertificateArn": "string",
                    "IsDefault": true|false
                }
            ],
            "SslPolicy": "string",
            "DefaultActions": [
                {
                    "Type": "forward|redirect|fixed-response|authenticate-oidc|authenticate-cognito",
                    "TargetGroupArn": "string",
                    "Order": integer,
                    "RedirectConfig": {
                        "Protocol": "string",
                        "Port": "string",
                        "Host": "string",
                        "Path": "string",
                        "Query": "string",
                        "StatusCode": "HTTP_301|HTTP_302"
                    },
                    "FixedResponseConfig": {
                        "MessageBody": "string",
                        "StatusCode": "string",
                        "ContentType": "string"
                    },
                    "ForwardConfig": {
                        "TargetGroups": [
                            {
                                "TargetGroupArn": "string",
                                "Weight": integer
                            }
                        ],
                        "TargetGroupStickinessConfig": {
                            "Enabled": true|false,
                            "DurationSeconds": integer
                        }
                    }
                }
            ],
            "AlpnPolicy": ["string"],
            "MutualAuthentication": {
                "Mode": "string",
                "TrustStoreArn": "string",
                "IgnoreClientCertificateExpiry": true|false,
                "TrustStoreAssociationStatus": "active|removed",
                "AdvertiseTrustStoreCaNames": "on|off"
            }
        }
    ]
}
```

---

### 3.2 `delete-listener`

Deletes the specified listener. Also deletes all associated listener rules.

**Synopsis:**
```bash
aws elbv2 delete-listener \
    --listener-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |

**Output Schema:** None (no output on success).

---

### 3.3 `describe-listeners`

Describes the specified listeners or all listeners for the load balancer. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-listeners \
    [--load-balancer-arn <value>] \
    [--listener-arns <value>] \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-arn` | No | string | -- | ARN of the load balancer |
| `--listener-arns` | No | list | -- | ARNs of listeners |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Listeners": [
        {
            "ListenerArn": "string",
            "LoadBalancerArn": "string",
            "Port": integer,
            "Protocol": "string",
            "Certificates": [
                {
                    "CertificateArn": "string",
                    "IsDefault": true|false
                }
            ],
            "SslPolicy": "string",
            "DefaultActions": [ ... ],
            "AlpnPolicy": ["string"],
            "MutualAuthentication": { ... }
        }
    ],
    "NextMarker": "string"
}
```

---

### 3.4 `modify-listener`

Replaces the specified properties of the specified listener. Any properties not specified remain unchanged.

**Synopsis:**
```bash
aws elbv2 modify-listener \
    --listener-arn <value> \
    [--port <value>] \
    [--protocol <value>] \
    [--ssl-policy <value>] \
    [--certificates <value>] \
    [--default-actions <value>] \
    [--alpn-policy <value>] \
    [--mutual-authentication <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--port` | No | integer | -- | Port (1-65535) |
| `--protocol` | No | string | -- | Protocol for connections |
| `--ssl-policy` | No | string | -- | SSL security policy |
| `--certificates` | No | list | -- | Default certificate |
| `--default-actions` | No | list | -- | Default actions |
| `--alpn-policy` | No | list | -- | ALPN policy |
| `--mutual-authentication` | No | structure | -- | Mutual TLS config |

**Output Schema:** Same as `create-listener`.

---

### 3.5 `describe-listener-attributes`

Describes the attributes for the specified listener.

**Synopsis:**
```bash
aws elbv2 describe-listener-attributes \
    --listener-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |

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

### 3.6 `modify-listener-attributes`

Modifies the specified attributes of the specified listener.

**Synopsis:**
```bash
aws elbv2 modify-listener-attributes \
    --listener-arn <value> \
    --attributes <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--attributes` | **Yes** | list | -- | Attributes to modify. Shorthand: `Key=string,Value=string ...` |

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
