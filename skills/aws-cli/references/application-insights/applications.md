# Applications

### 1.1 `create-application`

Creates an Application Insights monitoring application from a resource group.

**Synopsis:**
```bash
aws application-insights create-application \
    --resource-group-name <value> \
    [--ops-center-enabled | --no-ops-center-enabled] \
    [--cwe-monitor-enabled | --no-cwe-monitor-enabled] \
    [--ops-item-sns-topic-arn <value>] \
    [--sns-notification-arn <value>] \
    [--tags <value>] \
    [--auto-config-enabled | --no-auto-config-enabled] \
    [--auto-create | --no-auto-create] \
    [--grouping-type <value>] \
    [--attach-missing-permission | --no-attach-missing-permission] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--ops-center-enabled` | No | boolean | false | Enable OpsCenter integration |
| `--cwe-monitor-enabled` | No | boolean | false | Enable CloudWatch Events monitoring |
| `--ops-item-sns-topic-arn` | No | string | -- | SNS topic ARN for OpsItem notifications |
| `--sns-notification-arn` | No | string | -- | SNS topic ARN for notifications |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--auto-config-enabled` | No | boolean | false | Enable auto-configuration |
| `--auto-create` | No | boolean | false | Auto-create application for all resources in account |
| `--grouping-type` | No | string | -- | Grouping type: `ACCOUNT_BASED` |
| `--attach-missing-permission` | No | boolean | false | Attach missing IAM permissions |

**Output Schema:**
```json
{
    "ApplicationInfo": {
        "AccountId": "string",
        "ResourceGroupName": "string",
        "LifeCycle": "string",
        "OpsItemSNSTopicArn": "string",
        "SNSNotificationArn": "string",
        "OpsCenterEnabled": "boolean",
        "CWEMonitorEnabled": "boolean",
        "Remarks": "string",
        "AutoConfigEnabled": "boolean",
        "DiscoveryType": "RESOURCE_GROUP_BASED|ACCOUNT_BASED",
        "AttachMissingPermission": "boolean"
    }
}
```

---

### 1.2 `delete-application`

Removes the specified application from monitoring.

**Synopsis:**
```bash
aws application-insights delete-application \
    --resource-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-application`

Describes the application.

**Synopsis:**
```bash
aws application-insights describe-application \
    --resource-group-name <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--account-id` | No | string | -- | AWS account ID (for cross-account) |

**Output Schema:**
```json
{
    "ApplicationInfo": {
        "AccountId": "string",
        "ResourceGroupName": "string",
        "LifeCycle": "string",
        "OpsItemSNSTopicArn": "string",
        "SNSNotificationArn": "string",
        "OpsCenterEnabled": "boolean",
        "CWEMonitorEnabled": "boolean",
        "Remarks": "string",
        "AutoConfigEnabled": "boolean",
        "DiscoveryType": "RESOURCE_GROUP_BASED|ACCOUNT_BASED",
        "AttachMissingPermission": "boolean"
    }
}
```

---

### 1.4 `list-applications`

Lists all applications monitored by Application Insights. **Paginated operation.**

**Synopsis:**
```bash
aws application-insights list-applications \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | No | string | -- | AWS account ID (for cross-account) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ApplicationInfoList": [
        {
            "AccountId": "string",
            "ResourceGroupName": "string",
            "LifeCycle": "string",
            "OpsItemSNSTopicArn": "string",
            "SNSNotificationArn": "string",
            "OpsCenterEnabled": "boolean",
            "CWEMonitorEnabled": "boolean",
            "Remarks": "string",
            "AutoConfigEnabled": "boolean",
            "DiscoveryType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-application`

Updates the application settings.

**Synopsis:**
```bash
aws application-insights update-application \
    --resource-group-name <value> \
    [--ops-center-enabled | --no-ops-center-enabled] \
    [--cwe-monitor-enabled | --no-cwe-monitor-enabled] \
    [--ops-item-sns-topic-arn <value>] \
    [--sns-notification-arn <value>] \
    [--remove-sns-topic | --no-remove-sns-topic] \
    [--auto-config-enabled | --no-auto-config-enabled] \
    [--attach-missing-permission | --no-attach-missing-permission] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--ops-center-enabled` | No | boolean | -- | Enable/disable OpsCenter integration |
| `--cwe-monitor-enabled` | No | boolean | -- | Enable/disable CloudWatch Events monitoring |
| `--ops-item-sns-topic-arn` | No | string | -- | SNS topic ARN for OpsItem notifications |
| `--sns-notification-arn` | No | string | -- | SNS topic ARN for notifications |
| `--remove-sns-topic` | No | boolean | false | Remove SNS topic |
| `--auto-config-enabled` | No | boolean | -- | Enable/disable auto-configuration |
| `--attach-missing-permission` | No | boolean | -- | Attach missing IAM permissions |

**Output Schema:**
```json
{
    "ApplicationInfo": {
        "AccountId": "string",
        "ResourceGroupName": "string",
        "LifeCycle": "string",
        "OpsItemSNSTopicArn": "string",
        "SNSNotificationArn": "string",
        "OpsCenterEnabled": "boolean",
        "CWEMonitorEnabled": "boolean",
        "Remarks": "string",
        "AutoConfigEnabled": "boolean",
        "DiscoveryType": "string",
        "AttachMissingPermission": "boolean"
    }
}
```
