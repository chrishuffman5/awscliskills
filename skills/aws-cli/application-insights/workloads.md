# Workloads

### 5.1 `add-workload`

Adds a workload to a component. Each component can have at most five workloads.

**Synopsis:**
```bash
aws application-insights add-workload \
    --resource-group-name <value> \
    --component-name <value> \
    --workload-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--workload-configuration` | **Yes** | structure | -- | Workload configuration. JSON: `{"Tier":"string","WorkloadName":"string","Configuration":"string"}` |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "WorkloadConfiguration": {
        "WorkloadName": "string",
        "Tier": "string",
        "Configuration": "string"
    }
}
```

---

### 5.2 `remove-workload`

Removes a workload from a component.

**Synopsis:**
```bash
aws application-insights remove-workload \
    --resource-group-name <value> \
    --component-name <value> \
    --workload-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--workload-id` | **Yes** | string | -- | ID of the workload |

**Output Schema:**
```json
{}
```

---

### 5.3 `describe-workload`

Describes a workload and its configuration.

**Synopsis:**
```bash
aws application-insights describe-workload \
    --resource-group-name <value> \
    --component-name <value> \
    --workload-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--workload-id` | **Yes** | string | -- | ID of the workload |
| `--account-id` | No | string | -- | AWS account ID |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "WorkloadRemarks": "string",
    "WorkloadConfiguration": {
        "WorkloadName": "string",
        "Tier": "string",
        "Configuration": "string"
    }
}
```

---

### 5.4 `list-workloads`

Lists the workloads that are configured on a given component. **Paginated operation.**

**Synopsis:**
```bash
aws application-insights list-workloads \
    --resource-group-name <value> \
    --component-name <value> \
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
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--account-id` | No | string | -- | AWS account ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "WorkloadList": [
        {
            "WorkloadId": "string",
            "ComponentName": "string",
            "WorkloadName": "string",
            "Tier": "string",
            "WorkloadRemarks": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `update-workload`

Updates a workload configuration.

**Synopsis:**
```bash
aws application-insights update-workload \
    --resource-group-name <value> \
    --component-name <value> \
    --workload-configuration <value> \
    [--workload-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--component-name` | **Yes** | string | -- | Name of the component |
| `--workload-configuration` | **Yes** | structure | -- | Updated workload configuration. JSON: `{"Tier":"string","WorkloadName":"string","Configuration":"string"}` |
| `--workload-id` | No | string | -- | ID of the workload |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "WorkloadConfiguration": {
        "WorkloadName": "string",
        "Tier": "string",
        "Configuration": "string"
    }
}
```
