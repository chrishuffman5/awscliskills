# Connections & Tags

## Connections

### 6.1 `start-connection`

Starts a connection to the Outpost server for Remote Direct Peering.

**Synopsis:**
```bash
aws outposts start-connection \
    --device-serial-number <value> \
    --asset-id <value> \
    --client-public-key <value> \
    --network-interface-device-index <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--device-serial-number` | **Yes** | string | -- | Serial number of the dongle device |
| `--asset-id` | **Yes** | string | -- | ID of the Outpost server asset |
| `--client-public-key` | **Yes** | string | -- | Public key of the client |
| `--network-interface-device-index` | **Yes** | integer | -- | Device index of the network interface on the Outpost server |

**Output Schema:**
```json
{
    "ConnectionId": "string",
    "UnderlayIpAddress": "string"
}
```

---

### 6.2 `get-connection`

Gets information about the specified connection.

**Synopsis:**
```bash
aws outposts get-connection \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | ID of the connection |

**Output Schema:**
```json
{
    "ConnectionId": "string",
    "ConnectionDetails": {
        "ClientPublicKey": "string",
        "ServerPublicKey": "string",
        "ServerEndpoint": "string",
        "ClientTunnelAddress": "string",
        "ServerTunnelAddress": "string",
        "AllowedIps": ["string"]
    }
}
```

---

## Catalog Items

### 6.3 `list-catalog-items`

Lists the items in the catalog. **Paginated operation.**

**Synopsis:**
```bash
aws outposts list-catalog-items \
    [--item-class-filter <value>] \
    [--supported-storage-filter <value>] \
    [--ec2-family-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--item-class-filter` | No | list(string) | None | Filter by item class: `RACK`, `SERVER` |
| `--supported-storage-filter` | No | list(string) | None | Filter by storage type: `EBS`, `S3` |
| `--ec2-family-filter` | No | list(string) | None | Filter by EC2 family (e.g., `m5`, `c5`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CatalogItems": [
        {
            "CatalogItemId": "string",
            "ItemStatus": "AVAILABLE|DISCONTINUED",
            "EC2Capacities": [
                {
                    "Family": "string",
                    "MaxSize": "string",
                    "Quantity": "string"
                }
            ],
            "PowerKva": "float",
            "WeightLbs": "integer",
            "SupportedUplinkGbps": ["integer"],
            "SupportedStorage": ["EBS|S3"]
        }
    ],
    "NextToken": "string"
}
```

---

## Tags

### 6.4 `tag-resource`

Adds tags to the specified resource.

**Synopsis:**
```bash
aws outposts tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{}
```

---

### 6.5 `untag-resource`

Removes tags from the specified resource.

**Synopsis:**
```bash
aws outposts untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 6.6 `list-tags-for-resource`

Lists the tags for the specified resource.

**Synopsis:**
```bash
aws outposts list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
