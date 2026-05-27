# Components

### 2.1 `create-component`

Creates a custom component by grouping similar standalone instances together.

**Synopsis:**
```bash
aws application-insights create-component \
    --resource-group-name <value> \
    --component-name <value> \
    --resource-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the custom component |
| `--resource-list` | **Yes** | list(string) | -- | List of resource ARNs to group |

**Output Schema:**
```json
{}
```

---

### 2.2 `delete-component`

Ungroups a custom component.

**Synopsis:**
```bash
aws application-insights delete-component \
    --resource-group-name <value> \
    --component-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-component`

Describes a component and lists the resources that are grouped together in a component.

**Synopsis:**
```bash
aws application-insights describe-component \
    --resource-group-name <value> \
    --component-name <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--account-id` | No | string | -- | AWS account ID (for cross-account) |

**Output Schema:**
```json
{
    "ApplicationComponent": {
        "ComponentName": "string",
        "ComponentRemarks": "string",
        "ResourceType": "string",
        "OsType": "WINDOWS|LINUX",
        "Tier": "string",
        "Monitor": "boolean",
        "DetectedWorkload": {
            "string": {
                "string": "string"
            }
        }
    },
    "ResourceList": ["string"]
}
```

---

### 2.4 `list-components`

Lists the auto-grouped and custom components of the application. **Paginated operation.**

**Synopsis:**
```bash
aws application-insights list-components \
    --resource-group-name <value> \
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
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--account-id` | No | string | -- | AWS account ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ApplicationComponentList": [
        {
            "ComponentName": "string",
            "ComponentRemarks": "string",
            "ResourceType": "string",
            "OsType": "WINDOWS|LINUX",
            "Tier": "string",
            "Monitor": "boolean",
            "DetectedWorkload": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-component`

Updates the custom component name and/or the list of resources.

**Synopsis:**
```bash
aws application-insights update-component \
    --resource-group-name <value> \
    --component-name <value> \
    [--new-component-name <value>] \
    [--resource-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Current name of the component |
| `--new-component-name` | No | string | -- | New name for the component |
| `--resource-list` | No | list(string) | -- | Updated list of resource ARNs |

**Output Schema:**
```json
{}
```

---

### 2.6 `describe-component-configuration`

Describes the monitoring configuration of the component.

**Synopsis:**
```bash
aws application-insights describe-component-configuration \
    --resource-group-name <value> \
    --component-name <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--account-id` | No | string | -- | AWS account ID |

**Output Schema:**
```json
{
    "Monitor": "boolean",
    "Tier": "string",
    "ComponentConfiguration": "string"
}
```

---

### 2.7 `describe-component-configuration-recommendation`

Describes the recommended monitoring configuration for the component.

**Synopsis:**
```bash
aws application-insights describe-component-configuration-recommendation \
    --resource-group-name <value> \
    --component-name <value> \
    --tier <value> \
    [--workload-name <value>] \
    [--recommendation-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--tier` | **Yes** | string | -- | Tier of the component (e.g., `SQL_SERVER`, `DOT_NET_CORE`) |
| `--workload-name` | No | string | -- | Name of the workload |
| `--recommendation-type` | No | string | -- | Recommendation type: `INFRA_ONLY`, `WORKLOAD_ONLY`, `ALL` |

**Output Schema:**
```json
{
    "ComponentConfiguration": "string"
}
```

---

### 2.8 `update-component-configuration`

Updates the monitoring configuration for the component.

**Synopsis:**
```bash
aws application-insights update-component-configuration \
    --resource-group-name <value> \
    --component-name <value> \
    [--monitor | --no-monitor] \
    [--tier <value>] \
    [--component-configuration <value>] \
    [--auto-config-enabled | --no-auto-config-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--monitor` | No | boolean | -- | Enable or disable monitoring |
| `--tier` | No | string | -- | Tier of the component |
| `--component-configuration` | No | string | -- | JSON configuration string |
| `--auto-config-enabled` | No | boolean | -- | Enable auto-configuration |

**Output Schema:**
```json
{}
```
