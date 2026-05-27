# Containers

### 6.1 `create-container-service`

Creates a Lightsail container service.

**Synopsis:**
```bash
aws lightsail create-container-service \
    --service-name <value> \
    --power <value> \
    --scale <value> \
    [--tags <value>] \
    [--public-domain-names <value>] \
    [--deployment <value>] \
    [--private-registry-access <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name for the container service |
| `--power` | **Yes** | string | -- | Power: `nano`, `micro`, `small`, `medium`, `large`, `xlarge` |
| `--scale` | **Yes** | integer | -- | Number of compute nodes (1-20) |
| `--tags` | No | list | None | Tags |
| `--public-domain-names` | No | map | None | Public domains mapped to certificates |
| `--deployment` | No | structure | None | Initial deployment configuration |
| `--private-registry-access` | No | structure | None | Private ECR registry access config |

**Output Schema:**
```json
{
    "containerService": {
        "containerServiceName": "string",
        "arn": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "ContainerService",
        "tags": [],
        "power": "nano|micro|small|medium|large|xlarge",
        "powerId": "string",
        "state": "PENDING|READY|RUNNING|UPDATING|DELETING|DISABLED|DEPLOYING",
        "stateDetail": {
            "code": "CREATING_SYSTEM_RESOURCES|CREATING_NETWORK_INFRASTRUCTURE|...",
            "message": "string"
        },
        "scale": "integer",
        "currentDeployment": {},
        "nextDeployment": {},
        "isDisabled": true|false,
        "principalArn": "string",
        "privateDomainName": "string",
        "publicDomainNames": {},
        "url": "string",
        "privateRegistryAccess": {
            "ecrImagePullerRole": {
                "isActive": true|false,
                "principalArn": "string"
            }
        }
    }
}
```

---

### 6.2 `delete-container-service`

Deletes a container service.

**Synopsis:**
```bash
aws lightsail delete-container-service \
    --service-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service to delete |

**Output Schema:**
```json
{}
```

---

### 6.3 `get-container-services`

Returns information about container services.

**Synopsis:**
```bash
aws lightsail get-container-services \
    [--service-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | No | string | None | Name of a specific service (returns all if omitted) |

**Output Schema:**
```json
{
    "containerServices": [
        {
            "containerServiceName": "string",
            "arn": "string",
            "power": "string",
            "scale": "integer",
            "state": "string",
            "url": "string",
            "currentDeployment": {
                "version": "integer",
                "state": "ACTIVATING|ACTIVE|INACTIVE|FAILED",
                "containers": {},
                "publicEndpoint": {
                    "containerName": "string",
                    "containerPort": "integer",
                    "healthCheck": {}
                },
                "createdAt": "timestamp"
            }
        }
    ]
}
```

---

### 6.4 `update-container-service`

Updates the configuration of a container service.

**Synopsis:**
```bash
aws lightsail update-container-service \
    --service-name <value> \
    [--power <value>] \
    [--scale <value>] \
    [--is-disabled | --no-is-disabled] \
    [--public-domain-names <value>] \
    [--private-registry-access <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service |
| `--power` | No | string | None | New power: `nano`, `micro`, `small`, `medium`, `large`, `xlarge` |
| `--scale` | No | integer | None | New number of compute nodes |
| `--is-disabled` | No | boolean | None | Disable or enable the service |
| `--public-domain-names` | No | map | None | Public domain name mappings |
| `--private-registry-access` | No | structure | None | Private registry access config |

**Output Schema:**
```json
{
    "containerService": {
        "containerServiceName": "string",
        "arn": "string",
        "power": "string",
        "scale": "integer",
        "state": "string",
        "url": "string"
    }
}
```

---

### 6.5 `create-container-service-deployment`

Creates a deployment for a container service.

**Synopsis:**
```bash
aws lightsail create-container-service-deployment \
    --service-name <value> \
    [--containers <value>] \
    [--public-endpoint <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service |
| `--containers` | No | map | None | Container definitions. JSON: `{"name":{"image":"string","command":["string"],"environment":{"key":"value"},"ports":{"port":"HTTP\|HTTPS\|TCP\|UDP"}}}` |
| `--public-endpoint` | No | structure | None | Public endpoint. Shorthand: `containerName=string,containerPort=integer,healthCheck={...}` |

**Output Schema:**
```json
{
    "containerService": {
        "containerServiceName": "string",
        "nextDeployment": {
            "version": "integer",
            "state": "ACTIVATING|ACTIVE|INACTIVE|FAILED",
            "containers": {},
            "publicEndpoint": {},
            "createdAt": "timestamp"
        }
    }
}
```

---

### 6.6 `get-container-service-deployments`

Returns deployments for a container service.

**Synopsis:**
```bash
aws lightsail get-container-service-deployments \
    --service-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service |

**Output Schema:**
```json
{
    "deployments": [
        {
            "version": "integer",
            "state": "ACTIVATING|ACTIVE|INACTIVE|FAILED",
            "containers": {
                "string": {
                    "image": "string",
                    "command": ["string"],
                    "environment": {},
                    "ports": {}
                }
            },
            "publicEndpoint": {
                "containerName": "string",
                "containerPort": "integer",
                "healthCheck": {
                    "healthyThreshold": "integer",
                    "unhealthyThreshold": "integer",
                    "timeoutSeconds": "integer",
                    "intervalSeconds": "integer",
                    "path": "string",
                    "successCodes": "string"
                }
            },
            "createdAt": "timestamp"
        }
    ]
}
```

---

### 6.7 `get-container-service-metric-data`

Returns metric data for a container service.

**Synopsis:**
```bash
aws lightsail get-container-service-metric-data \
    --service-name <value> \
    --metric-name <value> \
    --start-time <value> \
    --end-time <value> \
    --period <value> \
    --statistics <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service |
| `--metric-name` | **Yes** | string | -- | Metric: `CPUUtilization`, `MemoryUtilization` |
| `--start-time` | **Yes** | timestamp | -- | Start time |
| `--end-time` | **Yes** | timestamp | -- | End time |
| `--period` | **Yes** | integer | -- | Granularity in seconds |
| `--statistics` | **Yes** | list(string) | -- | Statistics: `Minimum`, `Maximum`, `Sum`, `Average`, `SampleCount` |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricData": [
        {
            "average": "double",
            "maximum": "double",
            "minimum": "double",
            "sampleCount": "double",
            "sum": "double",
            "timestamp": "timestamp",
            "unit": "string"
        }
    ]
}
```

---

### 6.8 `get-container-service-powers`

Returns available container service power options.

**Synopsis:**
```bash
aws lightsail get-container-service-powers \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "powers": [
        {
            "powerId": "string",
            "price": "float",
            "cpuCount": "float",
            "ramSizeInGb": "float",
            "name": "string",
            "isActive": true|false
        }
    ]
}
```

---

### 6.9 `get-container-images`

Returns images registered to a container service.

**Synopsis:**
```bash
aws lightsail get-container-images \
    --service-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service |

**Output Schema:**
```json
{
    "containerImages": [
        {
            "image": "string",
            "digest": "string",
            "createdAt": "timestamp"
        }
    ]
}
```

---

### 6.10 `delete-container-image`

Deletes a container image registered to a container service.

**Synopsis:**
```bash
aws lightsail delete-container-image \
    --service-name <value> \
    --image <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service |
| `--image` | **Yes** | string | -- | Image name to delete (e.g., `:my-container.my-image.1`) |

**Output Schema:**
```json
{}
```

---

### 6.11 `register-container-image`

Registers a container image to a container service.

**Synopsis:**
```bash
aws lightsail register-container-image \
    --service-name <value> \
    --label <value> \
    --digest <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service |
| `--label` | **Yes** | string | -- | Label for the image |
| `--digest` | **Yes** | string | -- | Image digest |

**Output Schema:**
```json
{
    "containerImage": {
        "image": "string",
        "digest": "string",
        "createdAt": "timestamp"
    }
}
```

---

### 6.12 `get-container-log`

Returns log events for a container.

**Synopsis:**
```bash
aws lightsail get-container-log \
    --service-name <value> \
    --container-name <value> \
    [--start-time <value>] \
    [--end-time <value>] \
    [--filter-pattern <value>] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Name of the container service |
| `--container-name` | **Yes** | string | -- | Name of the container |
| `--start-time` | No | timestamp | None | Start time for log events |
| `--end-time` | No | timestamp | None | End time for log events |
| `--filter-pattern` | No | string | None | Filter pattern for log events |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "logEvents": [
        {
            "createdAt": "timestamp",
            "message": "string"
        }
    ],
    "nextPageToken": "string"
}
```
