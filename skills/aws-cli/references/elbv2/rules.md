# Rules

### 4.1 `create-rule`

Creates a rule for the specified listener. Each rule consists of conditions and actions.

**Synopsis:**
```bash
aws elbv2 create-rule \
    --listener-arn <value> \
    --conditions <value> \
    --priority <value> \
    --actions <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--conditions` | **Yes** | list | -- | Rule conditions (see structure below) |
| `--priority` | **Yes** | integer | -- | Rule priority (1-50000). Must be unique per listener |
| `--actions` | **Yes** | list | -- | Rule actions (see structure below) |
| `--tags` | No | list | None | Key-value tags |

**Condition Fields:**

| Field | Description | Config Key |
|-------|-------------|------------|
| `host-header` | Match host header (supports wildcards) | `HostHeaderConfig.Values` |
| `path-pattern` | Match URL path (supports wildcards) | `PathPatternConfig.Values` |
| `http-header` | Match HTTP header value | `HttpHeaderConfig` (HttpHeaderName, Values) |
| `http-request-method` | Match HTTP method | `HttpRequestMethodConfig.Values` |
| `query-string` | Match query string key/value | `QueryStringConfig.Values` |
| `source-ip` | Match source IP CIDR | `SourceIpConfig.Values` |

**Action Types:**

| Type | Description |
|------|-------------|
| `forward` | Forward to target group(s) |
| `redirect` | Redirect (301 or 302) |
| `fixed-response` | Return fixed response |
| `authenticate-oidc` | OIDC authentication (HTTPS only) |
| `authenticate-cognito` | Cognito authentication (HTTPS only) |

**Output Schema:**
```json
{
    "Rules": [
        {
            "RuleArn": "string",
            "Priority": "string",
            "Conditions": [
                {
                    "Field": "string",
                    "Values": ["string"],
                    "HostHeaderConfig": {
                        "Values": ["string"]
                    },
                    "PathPatternConfig": {
                        "Values": ["string"]
                    },
                    "HttpHeaderConfig": {
                        "HttpHeaderName": "string",
                        "Values": ["string"]
                    },
                    "QueryStringConfig": {
                        "Values": [
                            {
                                "Key": "string",
                                "Value": "string"
                            }
                        ]
                    },
                    "HttpRequestMethodConfig": {
                        "Values": ["string"]
                    },
                    "SourceIpConfig": {
                        "Values": ["string"]
                    }
                }
            ],
            "Actions": [
                {
                    "Type": "string",
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
            "IsDefault": true|false
        }
    ]
}
```

---

### 4.2 `delete-rule`

Deletes the specified rule. Cannot delete the default rule.

**Synopsis:**
```bash
aws elbv2 delete-rule \
    --rule-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-arn` | **Yes** | string | -- | ARN of the rule |

**Output Schema:** None (no output on success).

---

### 4.3 `describe-rules`

Describes the specified rules or all rules for the listener.

**Synopsis:**
```bash
aws elbv2 describe-rules \
    [--listener-arn <value>] \
    [--rule-arns <value>] \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | No | string | -- | ARN of the listener |
| `--rule-arns` | No | list | -- | ARNs of rules |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Rules": [
        {
            "RuleArn": "string",
            "Priority": "string",
            "Conditions": [ ... ],
            "Actions": [ ... ],
            "IsDefault": true|false
        }
    ],
    "NextMarker": "string"
}
```

---

### 4.4 `modify-rule`

Replaces the specified properties of the specified rule.

**Synopsis:**
```bash
aws elbv2 modify-rule \
    --rule-arn <value> \
    [--conditions <value>] \
    [--actions <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-arn` | **Yes** | string | -- | ARN of the rule |
| `--conditions` | No | list | -- | Updated conditions |
| `--actions` | No | list | -- | Updated actions |

**Output Schema:** Same as `create-rule`.

---

### 4.5 `set-rule-priorities`

Sets the priorities of the specified rules. Use this to reorder rules.

**Synopsis:**
```bash
aws elbv2 set-rule-priorities \
    --rule-priorities <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-priorities` | **Yes** | list | -- | Rule ARN and priority pairs. Shorthand: `RuleArn=string,Priority=integer ...` |

**Output Schema:**
```json
{
    "Rules": [
        {
            "RuleArn": "string",
            "Priority": "string",
            "Conditions": [ ... ],
            "Actions": [ ... ],
            "IsDefault": true|false
        }
    ]
}
```

---
