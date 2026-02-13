# Global Networks

### 1.1 `create-global-network`

Creates a new global network. A global network is the top-level container for your network objects (sites, devices, links, Transit Gateways, core networks).

**Synopsis:**
```bash
aws networkmanager create-global-network \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--description` | No | string | None | Description (max 256 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "GlobalNetwork": {
        "GlobalNetworkId": "string",
        "GlobalNetworkArn": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "State": "PENDING|AVAILABLE|DELETING|UPDATING",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 1.2 `delete-global-network`

Deletes a global network. All resources (sites, devices, links, Transit Gateways) must be removed first.

**Synopsis:**
```bash
aws networkmanager delete-global-network \
    --global-network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | The ID of the global network |

**Output Schema:**
```json
{
    "GlobalNetwork": {
        "GlobalNetworkId": "string",
        "GlobalNetworkArn": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "State": "PENDING|AVAILABLE|DELETING|UPDATING",
        "Tags": []
    }
}
```

---

### 1.3 `describe-global-networks`

Describes one or more global networks. **Paginated.**

**Synopsis:**
```bash
aws networkmanager describe-global-networks \
    [--global-network-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-ids` | No | list(string) | None | One or more global network IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GlobalNetworks": [
        {
            "GlobalNetworkId": "string",
            "GlobalNetworkArn": "string",
            "Description": "string",
            "CreatedAt": "timestamp",
            "State": "PENDING|AVAILABLE|DELETING|UPDATING",
            "Tags": [{"Key": "string", "Value": "string"}]
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-global-network`

Updates a global network description.

**Synopsis:**
```bash
aws networkmanager update-global-network \
    --global-network-id <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | The ID of the global network |
| `--description` | No | string | None | Updated description (max 256 chars) |

**Output Schema:**
```json
{
    "GlobalNetwork": {
        "GlobalNetworkId": "string",
        "GlobalNetworkArn": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "State": "PENDING|AVAILABLE|DELETING|UPDATING",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```
