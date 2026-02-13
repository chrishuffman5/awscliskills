# DNSSEC & Resolver Config

### 5.1 `get-resolver-dnssec-config`

Gets the DNSSEC validation configuration for a VPC.

**Synopsis:**
```bash
aws route53resolver get-resolver-dnssec-config \
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
    "ResolverDNSSECConfig": {
        "Id": "string",
        "OwnerId": "string",
        "ResourceId": "string",
        "ValidationStatus": "ENABLING|ENABLED|DISABLING|DISABLED|UPDATING_TO_USE_LOCAL_RESOURCE_SETTING|USE_LOCAL_RESOURCE_SETTING"
    }
}
```

---

### 5.2 `list-resolver-dnssec-configs`

Lists DNSSEC validation configurations for all VPCs. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-resolver-dnssec-configs \
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

**Output Schema:**
```json
{
    "ResolverDnssecConfigs": [{"...same as ResolverDNSSECConfig above..."}],
    "NextToken": "string"
}
```

---

### 5.3 `update-resolver-dnssec-config`

Enables or disables DNSSEC validation for a VPC. When enabled, Route 53 Resolver validates DNSSEC signatures for domains that support DNSSEC, and returns SERVFAIL for responses with invalid signatures.

**Synopsis:**
```bash
aws route53resolver update-resolver-dnssec-config \
    --resource-id <value> \
    --validation <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |
| `--validation` | **Yes** | string | -- | `ENABLE`, `DISABLE`, or `USE_LOCAL_RESOURCE_SETTING` |

**Output Schema:**
Same as `get-resolver-dnssec-config` output.

---

### 5.4 `get-resolver-config`

Gets the Resolver configuration for a VPC, including autodefined reverse DNS settings.

**Synopsis:**
```bash
aws route53resolver get-resolver-config \
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
    "ResolverConfig": {
        "Id": "string",
        "ResourceId": "string",
        "OwnerId": "string",
        "AutodefinedReverse": "ENABLING|ENABLED|DISABLING|DISABLED|UPDATING_TO_USE_LOCAL_RESOURCE_SETTING|USE_LOCAL_RESOURCE_SETTING"
    }
}
```

---

### 5.5 `list-resolver-configs`

Lists Resolver configurations for all VPCs. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-resolver-configs \
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
    "ResolverConfigs": [{"...same as ResolverConfig above..."}],
    "NextToken": "string"
}
```

---

### 5.6 `update-resolver-config`

Updates the autodefined reverse DNS configuration for a VPC. Controls whether Route 53 Resolver automatically creates reverse DNS records for EC2 instances.

**Synopsis:**
```bash
aws route53resolver update-resolver-config \
    --resource-id <value> \
    --autodefined-reverse-flag <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |
| `--autodefined-reverse-flag` | **Yes** | string | -- | `ENABLE`, `DISABLE`, or `USE_LOCAL_RESOURCE_SETTING` |

**Output Schema:**
Same as `get-resolver-config` output.
