# Web ACLs

### 1.1 `create-web-acl`

Creates a web ACL. A web ACL defines a collection of rules that are evaluated against web requests and the action to take on matching requests.

**Synopsis:**
```bash
aws wafv2 create-web-acl \
    --name <value> \
    --scope <value> \
    --default-action <value> \
    --visibility-config <value> \
    [--description <value>] \
    [--rules <value>] \
    [--tags <value>] \
    [--custom-response-bodies <value>] \
    [--captcha-config <value>] \
    [--challenge-config <value>] \
    [--token-domains <value>] \
    [--association-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the web ACL (1-128 chars, alphanumeric + hyphens) |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--default-action` | **Yes** | structure | -- | Default action: `Allow={}` or `Block={}` |
| `--visibility-config` | **Yes** | structure | -- | Visibility config for CloudWatch metrics and sampling |
| `--description` | No | string | -- | Description |
| `--rules` | No | list | -- | Rules for the web ACL (JSON array) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--custom-response-bodies` | No | map | -- | Custom response bodies referenced by rules |
| `--captcha-config` | No | structure | -- | CAPTCHA configuration (immunity time) |
| `--challenge-config` | No | structure | -- | Challenge configuration (immunity time) |
| `--token-domains` | No | list(string) | -- | Domains for token use (CAPTCHA/Challenge) |
| `--association-config` | No | structure | -- | Configuration for associated resources |

**Visibility Config Structure:**
```json
{
    "SampledRequestsEnabled": true,
    "CloudWatchMetricsEnabled": true,
    "MetricName": "string"
}
```

Shorthand: `SampledRequestsEnabled=true,CloudWatchMetricsEnabled=true,MetricName=my-web-acl`

**Rule Structure (each element):**
```json
{
    "Name": "string",
    "Priority": "integer",
    "Statement": {
        "RateBasedStatement": {},
        "ByteMatchStatement": {},
        "SqliMatchStatement": {},
        "XssMatchStatement": {},
        "SizeConstraintStatement": {},
        "GeoMatchStatement": {},
        "IPSetReferenceStatement": {},
        "RegexPatternSetReferenceStatement": {},
        "ManagedRuleGroupStatement": {},
        "RuleGroupReferenceStatement": {},
        "LabelMatchStatement": {},
        "RegexMatchStatement": {},
        "AndStatement": {},
        "OrStatement": {},
        "NotStatement": {}
    },
    "Action": {
        "Block": {},
        "Allow": {},
        "Count": {},
        "Captcha": {},
        "Challenge": {}
    },
    "OverrideAction": {
        "Count": {},
        "None": {}
    },
    "VisibilityConfig": {
        "SampledRequestsEnabled": "boolean",
        "CloudWatchMetricsEnabled": "boolean",
        "MetricName": "string"
    },
    "CaptchaConfig": {},
    "ChallengeConfig": {},
    "RuleLabels": [{"Name": "string"}]
}
```

**Output Schema:**
```json
{
    "Summary": {
        "Name": "string",
        "Id": "string",
        "Description": "string",
        "LockToken": "string",
        "ARN": "string"
    }
}
```

---

### 1.2 `delete-web-acl`

Deletes a web ACL. Must first disassociate it from all resources.

**Synopsis:**
```bash
aws wafv2 delete-web-acl \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the web ACL |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID of the web ACL |
| `--lock-token` | **Yes** | string | -- | Lock token from a get or create operation |

**Output:** None on success.

---

### 1.3 `get-web-acl`

Retrieves a web ACL with all its details.

**Synopsis:**
```bash
aws wafv2 get-web-acl \
    --name <value> \
    --scope <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the web ACL |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID of the web ACL |

**Output Schema:**
```json
{
    "WebACL": {
        "Name": "string",
        "Id": "string",
        "ARN": "string",
        "DefaultAction": {
            "Block": {},
            "Allow": {}
        },
        "Description": "string",
        "Rules": [
            {
                "Name": "string",
                "Priority": "integer",
                "Statement": {},
                "Action": {},
                "OverrideAction": {},
                "RuleLabels": [],
                "VisibilityConfig": {
                    "SampledRequestsEnabled": "boolean",
                    "CloudWatchMetricsEnabled": "boolean",
                    "MetricName": "string"
                },
                "CaptchaConfig": {},
                "ChallengeConfig": {}
            }
        ],
        "VisibilityConfig": {
            "SampledRequestsEnabled": "boolean",
            "CloudWatchMetricsEnabled": "boolean",
            "MetricName": "string"
        },
        "Capacity": "long",
        "PreProcessFirewallManagerRuleGroups": [],
        "PostProcessFirewallManagerRuleGroups": [],
        "ManagedByFirewallManager": "boolean",
        "LabelNamespace": "string",
        "CustomResponseBodies": {},
        "CaptchaConfig": {},
        "ChallengeConfig": {},
        "TokenDomains": ["string"],
        "AssociationConfig": {}
    },
    "LockToken": "string",
    "ApplicationIntegrationURL": "string"
}
```

---

### 1.4 `get-web-acl-for-resource`

Retrieves the web ACL associated with a specific resource.

**Synopsis:**
```bash
aws wafv2 get-web-acl-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the associated resource (ALB, API Gateway, etc.) |

**Output Schema:** Same as `get-web-acl` output.

---

### 1.5 `list-web-acls`

Returns a list of web ACLs. **Paginated operation.**

**Synopsis:**
```bash
aws wafv2 list-web-acls \
    --scope <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum number of results (1-100) |

**Output Schema:**
```json
{
    "NextMarker": "string",
    "WebACLs": [
        {
            "Name": "string",
            "Id": "string",
            "Description": "string",
            "LockToken": "string",
            "ARN": "string"
        }
    ]
}
```

---

### 1.6 `update-web-acl`

Updates a web ACL. Replaces the existing rules and configuration. Requires the current `--lock-token`.

**Synopsis:**
```bash
aws wafv2 update-web-acl \
    --name <value> \
    --scope <value> \
    --id <value> \
    --default-action <value> \
    --lock-token <value> \
    --visibility-config <value> \
    [--description <value>] \
    [--rules <value>] \
    [--custom-response-bodies <value>] \
    [--captcha-config <value>] \
    [--challenge-config <value>] \
    [--token-domains <value>] \
    [--association-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the web ACL |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID of the web ACL |
| `--default-action` | **Yes** | structure | -- | Default action: `Allow={}` or `Block={}` |
| `--lock-token` | **Yes** | string | -- | Lock token from get operation |
| `--visibility-config` | **Yes** | structure | -- | Visibility config |
| `--description` | No | string | -- | New description |
| `--rules` | No | list | -- | New rules (replaces all existing) |
| `--custom-response-bodies` | No | map | -- | Custom response bodies |
| `--captcha-config` | No | structure | -- | CAPTCHA configuration |
| `--challenge-config` | No | structure | -- | Challenge configuration |
| `--token-domains` | No | list(string) | -- | Token domains |
| `--association-config` | No | structure | -- | Association configuration |

**Output Schema:**
```json
{
    "NextLockToken": "string"
}
```

---

### 1.7 `associate-web-acl`

Associates a web ACL with a regional resource (ALB, API Gateway REST API, AppSync, Cognito, App Runner, or Verified Access).

**Synopsis:**
```bash
aws wafv2 associate-web-acl \
    --web-acl-arn <value> \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--web-acl-arn` | **Yes** | string | -- | ARN of the web ACL |
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to protect |

**Output:** None on success.

---

### 1.8 `disassociate-web-acl`

Removes the association between a web ACL and a resource.

**Synopsis:**
```bash
aws wafv2 disassociate-web-acl \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to disassociate |

**Output:** None on success.

---

### 1.9 `list-resources-for-web-acl`

Lists the resources associated with a web ACL.

**Synopsis:**
```bash
aws wafv2 list-resources-for-web-acl \
    --web-acl-arn <value> \
    [--resource-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--web-acl-arn` | **Yes** | string | -- | ARN of the web ACL |
| `--resource-type` | No | string | -- | Filter: `APPLICATION_LOAD_BALANCER`, `API_GATEWAY`, `APPSYNC`, `COGNITO_USER_POOL`, `APP_RUNNER_SERVICE`, `VERIFIED_ACCESS_INSTANCE` |

**Output Schema:**
```json
{
    "ResourceArns": ["string"]
}
```

---

### 1.10 `check-capacity`

Returns the web ACL capacity units (WCU) required for a specified set of rules.

**Synopsis:**
```bash
aws wafv2 check-capacity \
    --scope <value> \
    --rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--rules` | **Yes** | list | -- | Rules to check capacity for |

**Output Schema:**
```json
{
    "Capacity": "long"
}
```

---

### 1.11 `create-api-key`

Creates an API key for use with the CAPTCHA and Challenge JavaScript integrations.

**Synopsis:**
```bash
aws wafv2 create-api-key \
    --scope <value> \
    --token-domains <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--token-domains` | **Yes** | list(string) | -- | Domains the API key is valid for |

**Output Schema:**
```json
{
    "APIKey": "string"
}
```

---

### 1.12 `get-decrypted-api-key`

Returns information about a decrypted API key, including the domains it is valid for.

**Synopsis:**
```bash
aws wafv2 get-decrypted-api-key \
    --scope <value> \
    --api-key <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--api-key` | **Yes** | string | -- | The encrypted API key |

**Output Schema:**
```json
{
    "TokenDomains": ["string"],
    "CreationTimestamp": "timestamp"
}
```

---

### 1.13 `generate-mobile-sdk-release-url`

Generates a presigned download URL for the WAF mobile SDK release.

**Synopsis:**
```bash
aws wafv2 generate-mobile-sdk-release-url \
    --platform <value> \
    --release-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform` | **Yes** | string | -- | Platform: `IOS` or `ANDROID` |
| `--release-version` | **Yes** | string | -- | SDK release version |

**Output Schema:**
```json
{
    "Url": "string"
}
```
