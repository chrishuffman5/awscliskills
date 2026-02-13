# Firewalls

### 1.1 `create-firewall`

Creates a Network Firewall in a VPC with endpoints in specified subnets.

**Synopsis:**
```bash
aws network-firewall create-firewall \
    --firewall-name <value> \
    --firewall-policy-arn <value> \
    [--vpc-id <value>] \
    [--subnet-mappings <value>] \
    [--delete-protection | --no-delete-protection] \
    [--subnet-change-protection | --no-subnet-change-protection] \
    [--firewall-policy-change-protection | --no-firewall-policy-change-protection] \
    [--description <value>] \
    [--tags <value>] \
    [--encryption-configuration <value>] \
    [--enabled-analysis-types <value>] \
    [--transit-gateway-id <value>] \
    [--availability-zone-mappings <value>] \
    [--availability-zone-change-protection | --no-availability-zone-change-protection] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | **Yes** | string | -- | Firewall name (1-128 chars, alphanumeric and hyphens) |
| `--firewall-policy-arn` | **Yes** | string | -- | ARN of the firewall policy |
| `--vpc-id` | No | string | None | VPC ID (required for VPC-based firewalls) |
| `--subnet-mappings` | No | list | None | Subnets for firewall endpoints. Shorthand: `SubnetId=string,IPAddressType=DUALSTACK\|IPV4\|IPV6` |
| `--delete-protection` | No | boolean | true | Protect against deletion |
| `--subnet-change-protection` | No | boolean | true | Protect against subnet changes |
| `--firewall-policy-change-protection` | No | boolean | true | Protect against policy changes |
| `--description` | No | string | None | Description (max 512 chars) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string` |
| `--encryption-configuration` | No | structure | None | KMS encryption config |
| `--enabled-analysis-types` | No | list(string) | None | Analysis types: `TLS_SNI`, `HTTP_HOST` |
| `--transit-gateway-id` | No | string | None | Transit gateway ID for TGW-attached firewalls |
| `--availability-zone-mappings` | No | list | None | AZ mappings for TGW firewalls |
| `--availability-zone-change-protection` | No | boolean | false | Protect against AZ changes |

**Output Schema:**
```json
{
    "Firewall": {
        "FirewallName": "string",
        "FirewallArn": "string",
        "FirewallPolicyArn": "string",
        "VpcId": "string",
        "SubnetMappings": [
            {
                "SubnetId": "string",
                "IPAddressType": "DUALSTACK|IPV4|IPV6"
            }
        ],
        "DeleteProtection": true|false,
        "SubnetChangeProtection": true|false,
        "FirewallPolicyChangeProtection": true|false,
        "Description": "string",
        "FirewallId": "string",
        "Tags": [],
        "EncryptionConfiguration": {
            "KeyId": "string",
            "Type": "CUSTOMER_KMS|AWS_OWNED_KMS_KEY"
        },
        "EnabledAnalysisTypes": ["TLS_SNI|HTTP_HOST"],
        "TransitGatewayId": "string",
        "AvailabilityZoneMappings": [],
        "AvailabilityZoneChangeProtection": true|false
    },
    "FirewallStatus": {
        "Status": "PROVISIONING|DELETING|READY",
        "ConfigurationSyncStateSummary": "PENDING|IN_SYNC|CAPACITY_CONSTRAINED",
        "SyncStates": {}
    }
}
```

---

### 1.2 `delete-firewall`

Deletes the specified firewall and its endpoints.

**Synopsis:**
```bash
aws network-firewall delete-firewall \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |

*Must specify either `--firewall-name` or `--firewall-arn`.

**Output Schema:**
```json
{
    "Firewall": {
        "FirewallName": "string",
        "FirewallArn": "string",
        "FirewallId": "string"
    },
    "FirewallStatus": {
        "Status": "DELETING",
        "ConfigurationSyncStateSummary": "string"
    }
}
```

---

### 1.3 `describe-firewall`

Returns detailed information about the specified firewall.

**Synopsis:**
```bash
aws network-firewall describe-firewall \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |

*Must specify either `--firewall-name` or `--firewall-arn`.

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "Firewall": {
        "FirewallName": "string",
        "FirewallArn": "string",
        "FirewallPolicyArn": "string",
        "VpcId": "string",
        "SubnetMappings": [],
        "DeleteProtection": true|false,
        "SubnetChangeProtection": true|false,
        "FirewallPolicyChangeProtection": true|false,
        "Description": "string",
        "FirewallId": "string",
        "Tags": [],
        "EncryptionConfiguration": {},
        "EnabledAnalysisTypes": [],
        "TransitGatewayId": "string",
        "AvailabilityZoneMappings": [],
        "AvailabilityZoneChangeProtection": true|false
    },
    "FirewallStatus": {
        "Status": "PROVISIONING|DELETING|READY",
        "ConfigurationSyncStateSummary": "PENDING|IN_SYNC|CAPACITY_CONSTRAINED",
        "SyncStates": {
            "az": {
                "Attachment": {
                    "SubnetId": "string",
                    "EndpointId": "string",
                    "Status": "CREATING|DELETING|FAILED|ERROR|SCALING|READY",
                    "StatusMessage": "string"
                },
                "Config": {}
            }
        },
        "CapacityUsageSummary": {
            "CIDRs": {
                "AvailableCIDRCount": "integer",
                "UtilizedCIDRCount": "integer",
                "IPSetReferences": {}
            }
        }
    }
}
```

---

### 1.4 `describe-firewall-metadata`

Returns high-level metadata about a firewall without full configuration details.

**Synopsis:**
```bash
aws network-firewall describe-firewall-metadata \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallPolicyArn": "string",
    "Description": "string",
    "Status": "PROVISIONING|DELETING|READY"
}
```

---

### 1.5 `list-firewalls`

Lists all firewalls in the account. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-firewalls \
    [--vpc-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-ids` | No | list(string) | None | Filter by VPC IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Firewalls": [
        {
            "FirewallName": "string",
            "FirewallArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `update-firewall-description`

Updates the description of the specified firewall.

**Synopsis:**
```bash
aws network-firewall update-firewall-description \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--description` | No | string | None | New description (max 512 chars) |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "Description": "string",
    "UpdateToken": "string"
}
```

---

### 1.7 `update-firewall-delete-protection`

Enables or disables delete protection for the specified firewall.

**Synopsis:**
```bash
aws network-firewall update-firewall-delete-protection \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --delete-protection | --no-delete-protection \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--delete-protection` | **Yes** | boolean | -- | Enable or disable delete protection |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "DeleteProtection": true|false,
    "UpdateToken": "string"
}
```

---

### 1.8 `update-firewall-policy-change-protection`

Enables or disables firewall policy change protection.

**Synopsis:**
```bash
aws network-firewall update-firewall-policy-change-protection \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --firewall-policy-change-protection | --no-firewall-policy-change-protection \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--firewall-policy-change-protection` | **Yes** | boolean | -- | Enable or disable policy change protection |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "FirewallPolicyChangeProtection": true|false,
    "UpdateToken": "string"
}
```

---

### 1.9 `update-firewall-encryption-configuration`

Updates the encryption configuration for the specified firewall.

**Synopsis:**
```bash
aws network-firewall update-firewall-encryption-configuration \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    [--encryption-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--encryption-configuration` | No | structure | None | Encryption config: `Type=CUSTOMER_KMS\|AWS_OWNED_KMS_KEY,KeyId=string` |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "UpdateToken": "string",
    "EncryptionConfiguration": {
        "KeyId": "string",
        "Type": "CUSTOMER_KMS|AWS_OWNED_KMS_KEY"
    }
}
```

---

### 1.10 `update-firewall-analysis-settings`

Updates the traffic analysis settings for the specified firewall.

**Synopsis:**
```bash
aws network-firewall update-firewall-analysis-settings \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    [--enabled-analysis-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--enabled-analysis-types` | No | list(string) | None | Analysis types: `TLS_SNI`, `HTTP_HOST` |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "UpdateToken": "string",
    "EnabledAnalysisTypes": ["TLS_SNI|HTTP_HOST"]
}
```

---

### 1.11 `update-availability-zone-change-protection`

Enables or disables availability zone change protection for a transit gateway firewall.

**Synopsis:**
```bash
aws network-firewall update-availability-zone-change-protection \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --availability-zone-change-protection | --no-availability-zone-change-protection \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--availability-zone-change-protection` | **Yes** | boolean | -- | Enable or disable AZ change protection |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "UpdateToken": "string",
    "AvailabilityZoneChangeProtection": true|false
}
```

---

### 1.12 `associate-firewall-policy`

Associates a firewall policy with the specified firewall, replacing any existing association.

**Synopsis:**
```bash
aws network-firewall associate-firewall-policy \
    [--firewall-name <value>] \
    [--firewall-arn <value>] \
    [--update-token <value>] \
    --firewall-policy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-name` | No* | string | None | Firewall name |
| `--firewall-arn` | No* | string | None | Firewall ARN |
| `--update-token` | No | string | None | Token for optimistic locking |
| `--firewall-policy-arn` | **Yes** | string | -- | ARN of the firewall policy to associate |

**Output Schema:**
```json
{
    "FirewallArn": "string",
    "FirewallName": "string",
    "FirewallPolicyArn": "string",
    "UpdateToken": "string"
}
```
