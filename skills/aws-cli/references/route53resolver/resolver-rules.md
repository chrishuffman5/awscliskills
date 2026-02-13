# Resolver Rules

### 2.1 `create-resolver-rule`

Creates a resolver rule that specifies how DNS queries for a domain are forwarded. FORWARD rules send queries to specified target IPs via an outbound endpoint.

**Synopsis:**
```bash
aws route53resolver create-resolver-rule \
    --creator-request-id <value> \
    --rule-type <value> \
    [--name <value>] \
    [--domain-name <value>] \
    [--target-ips <value>] \
    [--resolver-endpoint-id <value>] \
    [--tags <value>] \
    [--delegation-record <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creator-request-id` | **Yes** | string | -- | Idempotency token (max 255 chars) |
| `--rule-type` | **Yes** | string | -- | `FORWARD`, `SYSTEM`, `RECURSIVE`, or `DELEGATE` |
| `--name` | No | string | None | Friendly name (max 64 chars) |
| `--domain-name` | No | string | None | Domain to match (max 256 chars). More specific domains take precedence |
| `--target-ips` | No | list(structure) | None | Target IPs for FORWARD rules. Do not use with DELEGATE rules |
| `--resolver-endpoint-id` | No | string | None | Outbound endpoint ID for routing queries (max 64 chars) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |
| `--delegation-record` | No | string | None | DNS delegation record (max 256 chars) |

**target-ips Structure:**
```json
[
    {
        "Ip": "string",
        "Port": "integer",
        "Ipv6": "string",
        "Protocol": "DoH|Do53|DoH-FIPS",
        "ServerNameIndication": "string"
    }
]
```
Shorthand: `Ip=string,Port=integer Ip=string,Port=integer`

**Output Schema:**
```json
{
    "ResolverRule": {
        "Id": "string",
        "CreatorRequestId": "string",
        "Arn": "string",
        "DomainName": "string",
        "Status": "COMPLETE|DELETING|UPDATING|FAILED",
        "StatusMessage": "string",
        "RuleType": "FORWARD|SYSTEM|RECURSIVE|DELEGATE",
        "Name": "string",
        "TargetIps": [
            {
                "Ip": "string",
                "Port": "integer",
                "Ipv6": "string",
                "Protocol": "DoH|Do53|DoH-FIPS",
                "ServerNameIndication": "string"
            }
        ],
        "ResolverEndpointId": "string",
        "OwnerId": "string",
        "ShareStatus": "NOT_SHARED|SHARED_WITH_ME|SHARED_BY_ME",
        "CreationTime": "string",
        "ModificationTime": "string",
        "DelegationRecord": "string"
    }
}
```

---

### 2.2 `delete-resolver-rule`

Deletes a resolver rule. The rule must not be associated with any VPCs.

**Synopsis:**
```bash
aws route53resolver delete-resolver-rule \
    --resolver-rule-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-rule-id` | **Yes** | string | -- | The rule ID (max 64 chars) |

**Output Schema:**
Same as `create-resolver-rule` output.

---

### 2.3 `get-resolver-rule`

Gets details of a resolver rule.

**Synopsis:**
```bash
aws route53resolver get-resolver-rule \
    --resolver-rule-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-rule-id` | **Yes** | string | -- | The rule ID (max 64 chars) |

**Output Schema:**
Same as `create-resolver-rule` output.

---

### 2.4 `list-resolver-rules`

Lists all resolver rules in the account. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-resolver-rules \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:** `CreatorRequestId`, `DomainName`, `Name`, `ResolverEndpointId`, `Status`, `Type`

**Output Schema:**
```json
{
    "ResolverRules": [{"...same as ResolverRule above..."}],
    "NextToken": "string",
    "MaxResults": "integer"
}
```

---

### 2.5 `update-resolver-rule`

Updates a resolver rule's name, target IPs, or endpoint.

**Synopsis:**
```bash
aws route53resolver update-resolver-rule \
    --resolver-rule-id <value> \
    --config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-rule-id` | **Yes** | string | -- | The rule ID (max 64 chars) |
| `--config` | **Yes** | structure | -- | New config. Shorthand: `Name=string,TargetIps=[{Ip=string,Port=integer},...],ResolverEndpointId=string` |

**Output Schema:**
Same as `create-resolver-rule` output.

---

### 2.6 `associate-resolver-rule`

Associates a resolver rule with a VPC. When DNS queries in the VPC match the rule's domain, they are forwarded according to the rule.

**Synopsis:**
```bash
aws route53resolver associate-resolver-rule \
    --resolver-rule-id <value> \
    --vpc-id <value> \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-rule-id` | **Yes** | string | -- | The rule ID (max 64 chars) |
| `--vpc-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |
| `--name` | No | string | None | Name for the association (max 64 chars) |

**Output Schema:**
```json
{
    "ResolverRuleAssociation": {
        "Id": "string",
        "ResolverRuleId": "string",
        "Name": "string",
        "VPCId": "string",
        "Status": "CREATING|COMPLETE|DELETING|FAILED|OVERRIDDEN",
        "StatusMessage": "string"
    }
}
```

---

### 2.7 `disassociate-resolver-rule`

Removes a resolver rule association from a VPC.

**Synopsis:**
```bash
aws route53resolver disassociate-resolver-rule \
    --resolver-rule-id <value> \
    --vpc-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-rule-id` | **Yes** | string | -- | The rule ID (max 64 chars) |
| `--vpc-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |

**Output Schema:**
Same as `associate-resolver-rule` output.

---

### 2.8 `get-resolver-rule-association`

Gets details of a resolver rule association.

**Synopsis:**
```bash
aws route53resolver get-resolver-rule-association \
    --resolver-rule-association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-rule-association-id` | **Yes** | string | -- | The association ID (max 64 chars) |

**Output Schema:**
Same as `associate-resolver-rule` output.

---

### 2.9 `list-resolver-rule-associations`

Lists all resolver rule associations. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-resolver-rule-associations \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:** `Name`, `ResolverRuleId`, `Status`, `VPCId`

**Output Schema:**
```json
{
    "ResolverRuleAssociations": [{"...same as ResolverRuleAssociation above..."}],
    "NextToken": "string",
    "MaxResults": "integer"
}
```

---

### 2.10 `get-resolver-rule-policy`

Gets the AWS RAM resource-based policy for sharing a resolver rule.

**Synopsis:**
```bash
aws route53resolver get-resolver-rule-policy \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | The rule ARN (max 255 chars) |

**Output Schema:**
```json
{
    "ResolverRulePolicy": "string"
}
```

---

### 2.11 `put-resolver-rule-policy`

Sets the AWS RAM resource-based policy for sharing a resolver rule with other accounts.

**Synopsis:**
```bash
aws route53resolver put-resolver-rule-policy \
    --arn <value> \
    --resolver-rule-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | The rule ARN (max 255 chars) |
| `--resolver-rule-policy` | **Yes** | string | -- | IAM policy document as JSON string (max 30000 chars) |

**Output Schema:**
```json
{
    "ReturnValue": "boolean"
}
```
