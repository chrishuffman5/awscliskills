# Compute

### 11.1 `register-compute`

Registers a compute resource to a fleet (Anywhere or container fleets).

**Synopsis:**
```bash
aws gamelift register-compute \
    --fleet-id <value> \
    --compute-name <value> \
    [--certificate-path <value>] \
    [--dns-name <value>] \
    [--ip-address <value>] \
    [--location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN (1-512 chars) |
| `--compute-name` | **Yes** | string | -- | Unique compute name (1-128 chars) |
| `--certificate-path` | No | string | None | Path to TLS certificate (1-1024 chars) |
| `--dns-name` | No | string | None | DNS name of compute (1-256 chars) |
| `--ip-address` | No | string | None | IP address (required for Anywhere fleets, 1-128 chars) |
| `--location` | No | string | None | Custom location (required for Anywhere fleets, 1-64 chars) |

**Output Schema:**
```json
{
    "Compute": {
        "FleetId": "string",
        "FleetArn": "string",
        "ComputeName": "string",
        "ComputeArn": "string",
        "IpAddress": "string",
        "DnsName": "string",
        "ComputeStatus": "PENDING|ACTIVE|TERMINATING|IMPAIRED",
        "Location": "string",
        "CreationTime": "timestamp",
        "OperatingSystem": "string",
        "Type": "string",
        "GameLiftServiceSdkEndpoint": "string",
        "GameLiftAgentEndpoint": "string",
        "InstanceId": "string",
        "ContainerAttributes": [
            {
                "ContainerName": "string",
                "ContainerRuntimeId": "string"
            }
        ],
        "GameServerContainerGroupDefinitionArn": "string"
    }
}
```

---

### 11.2 `deregister-compute`

Removes a registered compute from a fleet.

**Synopsis:**
```bash
aws gamelift deregister-compute \
    --fleet-id <value> \
    --compute-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--compute-name` | **Yes** | string | -- | Compute name |

**Output Schema:**
```json
None
```

---

### 11.3 `describe-compute`

Retrieves properties of a registered compute resource.

**Synopsis:**
```bash
aws gamelift describe-compute \
    --fleet-id <value> \
    --compute-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--compute-name` | **Yes** | string | -- | Compute name |

**Output Schema:**
```json
{
    "Compute": {
        "FleetId": "string",
        "FleetArn": "string",
        "ComputeName": "string",
        "ComputeArn": "string",
        "IpAddress": "string",
        "DnsName": "string",
        "ComputeStatus": "PENDING|ACTIVE|TERMINATING|IMPAIRED",
        "Location": "string",
        "CreationTime": "timestamp",
        "OperatingSystem": "string",
        "Type": "string",
        "GameLiftServiceSdkEndpoint": "string",
        "GameLiftAgentEndpoint": "string",
        "InstanceId": "string",
        "ContainerAttributes": [],
        "GameServerContainerGroupDefinitionArn": "string"
    }
}
```

---

### 11.4 `list-compute`

Lists compute resources in a fleet. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-compute \
    --fleet-id <value> \
    [--location <value>] \
    [--container-group-definition-name <value>] \
    [--compute-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--location` | No | string | None | Filter by location |
| `--container-group-definition-name` | No | string | None | Filter by container group definition |
| `--compute-status` | No | string | None | Filter: `ACTIVE` or `IMPAIRED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ComputeList": [
        {
            "FleetId": "string",
            "FleetArn": "string",
            "ComputeName": "string",
            "ComputeArn": "string",
            "IpAddress": "string",
            "DnsName": "string",
            "ComputeStatus": "string",
            "Location": "string",
            "CreationTime": "timestamp",
            "OperatingSystem": "string",
            "Type": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.5 `get-compute-access`

Requests credentials for remote access to a compute resource (SSH for Linux, RDP for Windows).

**Synopsis:**
```bash
aws gamelift get-compute-access \
    --fleet-id <value> \
    --compute-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--compute-name` | **Yes** | string | -- | Compute name |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string",
    "ComputeName": "string",
    "ComputeArn": "string",
    "Credentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string"
    },
    "Target": "string",
    "ContainerIdentifiers": [
        {
            "ContainerName": "string",
            "ContainerRuntimeId": "string"
        }
    ]
}
```

---

### 11.6 `get-compute-auth-token`

Retrieves an authentication token for a compute resource to communicate with GameLift.

**Synopsis:**
```bash
aws gamelift get-compute-auth-token \
    --fleet-id <value> \
    --compute-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--compute-name` | **Yes** | string | -- | Compute name |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string",
    "ComputeName": "string",
    "ComputeArn": "string",
    "AuthToken": "string",
    "ExpirationTimestamp": "timestamp"
}
```
