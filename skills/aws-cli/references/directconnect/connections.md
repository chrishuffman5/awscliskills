# Connections

### 1.1 `create-connection`

Creates a dedicated connection between your network and a specific Direct Connect location.

**Synopsis:**
```bash
aws directconnect create-connection \
    --location <value> \
    --bandwidth <value> \
    --connection-name <value> \
    [--lag-id <value>] \
    [--tags <value>] \
    [--provider-name <value>] \
    [--request-mac-sec | --no-request-mac-sec] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location` | **Yes** | string | -- | The location of the connection (use `describe-locations` to list) |
| `--bandwidth` | **Yes** | string | -- | The bandwidth: `1Gbps`, `10Gbps`, `100Gbps`, `400Gbps` |
| `--connection-name` | **Yes** | string | -- | The name of the connection |
| `--lag-id` | No | string | None | The ID of the LAG to automatically add the connection to |
| `--tags` | No | list | None | Tags to associate. Shorthand: `key=string,value=string ...` |
| `--provider-name` | No | string | None | The service provider name |
| `--request-mac-sec` | No | boolean | false | Request MACsec support on the connection |

**Output Schema:**
```json
{
    "ownerAccount": "string",
    "connectionId": "string",
    "connectionName": "string",
    "connectionState": "ordering|requested|pending|available|down|deleting|deleted|rejected|unknown",
    "region": "string",
    "location": "string",
    "bandwidth": "string",
    "vlan": "integer",
    "partnerName": "string",
    "loaIssueTime": "timestamp",
    "lagId": "string",
    "awsDevice": "string",
    "jumboFrameCapable": "boolean",
    "awsDeviceV2": "string",
    "awsLogicalDeviceId": "string",
    "hasLogicalRedundancy": "unknown|yes|no",
    "tags": [{"key": "string", "value": "string"}],
    "providerName": "string",
    "macSecCapable": "boolean",
    "portEncryptionStatus": "string",
    "encryptionMode": "string",
    "macSecKeys": [
        {
            "secretARN": "string",
            "ckn": "string",
            "state": "associating|associated|disassociating|disassociated",
            "startOn": "string"
        }
    ]
}
```

---

### 1.2 `delete-connection`

Deletes the specified connection.

**Synopsis:**
```bash
aws directconnect delete-connection \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |

**Output Schema:**
```json
{
    "ownerAccount": "string",
    "connectionId": "string",
    "connectionName": "string",
    "connectionState": "ordering|requested|pending|available|down|deleting|deleted|rejected|unknown",
    "region": "string",
    "location": "string",
    "bandwidth": "string",
    "vlan": "integer",
    "partnerName": "string",
    "lagId": "string",
    "awsDevice": "string",
    "macSecCapable": "boolean",
    "encryptionMode": "string",
    "macSecKeys": []
}
```

---

### 1.3 `describe-connections`

Displays the specified connection or all connections in the current region. **Paginated.**

**Synopsis:**
```bash
aws directconnect describe-connections \
    [--connection-id <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | No | string | None | The ID of a specific connection |
| `--max-results` | No | integer | None | Maximum number of results (max 100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "connections": [
        {
            "ownerAccount": "string",
            "connectionId": "string",
            "connectionName": "string",
            "connectionState": "ordering|requested|pending|available|down|deleting|deleted|rejected|unknown",
            "region": "string",
            "location": "string",
            "bandwidth": "string",
            "vlan": "integer",
            "partnerName": "string",
            "loaIssueTime": "timestamp",
            "lagId": "string",
            "awsDevice": "string",
            "jumboFrameCapable": "boolean",
            "awsDeviceV2": "string",
            "awsLogicalDeviceId": "string",
            "hasLogicalRedundancy": "unknown|yes|no",
            "tags": [{"key": "string", "value": "string"}],
            "providerName": "string",
            "macSecCapable": "boolean",
            "portEncryptionStatus": "string",
            "encryptionMode": "string",
            "macSecKeys": []
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-connection`

Updates the connection name or encryption mode for a dedicated connection.

**Synopsis:**
```bash
aws directconnect update-connection \
    --connection-id <value> \
    [--connection-name <value>] \
    [--encryption-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--connection-name` | No | string | None | The new connection name |
| `--encryption-mode` | No | string | None | MACsec encryption mode: `no_encrypt`, `should_encrypt`, `must_encrypt` |

**Output Schema:**
Same as `create-connection` output.

---

### 1.5 `confirm-connection`

Confirms the creation of a hosted connection on an interconnect. Used by the partner to confirm the connection was created successfully.

**Synopsis:**
```bash
aws directconnect confirm-connection \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the hosted connection |

**Output Schema:**
```json
{
    "connectionState": "ordering|requested|pending|available|down|deleting|deleted|rejected|unknown"
}
```

---

### 1.6 `allocate-hosted-connection`

Creates a hosted connection on the specified interconnect or LAG. Intended for Direct Connect partners.

**Synopsis:**
```bash
aws directconnect allocate-hosted-connection \
    --connection-id <value> \
    --owner-account <value> \
    --bandwidth <value> \
    --connection-name <value> \
    --vlan <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the interconnect or LAG |
| `--owner-account` | **Yes** | string | -- | The ID of the AWS account of the customer |
| `--bandwidth` | **Yes** | string | -- | The bandwidth of the hosted connection |
| `--connection-name` | **Yes** | string | -- | The name of the hosted connection |
| `--vlan` | **Yes** | integer | -- | The dedicated VLAN provisioned for the connection |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Output Schema:**
Same as `create-connection` output.

---

### 1.7 `describe-hosted-connections`

Lists the hosted connections provisioned on the specified interconnect or LAG.

**Synopsis:**
```bash
aws directconnect describe-hosted-connections \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the interconnect or LAG |

**Output Schema:**
```json
{
    "connections": [
        {
            "ownerAccount": "string",
            "connectionId": "string",
            "connectionName": "string",
            "connectionState": "string",
            "region": "string",
            "location": "string",
            "bandwidth": "string",
            "vlan": "integer",
            "lagId": "string"
        }
    ]
}
```

---

### 1.8 `associate-hosted-connection`

Associates a hosted connection and its virtual interfaces with a LAG or interconnect.

**Synopsis:**
```bash
aws directconnect associate-hosted-connection \
    --connection-id <value> \
    --parent-connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the hosted connection |
| `--parent-connection-id` | **Yes** | string | -- | The ID of the interconnect or LAG |

**Output Schema:**
Same as `create-connection` output.

---

### 1.9 `associate-connection-with-lag`

Associates an existing connection with a LAG. The connection and LAG must be in the same location and use the same bandwidth.

**Synopsis:**
```bash
aws directconnect associate-connection-with-lag \
    --connection-id <value> \
    --lag-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--lag-id` | **Yes** | string | -- | The ID of the LAG to associate the connection with |

**Output Schema:**
Same as `create-connection` output.

---

### 1.10 `disassociate-connection-from-lag`

Disassociates a connection from a LAG. The connection reverts to a standalone connection.

**Synopsis:**
```bash
aws directconnect disassociate-connection-from-lag \
    --connection-id <value> \
    --lag-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--lag-id` | **Yes** | string | -- | The ID of the LAG |

**Output Schema:**
Same as `create-connection` output.

---

### 1.11 `describe-loa`

Gets the LOA-CFA (Letter of Authorization - Connecting Facility Assignment) for a connection.

**Synopsis:**
```bash
aws directconnect describe-loa \
    --connection-id <value> \
    [--provider-name <value>] \
    [--loa-content-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--provider-name` | No | string | None | The name of the provider |
| `--loa-content-type` | No | string | `application/pdf` | The LOA content type |

**Output Schema:**
```json
{
    "loaContent": "blob",
    "loaContentType": "application/pdf"
}
```

---

### 1.12 `describe-locations`

Lists the Direct Connect locations in the current region. Provides location codes, port speeds, and available providers.

**Synopsis:**
```bash
aws directconnect describe-locations \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**
```json
{
    "locations": [
        {
            "locationCode": "string",
            "locationName": "string",
            "region": "string",
            "availablePortSpeeds": ["string"],
            "availableProviders": ["string"],
            "availableMacSecPortSpeeds": ["string"]
        }
    ]
}
```

---

### 1.13 `describe-customer-metadata`

Gets the customer metadata associated with the specified Direct Connect connection.

**Synopsis:**
```bash
aws directconnect describe-customer-metadata \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**
```json
{
    "agreements": [
        {
            "agreementName": "string",
            "status": "string"
        }
    ],
    "nniPartnerType": "v1|v2|nonPartner"
}
```

---

### 1.14 `confirm-customer-agreement`

Confirms the customer agreement for the specified account.

**Synopsis:**
```bash
aws directconnect confirm-customer-agreement \
    [--agreement-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agreement-name` | No | string | None | The name of the customer agreement |

**Output Schema:**
```json
{
    "status": "string"
}
```
