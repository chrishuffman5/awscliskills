# Linux Subscriptions

> All commands in this file use the `aws license-manager-linux-subscriptions` namespace.

### 8.1 `list-linux-subscriptions`

Lists Linux subscriptions discovered in your account. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager-linux-subscriptions list-linux-subscriptions \
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
| `--filters` | No | list | None | Filters: `Subscription` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Subscriptions": [
        {
            "Name": "string",
            "Type": "string",
            "InstanceCount": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.2 `list-linux-subscription-instances`

Lists EC2 instances running Linux subscriptions. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager-linux-subscriptions list-linux-subscription-instances \
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
| `--filters` | No | list | None | Filters: `AmiId`, `InstanceID`, `Region`, `AccountID`, `Status`, `DualSubscription`, `UsageOperation`, `ProductCode`, `SubscriptionProviderSource` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Instances": [
        {
            "InstanceID": "string",
            "AmiId": "string",
            "Region": "string",
            "AccountID": "string",
            "Status": "string",
            "InstanceType": "string",
            "ProductCode": ["string"],
            "UsageOperation": "string",
            "SubscriptionName": "string",
            "SubscriptionProviderCreateTime": "string",
            "SubscriptionProviderUpdateTime": "string",
            "DualSubscription": "string",
            "OsVersion": "string",
            "LastUpdatedTime": "string",
            "RegisteredWithSubscriptionProvider": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.3 `register-subscription-provider`

Registers a third-party subscription provider (currently RedHat) for BYOL subscriptions.

**Synopsis:**
```bash
aws license-manager-linux-subscriptions register-subscription-provider \
    --subscription-provider-source <value> \
    --secret-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-provider-source` | **Yes** | string | -- | Provider to register: `RedHat` |
| `--secret-arn` | **Yes** | string | -- | ARN of the Secrets Manager secret containing the provider access token |
| `--tags` | No | map | None | Tags (max 50). Format: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "SubscriptionProviderArn": "string",
    "SubscriptionProviderSource": "RedHat",
    "SubscriptionProviderStatus": "ACTIVE|INVALID|PENDING"
}
```

---

### 8.4 `deregister-subscription-provider`

Deregisters a subscription provider.

**Synopsis:**
```bash
aws license-manager-linux-subscriptions deregister-subscription-provider \
    --subscription-provider-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-provider-arn` | **Yes** | string | -- | ARN of the subscription provider |

**Output:** None

---

### 8.5 `get-registered-subscription-provider`

Gets details of a registered subscription provider.

**Synopsis:**
```bash
aws license-manager-linux-subscriptions get-registered-subscription-provider \
    --subscription-provider-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-provider-arn` | **Yes** | string | -- | ARN of the subscription provider |

**Output Schema:**
```json
{
    "SubscriptionProviderArn": "string",
    "SubscriptionProviderSource": "RedHat",
    "SubscriptionProviderStatus": "ACTIVE|INVALID|PENDING",
    "SubscriptionProviderStatusMessage": "string",
    "SecretArn": "string",
    "LastSuccessfulDataRetrievalTime": "string"
}
```

---

### 8.6 `list-registered-subscription-providers`

Lists registered subscription providers. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager-linux-subscriptions list-registered-subscription-providers \
    [--subscription-provider-sources <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-provider-sources` | No | list(string) | None | Filter by source: `RedHat` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegisteredSubscriptionProviders": [
        {
            "SubscriptionProviderArn": "string",
            "SubscriptionProviderSource": "RedHat",
            "SubscriptionProviderStatus": "ACTIVE|INVALID|PENDING",
            "SecretArn": "string",
            "LastSuccessfulDataRetrievalTime": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.7 `get-service-settings`

Gets the Linux Subscriptions service settings.

**Synopsis:**
```bash
aws license-manager-linux-subscriptions get-service-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "LinuxSubscriptionsDiscovery": "Enabled|Disabled",
    "LinuxSubscriptionsDiscoverySettings": {
        "SourceRegions": ["string"],
        "OrganizationIntegration": "Enabled|Disabled"
    },
    "Status": "Completed|InProgress|Failed",
    "StatusMessage": {},
    "HomeRegions": ["string"]
}
```

---

### 8.8 `update-service-settings`

Updates the Linux Subscriptions service settings.

**Synopsis:**
```bash
aws license-manager-linux-subscriptions update-service-settings \
    --linux-subscriptions-discovery <value> \
    --linux-subscriptions-discovery-settings <value> \
    [--allow-update | --no-allow-update] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--linux-subscriptions-discovery` | **Yes** | string | -- | `Enabled` or `Disabled` |
| `--linux-subscriptions-discovery-settings` | **Yes** | structure | -- | Settings: `SourceRegions` and `OrganizationIntegration` |
| `--allow-update` | No | boolean | None | Allow updating settings that require reconfiguration |

**Discovery Settings Structure:**
```json
{
    "SourceRegions": ["string"],
    "OrganizationIntegration": "Enabled|Disabled"
}
```

**Output Schema:**
```json
{
    "LinuxSubscriptionsDiscovery": "Enabled|Disabled",
    "LinuxSubscriptionsDiscoverySettings": {
        "SourceRegions": ["string"],
        "OrganizationIntegration": "Enabled|Disabled"
    },
    "Status": "Completed|InProgress|Failed",
    "StatusMessage": {},
    "HomeRegions": ["string"]
}
```
