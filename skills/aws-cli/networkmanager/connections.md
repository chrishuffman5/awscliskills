# Connections

### 5.1 `create-connection`

Creates a connection between two devices. The devices can be a physical or virtual appliance that connects to a third-party appliance in a VPC.

**Synopsis:**
```bash
aws networkmanager create-connection \
    --global-network-id <value> \
    --device-id <value> \
    --connected-device-id <value> \
    [--link-id <value>] \
    [--connected-link-id <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--device-id` | **Yes** | string | -- | First device ID |
| `--connected-device-id` | **Yes** | string | -- | Second device ID |
| `--link-id` | No | string | None | Link ID for the first device |
| `--connected-link-id` | No | string | None | Link ID for the second device |
| `--description` | No | string | None | Description (max 256 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Connection": {
        "ConnectionId": "string",
        "ConnectionArn": "string",
        "GlobalNetworkId": "string",
        "DeviceId": "string",
        "ConnectedDeviceId": "string",
        "LinkId": "string",
        "ConnectedLinkId": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "State": "PENDING|AVAILABLE|DELETING|UPDATING",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 5.2 `delete-connection`

Deletes a connection.

**Synopsis:**
```bash
aws networkmanager delete-connection \
    --global-network-id <value> \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--connection-id` | **Yes** | string | -- | Connection ID |

**Output Schema:** Same as create-connection.

---

### 5.3 `get-connections`

Gets information about one or more connections. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-connections \
    --global-network-id <value> \
    [--connection-ids <value>] \
    [--device-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--connection-ids` | No | list(string) | None | One or more connection IDs |
| `--device-id` | No | string | None | Filter by device ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Connections": [
        {
            "ConnectionId": "string",
            "ConnectionArn": "string",
            "GlobalNetworkId": "string",
            "DeviceId": "string",
            "ConnectedDeviceId": "string",
            "LinkId": "string",
            "ConnectedLinkId": "string",
            "Description": "string",
            "CreatedAt": "timestamp",
            "State": "string",
            "Tags": []
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `update-connection`

Updates a connection's properties.

**Synopsis:**
```bash
aws networkmanager update-connection \
    --global-network-id <value> \
    --connection-id <value> \
    [--link-id <value>] \
    [--connected-link-id <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--connection-id` | **Yes** | string | -- | Connection ID |
| `--link-id` | No | string | None | Updated link ID for first device |
| `--connected-link-id` | No | string | None | Updated link ID for second device |
| `--description` | No | string | None | Updated description |

**Output Schema:** Same as create-connection.
