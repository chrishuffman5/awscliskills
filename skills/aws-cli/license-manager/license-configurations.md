# License Configurations

### 1.1 `create-license-configuration`

Creates a license configuration for tracking license usage.

**Synopsis:**
```bash
aws license-manager create-license-configuration \
    --name <value> \
    --license-counting-type <value> \
    [--description <value>] \
    [--license-count <value>] \
    [--license-count-hard-limit | --no-license-count-hard-limit] \
    [--license-rules <value>] \
    [--tags <value>] \
    [--disassociate-when-not-found | --no-disassociate-when-not-found] \
    [--product-information-list <value>] \
    [--license-expiry <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the license configuration |
| `--license-counting-type` | **Yes** | string | -- | Dimension: `vCPU`, `Instance`, `Core`, or `Socket` |
| `--description` | No | string | None | Description of the license configuration |
| `--license-count` | No | long | None | Number of licenses managed |
| `--license-count-hard-limit` | No | boolean | false | Hard limit blocks launch; soft limit allows launch |
| `--license-rules` | No | list(string) | None | License rules in `#name=value` format |
| `--tags` | No | list | None | Tags (Key/Value pairs) |
| `--disassociate-when-not-found` | No | boolean | false | Disassociate resource when software is uninstalled |
| `--product-information-list` | No | list | None | Product information with resource type and filters |
| `--license-expiry` | No | long | None | License configuration expiry time |

**Output Schema:**
```json
{
    "LicenseConfigurationArn": "string"
}
```

---

### 1.2 `delete-license-configuration`

Deletes the specified license configuration. Cannot delete if in use.

**Synopsis:**
```bash
aws license-manager delete-license-configuration \
    --license-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-configuration-arn` | **Yes** | string | -- | ARN of the license configuration to delete |

**Output:** None

---

### 1.3 `get-license-configuration`

Gets detailed information about a license configuration.

**Synopsis:**
```bash
aws license-manager get-license-configuration \
    --license-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-configuration-arn` | **Yes** | string | -- | ARN of the license configuration |

**Output Schema:**
```json
{
    "LicenseConfigurationId": "string",
    "LicenseConfigurationArn": "string",
    "Name": "string",
    "Description": "string",
    "LicenseCountingType": "vCPU|Instance|Core|Socket",
    "LicenseRules": ["string"],
    "LicenseCount": "long",
    "LicenseCountHardLimit": "boolean",
    "ConsumedLicenses": "long",
    "Status": "string",
    "OwnerAccountId": "string",
    "ConsumedLicenseSummaryList": [
        {
            "ResourceType": "EC2_INSTANCE|EC2_HOST|EC2_AMI|RDS|SYSTEMS_MANAGER_MANAGED_INSTANCE",
            "ConsumedLicenses": "long"
        }
    ],
    "ManagedResourceSummaryList": [
        {
            "ResourceType": "EC2_INSTANCE|EC2_HOST|EC2_AMI|RDS|SYSTEMS_MANAGER_MANAGED_INSTANCE",
            "AssociationCount": "long"
        }
    ],
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "ProductInformationList": [
        {
            "ResourceType": "SSM_MANAGED|RDS",
            "ProductInformationFilterList": [
                {
                    "ProductInformationFilterName": "string",
                    "ProductInformationFilterValue": ["string"],
                    "ProductInformationFilterComparator": "string"
                }
            ]
        }
    ],
    "AutomatedDiscoveryInformation": {
        "LastRunTime": "timestamp"
    },
    "DisassociateWhenNotFound": "boolean",
    "LicenseExpiry": "long"
}
```

---

### 1.4 `list-license-configurations`

Lists license configurations. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-license-configurations \
    [--license-configuration-arns <value>] \
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
| `--license-configuration-arns` | No | list(string) | None | ARNs to filter by |
| `--filters` | No | list | None | Filters: `licenseCountingType`, `enforceLicenseCount`, `usagelimitExceeded` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseConfigurations": [
        {
            "LicenseConfigurationId": "string",
            "LicenseConfigurationArn": "string",
            "Name": "string",
            "Description": "string",
            "LicenseCountingType": "vCPU|Instance|Core|Socket",
            "LicenseRules": ["string"],
            "LicenseCount": "long",
            "LicenseCountHardLimit": "boolean",
            "ConsumedLicenses": "long",
            "Status": "string",
            "OwnerAccountId": "string",
            "ConsumedLicenseSummaryList": [],
            "ManagedResourceSummaryList": []
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-license-configuration`

Modifies the attributes of an existing license configuration.

**Synopsis:**
```bash
aws license-manager update-license-configuration \
    --license-configuration-arn <value> \
    [--license-configuration-status <value>] \
    [--license-rules <value>] \
    [--license-count <value>] \
    [--license-count-hard-limit | --no-license-count-hard-limit] \
    [--name <value>] \
    [--description <value>] \
    [--product-information-list <value>] \
    [--disassociate-when-not-found | --no-disassociate-when-not-found] \
    [--license-expiry <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-configuration-arn` | **Yes** | string | -- | ARN of the license configuration |
| `--license-configuration-status` | No | string | None | New status: `AVAILABLE` or `DISABLED` |
| `--license-rules` | No | list(string) | None | License rules in `#name=value` format |
| `--license-count` | No | long | None | New license count |
| `--license-count-hard-limit` | No | boolean | None | Hard/soft limit toggle |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--product-information-list` | No | list | None | Product information filters |
| `--disassociate-when-not-found` | No | boolean | None | Disassociate on uninstall |
| `--license-expiry` | No | long | None | License expiry time |

**Output:** None

---

### 1.6 `list-license-configurations-for-organization`

Lists license configurations across the organization. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-license-configurations-for-organization \
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
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseConfigurations": [],
    "NextToken": "string"
}
```

---

### 1.7 `list-usage-for-license-configuration`

Lists usage records for a license configuration. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-usage-for-license-configuration \
    --license-configuration-arn <value> \
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
| `--license-configuration-arn` | **Yes** | string | -- | ARN of the license configuration |
| `--filters` | No | list | None | Filters: `resourceArn`, `resourceType`, `resourceAccount` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseConfigurationUsageList": [
        {
            "ResourceArn": "string",
            "ResourceType": "EC2_INSTANCE|EC2_HOST|EC2_AMI|RDS|SYSTEMS_MANAGER_MANAGED_INSTANCE",
            "ResourceStatus": "string",
            "ResourceOwnerId": "string",
            "AssociationTime": "timestamp",
            "ConsumedLicenses": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.8 `list-associations-for-license-configuration`

Lists resource associations for a license configuration. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-associations-for-license-configuration \
    --license-configuration-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-configuration-arn` | **Yes** | string | -- | ARN of the license configuration |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseConfigurationAssociations": [
        {
            "ResourceArn": "string",
            "ResourceType": "EC2_INSTANCE|EC2_HOST|EC2_AMI|RDS|SYSTEMS_MANAGER_MANAGED_INSTANCE",
            "ResourceOwnerId": "string",
            "AssociationTime": "timestamp",
            "AmiAssociationScope": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.9 `list-failures-for-license-configuration-operations`

Lists failures for license configuration operations. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-failures-for-license-configuration-operations \
    --license-configuration-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-configuration-arn` | **Yes** | string | -- | ARN of the license configuration |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseOperationFailureList": [
        {
            "ResourceArn": "string",
            "ResourceType": "EC2_INSTANCE|EC2_HOST|EC2_AMI|RDS|SYSTEMS_MANAGER_MANAGED_INSTANCE",
            "ErrorMessage": "string",
            "FailureTime": "timestamp",
            "OperationName": "string",
            "ResourceOwnerId": "string",
            "OperationRequestedBy": "string",
            "MetadataList": [
                {
                    "Name": "string",
                    "Value": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 1.10 `update-license-specifications-for-resource`

Adds or removes license specifications for a resource.

**Synopsis:**
```bash
aws license-manager update-license-specifications-for-resource \
    --resource-arn <value> \
    [--add-license-specifications <value>] \
    [--remove-license-specifications <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the AWS resource |
| `--add-license-specifications` | No | list | None | License configurations to add. Shorthand: `LicenseConfigurationArn=string ...` |
| `--remove-license-specifications` | No | list | None | License configurations to remove. Shorthand: `LicenseConfigurationArn=string ...` |

**Output:** None

---

### 1.11 `list-license-specifications-for-resource`

Lists license specifications for a resource. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-license-specifications-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseSpecifications": [
        {
            "LicenseConfigurationArn": "string",
            "AmiAssociationScope": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.12 `list-resource-inventory`

Lists resources managed with license configurations. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-resource-inventory \
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
| `--filters` | No | list | None | Filters: `platform`, `resource_id`, `account_id`, `tag:Key` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceInventoryList": [
        {
            "ResourceId": "string",
            "ResourceType": "EC2_INSTANCE|EC2_HOST|EC2_AMI|RDS|SYSTEMS_MANAGER_MANAGED_INSTANCE",
            "ResourceArn": "string",
            "Platform": "string",
            "PlatformVersion": "string",
            "ResourceOwningAccountId": "string"
        }
    ],
    "NextToken": "string"
}
```
