# Sites, Devices & Links

## Sites

### 4.1 `create-site`

Creates a site in a global network.

**Synopsis:**
```bash
aws networkmanager create-site \
    --global-network-id <value> \
    [--description <value>] \
    [--location <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--description` | No | string | None | Description (max 256 chars) |
| `--location` | No | structure | None | Physical location. Shorthand: `Address=string,Latitude=string,Longitude=string` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Site": {
        "SiteId": "string",
        "SiteArn": "string",
        "GlobalNetworkId": "string",
        "Description": "string",
        "Location": {
            "Address": "string",
            "Latitude": "string",
            "Longitude": "string"
        },
        "CreatedAt": "timestamp",
        "State": "PENDING|AVAILABLE|DELETING|UPDATING",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 4.2 `delete-site`

Deletes a site. All devices and links at the site must be removed first.

**Synopsis:**
```bash
aws networkmanager delete-site \
    --global-network-id <value> \
    --site-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--site-id` | **Yes** | string | -- | Site ID |

**Output Schema:** Same as create-site.

---

### 4.3 `get-sites`

Gets information about one or more sites in a global network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-sites \
    --global-network-id <value> \
    [--site-ids <value>] \
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
| `--site-ids` | No | list(string) | None | One or more site IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Sites": [
        {
            "SiteId": "string",
            "SiteArn": "string",
            "GlobalNetworkId": "string",
            "Description": "string",
            "Location": {},
            "CreatedAt": "timestamp",
            "State": "string",
            "Tags": []
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `update-site`

Updates a site's description and location.

**Synopsis:**
```bash
aws networkmanager update-site \
    --global-network-id <value> \
    --site-id <value> \
    [--description <value>] \
    [--location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--site-id` | **Yes** | string | -- | Site ID |
| `--description` | No | string | None | Updated description |
| `--location` | No | structure | None | Updated location |

**Output Schema:** Same as create-site.

---

## Devices

### 4.5 `create-device`

Creates a device in a global network.

**Synopsis:**
```bash
aws networkmanager create-device \
    --global-network-id <value> \
    [--aws-location <value>] \
    [--description <value>] \
    [--type <value>] \
    [--vendor <value>] \
    [--model <value>] \
    [--serial-number <value>] \
    [--location <value>] \
    [--site-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--aws-location` | No | structure | None | AWS location. Shorthand: `Zone=string,SubnetArn=string` |
| `--description` | No | string | None | Description (max 256 chars) |
| `--type` | No | string | None | Device type (max 256 chars) |
| `--vendor` | No | string | None | Vendor (max 128 chars) |
| `--model` | No | string | None | Model (max 128 chars) |
| `--serial-number` | No | string | None | Serial number (max 128 chars) |
| `--location` | No | structure | None | Physical location. Shorthand: `Address=string,Latitude=string,Longitude=string` |
| `--site-id` | No | string | None | Associated site ID |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "Device": {
        "DeviceId": "string",
        "DeviceArn": "string",
        "GlobalNetworkId": "string",
        "AWSLocation": {
            "Zone": "string",
            "SubnetArn": "string"
        },
        "Description": "string",
        "Type": "string",
        "Vendor": "string",
        "Model": "string",
        "SerialNumber": "string",
        "Location": {
            "Address": "string",
            "Latitude": "string",
            "Longitude": "string"
        },
        "SiteId": "string",
        "CreatedAt": "timestamp",
        "State": "PENDING|AVAILABLE|DELETING|UPDATING",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 4.6 `delete-device`

Deletes a device. All links and connections for the device must be removed first.

**Synopsis:**
```bash
aws networkmanager delete-device \
    --global-network-id <value> \
    --device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--device-id` | **Yes** | string | -- | Device ID |

**Output Schema:** Same as create-device.

---

### 4.7 `get-devices`

Gets information about one or more devices. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-devices \
    --global-network-id <value> \
    [--device-ids <value>] \
    [--site-id <value>] \
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
| `--device-ids` | No | list(string) | None | One or more device IDs |
| `--site-id` | No | string | None | Filter by site ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Devices": [{"DeviceId": "string", "...": "..."}],
    "NextToken": "string"
}
```

---

### 4.8 `update-device`

Updates device properties.

**Synopsis:**
```bash
aws networkmanager update-device \
    --global-network-id <value> \
    --device-id <value> \
    [--aws-location <value>] \
    [--description <value>] \
    [--type <value>] \
    [--vendor <value>] \
    [--model <value>] \
    [--serial-number <value>] \
    [--location <value>] \
    [--site-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same optional parameters as create-device, plus required `--device-id`.

**Output Schema:** Same as create-device.

---

## Links

### 4.9 `create-link`

Creates a link in a global network.

**Synopsis:**
```bash
aws networkmanager create-link \
    --global-network-id <value> \
    --bandwidth <value> \
    --site-id <value> \
    [--description <value>] \
    [--type <value>] \
    [--provider <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--bandwidth` | **Yes** | structure | -- | Upload/download speeds. Shorthand: `UploadSpeed=integer,DownloadSpeed=integer` |
| `--site-id` | **Yes** | string | -- | Site ID where the link is located |
| `--description` | No | string | None | Description (max 256 chars) |
| `--type` | No | string | None | Link type (max 256 chars) |
| `--provider` | No | string | None | Link provider (max 128 chars) |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "Link": {
        "LinkId": "string",
        "LinkArn": "string",
        "GlobalNetworkId": "string",
        "SiteId": "string",
        "Description": "string",
        "Type": "string",
        "Bandwidth": {
            "UploadSpeed": "integer",
            "DownloadSpeed": "integer"
        },
        "Provider": "string",
        "CreatedAt": "timestamp",
        "State": "PENDING|AVAILABLE|DELETING|UPDATING",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 4.10 `delete-link`

Deletes a link. The link must be disassociated from all devices first.

**Synopsis:**
```bash
aws networkmanager delete-link \
    --global-network-id <value> \
    --link-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--link-id` | **Yes** | string | -- | Link ID |

**Output Schema:** Same as create-link.

---

### 4.11 `get-links`

Gets information about one or more links. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-links \
    --global-network-id <value> \
    [--link-ids <value>] \
    [--site-id <value>] \
    [--type <value>] \
    [--provider <value>] \
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
| `--link-ids` | No | list(string) | None | One or more link IDs |
| `--site-id` | No | string | None | Filter by site ID |
| `--type` | No | string | None | Filter by link type |
| `--provider` | No | string | None | Filter by provider |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Links": [{"LinkId": "string", "...": "..."}],
    "NextToken": "string"
}
```

---

### 4.12 `update-link`

Updates a link's properties.

**Synopsis:**
```bash
aws networkmanager update-link \
    --global-network-id <value> \
    --link-id <value> \
    [--description <value>] \
    [--type <value>] \
    [--bandwidth <value>] \
    [--provider <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same optional parameters as create-link, plus required `--link-id`.

**Output Schema:** Same as create-link.

---

### 4.13 `associate-link`

Associates a link with a device at the same site.

**Synopsis:**
```bash
aws networkmanager associate-link \
    --global-network-id <value> \
    --device-id <value> \
    --link-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--device-id` | **Yes** | string | -- | Device ID |
| `--link-id` | **Yes** | string | -- | Link ID |

**Output Schema:**
```json
{
    "LinkAssociation": {
        "GlobalNetworkId": "string",
        "DeviceId": "string",
        "LinkId": "string",
        "LinkAssociationState": "PENDING|AVAILABLE|DELETING|DELETED"
    }
}
```

---

### 4.14 `disassociate-link`

Disassociates a link from a device.

**Synopsis:**
```bash
aws networkmanager disassociate-link \
    --global-network-id <value> \
    --device-id <value> \
    --link-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as associate-link.

**Output Schema:** Same as associate-link.

---

### 4.15 `get-link-associations`

Gets link associations for a global network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-link-associations \
    --global-network-id <value> \
    [--device-id <value>] \
    [--link-id <value>] \
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
| `--device-id` | No | string | None | Filter by device ID |
| `--link-id` | No | string | None | Filter by link ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LinkAssociations": [
        {
            "GlobalNetworkId": "string",
            "DeviceId": "string",
            "LinkId": "string",
            "LinkAssociationState": "string"
        }
    ],
    "NextToken": "string"
}
```
