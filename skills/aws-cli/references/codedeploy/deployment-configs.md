# Deployment Configs

### 4.1 `create-deployment-config`

Creates a deployment configuration.

**Synopsis:**
```bash
aws deploy create-deployment-config \
    --deployment-config-name <value> \
    [--minimum-healthy-hosts <value>] \
    [--traffic-routing-config <value>] \
    [--compute-platform <value>] \
    [--zonal-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-config-name` | **Yes** | string | -- | Deployment configuration name |
| `--minimum-healthy-hosts` | No | structure | None | Minimum healthy hosts (Server platform). Shorthand: `type=HOST_COUNT\|FLEET_PERCENT,value=integer` |
| `--traffic-routing-config` | No | structure | None | Traffic routing configuration (ECS/Lambda platforms) |
| `--compute-platform` | No | string | `Server` | Compute platform: `Server`, `Lambda`, `ECS` |
| `--zonal-config` | No | structure | None | Zonal deployment configuration |

**Traffic Routing Config Structure:**
```json
{
    "type": "TimeBasedCanary|TimeBasedLinear|AllAtOnce",
    "timeBasedCanary": {
        "canaryPercentage": "integer",
        "canaryInterval": "integer"
    },
    "timeBasedLinear": {
        "linearPercentage": "integer",
        "linearInterval": "integer"
    }
}
```

**Zonal Config Structure:**
```json
{
    "firstZoneMonitorDurationInSeconds": "long",
    "monitorDurationInSeconds": "long",
    "minimumHealthyHostsPerZone": {
        "type": "HOST_COUNT|FLEET_PERCENT",
        "value": "integer"
    }
}
```

**Output Schema:**
```json
{
    "deploymentConfigId": "string"
}
```

---

### 4.2 `delete-deployment-config`

Deletes a deployment configuration. Cannot delete built-in configurations or configurations in use by a deployment group.

**Synopsis:**
```bash
aws deploy delete-deployment-config \
    --deployment-config-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-config-name` | **Yes** | string | -- | Deployment configuration name |

**Output Schema:**
```json
{}
```

---

### 4.3 `get-deployment-config`

Gets information about a deployment configuration.

**Synopsis:**
```bash
aws deploy get-deployment-config \
    --deployment-config-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-config-name` | **Yes** | string | -- | Deployment configuration name |

**Output Schema:**
```json
{
    "deploymentConfigInfo": {
        "deploymentConfigId": "string",
        "deploymentConfigName": "string",
        "minimumHealthyHosts": {
            "type": "HOST_COUNT|FLEET_PERCENT",
            "value": "integer"
        },
        "createTime": "timestamp",
        "computePlatform": "Server|Lambda|ECS",
        "trafficRoutingConfig": {
            "type": "TimeBasedCanary|TimeBasedLinear|AllAtOnce",
            "timeBasedCanary": {
                "canaryPercentage": "integer",
                "canaryInterval": "integer"
            },
            "timeBasedLinear": {
                "linearPercentage": "integer",
                "linearInterval": "integer"
            }
        },
        "zonalConfig": {
            "firstZoneMonitorDurationInSeconds": "long",
            "monitorDurationInSeconds": "long",
            "minimumHealthyHostsPerZone": {
                "type": "HOST_COUNT|FLEET_PERCENT",
                "value": "integer"
            }
        }
    }
}
```

---

### 4.4 `list-deployment-configs`

Lists the deployment configurations in the account. **Paginated operation.**

**Synopsis:**
```bash
aws deploy list-deployment-configs \
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
    "deploymentConfigsList": ["string"],
    "nextToken": "string"
}
```
