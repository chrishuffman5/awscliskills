# Networking

### 11.1 `allocate-static-ip`

Allocates a static IP address.

**Synopsis:**
```bash
aws lightsail allocate-static-ip \
    --static-ip-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--static-ip-name` | **Yes** | string | -- | Name for the static IP |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "StaticIp",
            "operationType": "AllocateStaticIp",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 11.2 `release-static-ip`

Releases (deletes) a static IP address.

**Synopsis:**
```bash
aws lightsail release-static-ip \
    --static-ip-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--static-ip-name` | **Yes** | string | -- | Name of the static IP to release |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "StaticIp",
            "operationType": "ReleaseStaticIp",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 11.3 `get-static-ip`

Returns information about a specific static IP.

**Synopsis:**
```bash
aws lightsail get-static-ip \
    --static-ip-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--static-ip-name` | **Yes** | string | -- | Name of the static IP |

**Output Schema:**
```json
{
    "staticIp": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "StaticIp",
        "ipAddress": "string",
        "attachedTo": "string",
        "isAttached": true|false
    }
}
```

---

### 11.4 `get-static-ips`

Returns information about all static IPs. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-static-ips \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "staticIps": [
        {
            "name": "string",
            "arn": "string",
            "ipAddress": "string",
            "attachedTo": "string",
            "isAttached": true|false
        }
    ],
    "nextPageToken": "string"
}
```

---

### 11.5 `attach-static-ip`

Attaches a static IP address to an instance.

**Synopsis:**
```bash
aws lightsail attach-static-ip \
    --static-ip-name <value> \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--static-ip-name` | **Yes** | string | -- | Name of the static IP |
| `--instance-name` | **Yes** | string | -- | Name of the instance to attach to |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "StaticIp",
            "operationType": "AttachStaticIp",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 11.6 `detach-static-ip`

Detaches a static IP address from an instance.

**Synopsis:**
```bash
aws lightsail detach-static-ip \
    --static-ip-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--static-ip-name` | **Yes** | string | -- | Name of the static IP to detach |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "StaticIp",
            "operationType": "DetachStaticIp",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 11.7 `is-vpc-peered`

Returns whether the Lightsail VPC is peered with the default VPC.

**Synopsis:**
```bash
aws lightsail is-vpc-peered \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "isPeered": true|false
}
```

---

### 11.8 `peer-vpc`

Peers the Lightsail VPC with the default VPC in the account.

**Synopsis:**
```bash
aws lightsail peer-vpc \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "PeeredVpc",
        "operationType": "PeerVpc",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 11.9 `unpeer-vpc`

Unpeers the Lightsail VPC from the default VPC.

**Synopsis:**
```bash
aws lightsail unpeer-vpc \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "PeeredVpc",
        "operationType": "UnpeerVpc",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```
