# DNS Firewall

### 3.1 `create-firewall-rule-group`

Creates an empty DNS Firewall rule group for organizing firewall rules.

**Synopsis:**
```bash
aws route53resolver create-firewall-rule-group \
    --name <value> \
    [--creator-request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule group name (max 64 chars) |
| `--creator-request-id` | No | string | None | Idempotency token (max 255 chars) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "FirewallRuleGroup": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "RuleCount": "integer",
        "Status": "COMPLETE|DELETING|UPDATING",
        "StatusMessage": "string",
        "OwnerId": "string",
        "CreatorRequestId": "string",
        "ShareStatus": "NOT_SHARED|SHARED_WITH_ME|SHARED_BY_ME",
        "CreationTime": "string",
        "ModificationTime": "string"
    }
}
```

---

### 3.2 `delete-firewall-rule-group`

Deletes a DNS Firewall rule group. The group must have no rules and no VPC associations.

**Synopsis:**
```bash
aws route53resolver delete-firewall-rule-group \
    --firewall-rule-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-id` | **Yes** | string | -- | The rule group ID (max 64 chars) |

**Output Schema:**
Same as `create-firewall-rule-group` output.

---

### 3.3 `get-firewall-rule-group`

Gets details of a DNS Firewall rule group.

**Synopsis:**
```bash
aws route53resolver get-firewall-rule-group \
    --firewall-rule-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-id` | **Yes** | string | -- | The rule group ID (max 64 chars) |

**Output Schema:**
Same as `create-firewall-rule-group` output.

---

### 3.4 `list-firewall-rule-groups`

Lists all DNS Firewall rule groups. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-firewall-rule-groups \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FirewallRuleGroups": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "OwnerId": "string",
            "CreatorRequestId": "string",
            "ShareStatus": "NOT_SHARED|SHARED_WITH_ME|SHARED_BY_ME"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `associate-firewall-rule-group`

Associates a DNS Firewall rule group with a VPC.

**Synopsis:**
```bash
aws route53resolver associate-firewall-rule-group \
    --firewall-rule-group-id <value> \
    --vpc-id <value> \
    --priority <value> \
    --name <value> \
    [--creator-request-id <value>] \
    [--mutation-protection <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-id` | **Yes** | string | -- | The rule group ID (max 64 chars) |
| `--vpc-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |
| `--priority` | **Yes** | integer | -- | Processing priority (lower = first). Must be unique per VPC |
| `--name` | **Yes** | string | -- | Association name (max 64 chars) |
| `--creator-request-id` | No | string | None | Idempotency token (max 255 chars) |
| `--mutation-protection` | No | string | None | `ENABLED` or `DISABLED`. Prevents modification |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "FirewallRuleGroupAssociation": {
        "Id": "string",
        "Arn": "string",
        "FirewallRuleGroupId": "string",
        "VpcId": "string",
        "Name": "string",
        "Priority": "integer",
        "MutationProtection": "ENABLED|DISABLED",
        "ManagedOwnerName": "string",
        "Status": "COMPLETE|DELETING|UPDATING",
        "StatusMessage": "string",
        "CreatorRequestId": "string",
        "CreationTime": "string",
        "ModificationTime": "string"
    }
}
```

---

### 3.6 `disassociate-firewall-rule-group`

Removes a DNS Firewall rule group association from a VPC.

**Synopsis:**
```bash
aws route53resolver disassociate-firewall-rule-group \
    --firewall-rule-group-association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-association-id` | **Yes** | string | -- | The association ID (max 64 chars) |

**Output Schema:**
Same as `associate-firewall-rule-group` output.

---

### 3.7 `get-firewall-rule-group-association`

Gets details of a firewall rule group association.

**Synopsis:**
```bash
aws route53resolver get-firewall-rule-group-association \
    --firewall-rule-group-association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-association-id` | **Yes** | string | -- | The association ID (max 64 chars) |

**Output Schema:**
Same as `associate-firewall-rule-group` output.

---

### 3.8 `list-firewall-rule-group-associations`

Lists firewall rule group associations. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-firewall-rule-group-associations \
    [--firewall-rule-group-id <value>] \
    [--vpc-id <value>] \
    [--priority <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-id` | No | string | None | Filter by rule group ID |
| `--vpc-id` | No | string | None | Filter by VPC ID |
| `--priority` | No | integer | None | Filter by priority |
| `--status` | No | string | None | Filter: `COMPLETE`, `DELETING`, `UPDATING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FirewallRuleGroupAssociations": [{"...same as FirewallRuleGroupAssociation above..."}],
    "NextToken": "string"
}
```

---

### 3.9 `get-firewall-rule-group-policy`

Gets the RAM resource-based policy for sharing a firewall rule group.

**Synopsis:**
```bash
aws route53resolver get-firewall-rule-group-policy \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | The rule group ARN (max 255 chars) |

**Output Schema:**
```json
{
    "FirewallRuleGroupPolicy": "string"
}
```

---

### 3.10 `put-firewall-rule-group-policy`

Sets the RAM resource-based policy for sharing a firewall rule group.

**Synopsis:**
```bash
aws route53resolver put-firewall-rule-group-policy \
    --arn <value> \
    --firewall-rule-group-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | The rule group ARN (max 255 chars) |
| `--firewall-rule-group-policy` | **Yes** | string | -- | IAM policy document as JSON string (max 30000 chars) |

**Output Schema:**
```json
{
    "ReturnValue": "boolean"
}
```

---

### 3.11 `create-firewall-domain-list`

Creates a domain list for use with DNS Firewall rules.

**Synopsis:**
```bash
aws route53resolver create-firewall-domain-list \
    --name <value> \
    [--creator-request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain list name (max 64 chars) |
| `--creator-request-id` | No | string | None | Idempotency token (max 255 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "FirewallDomainList": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "DomainCount": "integer",
        "Status": "COMPLETE|COMPLETE_IMPORT_FAILED|IMPORTING|DELETING|UPDATING",
        "StatusMessage": "string",
        "ManagedOwnerName": "string",
        "CreatorRequestId": "string",
        "CreationTime": "string",
        "ModificationTime": "string"
    }
}
```

---

### 3.12 `delete-firewall-domain-list`

Deletes a firewall domain list.

**Synopsis:**
```bash
aws route53resolver delete-firewall-domain-list \
    --firewall-domain-list-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-domain-list-id` | **Yes** | string | -- | The domain list ID (max 64 chars) |

**Output Schema:**
Same as `create-firewall-domain-list` output.

---

### 3.13 `get-firewall-domain-list`

Gets details of a firewall domain list.

**Synopsis:**
```bash
aws route53resolver get-firewall-domain-list \
    --firewall-domain-list-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-domain-list-id` | **Yes** | string | -- | The domain list ID (max 64 chars) |

**Output Schema:**
Same as `create-firewall-domain-list` output.

---

### 3.14 `list-firewall-domain-lists`

Lists all firewall domain lists. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-firewall-domain-lists \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FirewallDomainLists": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "CreatorRequestId": "string",
            "ManagedOwnerName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.15 `list-firewall-domains`

Lists the domains in a firewall domain list. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-firewall-domains \
    --firewall-domain-list-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-domain-list-id` | **Yes** | string | -- | The domain list ID (max 64 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Domains": ["string"],
    "NextToken": "string"
}
```

---

### 3.16 `import-firewall-domains`

Imports a list of domains from an S3 file into a firewall domain list.

**Synopsis:**
```bash
aws route53resolver import-firewall-domains \
    --firewall-domain-list-id <value> \
    --operation <value> \
    --domain-file-url <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-domain-list-id` | **Yes** | string | -- | The domain list ID (max 64 chars) |
| `--operation` | **Yes** | string | -- | `REPLACE` (replaces all domains in the list) |
| `--domain-file-url` | **Yes** | string | -- | S3 URL of the file containing domains (one per line). Max 255 chars |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Status": "COMPLETE|COMPLETE_IMPORT_FAILED|IMPORTING|DELETING|UPDATING",
    "StatusMessage": "string"
}
```

---

### 3.17 `update-firewall-domains`

Adds or removes domains from a firewall domain list.

**Synopsis:**
```bash
aws route53resolver update-firewall-domains \
    --firewall-domain-list-id <value> \
    --operation <value> \
    --domains <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-domain-list-id` | **Yes** | string | -- | The domain list ID (max 64 chars) |
| `--operation` | **Yes** | string | -- | `ADD`, `REMOVE`, or `REPLACE` |
| `--domains` | **Yes** | list(string) | -- | List of domain names (max 255 chars each) |

**Output Schema:**
Same as `import-firewall-domains` output.

---

### 3.18 `create-firewall-rule`

Creates a rule in a DNS Firewall rule group. Rules match DNS queries against domain lists and take specified actions.

**Synopsis:**
```bash
aws route53resolver create-firewall-rule \
    --firewall-rule-group-id <value> \
    --priority <value> \
    --action <value> \
    --name <value> \
    [--creator-request-id <value>] \
    [--firewall-domain-list-id <value>] \
    [--block-response <value>] \
    [--block-override-domain <value>] \
    [--block-override-dns-type <value>] \
    [--block-override-ttl <value>] \
    [--firewall-domain-redirection-action <value>] \
    [--qtype <value>] \
    [--dns-threat-protection <value>] \
    [--confidence-threshold <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-id` | **Yes** | string | -- | The rule group ID (max 64 chars) |
| `--priority` | **Yes** | integer | -- | Processing order (lower = first). Must be unique in group |
| `--action` | **Yes** | string | -- | `ALLOW`, `BLOCK`, or `ALERT` |
| `--name` | **Yes** | string | -- | Rule name (max 64 chars) |
| `--creator-request-id` | No | string | None | Idempotency token (max 255 chars) |
| `--firewall-domain-list-id` | No | string | None | Domain list ID. Cannot use with `--dns-threat-protection` |
| `--block-response` | No | string | None | Required for BLOCK: `NODATA`, `NXDOMAIN`, or `OVERRIDE` |
| `--block-override-domain` | No | string | None | Custom domain for OVERRIDE response (max 255 chars) |
| `--block-override-dns-type` | No | string | None | DNS type for override: `CNAME` |
| `--block-override-ttl` | No | integer | None | TTL for override record (0-604800 seconds) |
| `--firewall-domain-redirection-action` | No | string | None | `INSPECT_REDIRECTION_DOMAIN` or `TRUST_REDIRECTION_DOMAIN` |
| `--qtype` | No | string | None | DNS query type filter: `A`, `AAAA`, `CNAME`, `MX`, etc. |
| `--dns-threat-protection` | No | string | None | Advanced: `DGA`, `DNS_TUNNELING`, or `DICTIONARY_DGA` |
| `--confidence-threshold` | No | string | None | For advanced rules: `LOW`, `MEDIUM`, or `HIGH` |

**Output Schema:**
```json
{
    "FirewallRule": {
        "FirewallRuleGroupId": "string",
        "FirewallDomainListId": "string",
        "FirewallThreatProtectionId": "string",
        "Name": "string",
        "Priority": "integer",
        "Action": "ALLOW|BLOCK|ALERT",
        "BlockResponse": "NODATA|NXDOMAIN|OVERRIDE",
        "BlockOverrideDomain": "string",
        "BlockOverrideDnsType": "CNAME",
        "BlockOverrideTtl": "integer",
        "CreatorRequestId": "string",
        "CreationTime": "string",
        "ModificationTime": "string",
        "FirewallDomainRedirectionAction": "INSPECT_REDIRECTION_DOMAIN|TRUST_REDIRECTION_DOMAIN",
        "Qtype": "string",
        "DnsThreatProtection": "DGA|DNS_TUNNELING|DICTIONARY_DGA",
        "ConfidenceThreshold": "LOW|MEDIUM|HIGH"
    }
}
```

---

### 3.19 `delete-firewall-rule`

Deletes a rule from a DNS Firewall rule group.

**Synopsis:**
```bash
aws route53resolver delete-firewall-rule \
    --firewall-rule-group-id <value> \
    [--firewall-domain-list-id <value>] \
    [--firewall-threat-protection-id <value>] \
    [--qtype <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-id` | **Yes** | string | -- | The rule group ID (max 64 chars) |
| `--firewall-domain-list-id` | No | string | None | Domain list ID of the rule to delete |
| `--firewall-threat-protection-id` | No | string | None | Threat protection ID of the rule to delete |
| `--qtype` | No | string | None | DNS query type of the rule to delete |

**Output Schema:**
Same as `create-firewall-rule` output.

---

### 3.20 `list-firewall-rules`

Lists rules in a DNS Firewall rule group. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-firewall-rules \
    --firewall-rule-group-id <value> \
    [--priority <value>] \
    [--action <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-id` | **Yes** | string | -- | The rule group ID (max 64 chars) |
| `--priority` | No | integer | None | Filter by priority |
| `--action` | No | string | None | Filter: `ALLOW`, `BLOCK`, `ALERT` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FirewallRules": [{"...same as FirewallRule above..."}],
    "NextToken": "string"
}
```

---

### 3.21 `update-firewall-rule`

Updates a DNS Firewall rule (action, priority, block response, etc.).

**Synopsis:**
```bash
aws route53resolver update-firewall-rule \
    --firewall-rule-group-id <value> \
    [--firewall-domain-list-id <value>] \
    [--firewall-threat-protection-id <value>] \
    [--priority <value>] \
    [--action <value>] \
    [--block-response <value>] \
    [--block-override-domain <value>] \
    [--block-override-dns-type <value>] \
    [--block-override-ttl <value>] \
    [--name <value>] \
    [--qtype <value>] \
    [--dns-threat-protection <value>] \
    [--confidence-threshold <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-id` | **Yes** | string | -- | The rule group ID (max 64 chars) |
| `--firewall-domain-list-id` | No | string | None | Domain list ID of the rule |
| `--firewall-threat-protection-id` | No | string | None | Threat protection ID of the rule |
| `--priority` | No | integer | None | New processing priority |
| `--action` | No | string | None | New action: `ALLOW`, `BLOCK`, `ALERT` |
| `--block-response` | No | string | None | New block response: `NODATA`, `NXDOMAIN`, `OVERRIDE` |
| `--block-override-domain` | No | string | None | New override domain |
| `--block-override-dns-type` | No | string | None | New override DNS type: `CNAME` |
| `--block-override-ttl` | No | integer | None | New override TTL |
| `--name` | No | string | None | New rule name |
| `--qtype` | No | string | None | DNS query type filter |
| `--dns-threat-protection` | No | string | None | `DGA`, `DNS_TUNNELING`, `DICTIONARY_DGA` |
| `--confidence-threshold` | No | string | None | `LOW`, `MEDIUM`, `HIGH` |

**Output Schema:**
Same as `create-firewall-rule` output.

---

### 3.22 `update-firewall-rule-group-association`

Updates a firewall rule group association's priority or mutation protection.

**Synopsis:**
```bash
aws route53resolver update-firewall-rule-group-association \
    --firewall-rule-group-association-id <value> \
    [--priority <value>] \
    [--mutation-protection <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-rule-group-association-id` | **Yes** | string | -- | The association ID (max 64 chars) |
| `--priority` | No | integer | None | New processing priority |
| `--mutation-protection` | No | string | None | `ENABLED` or `DISABLED` |

**Output Schema:**
Same as `associate-firewall-rule-group` output.

---

### 3.23 `get-firewall-config`

Gets the DNS Firewall configuration for a VPC (fail-open behavior).

**Synopsis:**
```bash
aws route53resolver get-firewall-config \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |

**Output Schema:**
```json
{
    "FirewallConfig": {
        "Id": "string",
        "ResourceId": "string",
        "OwnerId": "string",
        "FirewallFailOpen": "ENABLED|DISABLED|USE_LOCAL_RESOURCE_SETTING"
    }
}
```

---

### 3.24 `list-firewall-configs`

Lists DNS Firewall configs for all VPCs. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-firewall-configs \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FirewallConfigs": [{"...same as FirewallConfig above..."}],
    "NextToken": "string"
}
```

---

### 3.25 `update-firewall-config`

Updates the DNS Firewall fail-open configuration for a VPC. When fail-open is enabled, DNS queries are allowed even if Firewall cannot inspect them.

**Synopsis:**
```bash
aws route53resolver update-firewall-config \
    --resource-id <value> \
    --firewall-fail-open <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |
| `--firewall-fail-open` | **Yes** | string | -- | `ENABLED`, `DISABLED`, or `USE_LOCAL_RESOURCE_SETTING` |

**Output Schema:**
Same as `get-firewall-config` output.
