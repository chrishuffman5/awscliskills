# Sites

### 2.1 `create-site`

Creates a site for an Outpost. A site is a physical location where AWS Outposts hardware is installed.

**Synopsis:**
```bash
aws outposts create-site \
    --name <value> \
    [--description <value>] \
    [--notes <value>] \
    [--tags <value>] \
    [--operating-address <value>] \
    [--shipping-address <value>] \
    [--rack-physical-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the site (1-1000 chars) |
| `--description` | No | string | -- | Description of the site |
| `--notes` | No | string | -- | Additional notes about the site |
| `--tags` | No | map | None | Tags as key-value pairs |
| `--operating-address` | No | structure | None | Operating address of the site |
| `--shipping-address` | No | structure | None | Shipping address for deliveries |
| `--rack-physical-properties` | No | structure | None | Physical properties of the rack |

**Address Structure:**
```json
{
    "ContactName": "string",
    "ContactPhoneNumber": "string",
    "AddressLine1": "string",
    "AddressLine2": "string",
    "AddressLine3": "string",
    "City": "string",
    "StateOrRegion": "string",
    "DistrictOrCounty": "string",
    "PostalCode": "string",
    "CountryCode": "string",
    "Municipality": "string"
}
```

**Rack Physical Properties Structure:**
```json
{
    "PowerDrawKva": "POWER_5_KVA|POWER_10_KVA|POWER_15_KVA|POWER_30_KVA",
    "PowerPhase": "SINGLE_PHASE|THREE_PHASE",
    "PowerConnector": "L6_30P|IEC309|AH530P7W|AH532P6W",
    "PowerFeedDrop": "ABOVE_RACK|BELOW_RACK",
    "UplinkGbps": "UPLINK_1G|UPLINK_10G|UPLINK_40G|UPLINK_100G",
    "UplinkCount": "UPLINK_COUNT_1|UPLINK_COUNT_2|UPLINK_COUNT_3|...|UPLINK_COUNT_16",
    "FiberOpticCableType": "SINGLE_MODE|MULTI_MODE",
    "OpticalStandard": "OPTIC_10GBASE_SR|OPTIC_10GBASE_IR|OPTIC_10GBASE_LR|OPTIC_40GBASE_SR|OPTIC_40GBASE_ESR|OPTIC_40GBASE_IR4_LR4L|OPTIC_40GBASE_LR4|OPTIC_100GBASE_SR4|OPTIC_100GBASE_CWDM4|OPTIC_100GBASE_LR4|OPTIC_100G_PSM4_MSA|OPTIC_1000BASE_LX|OPTIC_1000BASE_SX",
    "MaximumSupportedWeightLbs": "NO_LIMIT|MAX_1400_LBS|MAX_1600_LBS|MAX_1800_LBS|MAX_2000_LBS"
}
```

**Output Schema:**
```json
{
    "Site": {
        "SiteId": "string",
        "AccountId": "string",
        "Name": "string",
        "Description": "string",
        "Tags": {
            "string": "string"
        },
        "SiteArn": "string",
        "Notes": "string",
        "OperatingAddressCountryCode": "string",
        "OperatingAddressStateOrRegion": "string",
        "OperatingAddressCity": "string",
        "RackPhysicalProperties": {
            "PowerDrawKva": "string",
            "PowerPhase": "string",
            "PowerConnector": "string",
            "PowerFeedDrop": "string",
            "UplinkGbps": "string",
            "UplinkCount": "string",
            "FiberOpticCableType": "string",
            "OpticalStandard": "string",
            "MaximumSupportedWeightLbs": "string"
        }
    }
}
```

---

### 2.2 `get-site`

Gets information about the specified site.

**Synopsis:**
```bash
aws outposts get-site \
    --site-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--site-id` | **Yes** | string | -- | ID or ARN of the site |

**Output Schema:**
```json
{
    "Site": {
        "SiteId": "string",
        "AccountId": "string",
        "Name": "string",
        "Description": "string",
        "Tags": {
            "string": "string"
        },
        "SiteArn": "string",
        "Notes": "string",
        "OperatingAddressCountryCode": "string",
        "OperatingAddressStateOrRegion": "string",
        "OperatingAddressCity": "string",
        "RackPhysicalProperties": {}
    }
}
```

---

### 2.3 `list-sites`

Lists the Outpost sites for your AWS account. **Paginated operation.**

**Synopsis:**
```bash
aws outposts list-sites \
    [--operating-address-country-code-filter <value>] \
    [--operating-address-state-or-region-filter <value>] \
    [--operating-address-city-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--operating-address-country-code-filter` | No | list(string) | None | Filter by country code (e.g., `US`) |
| `--operating-address-state-or-region-filter` | No | list(string) | None | Filter by state or region |
| `--operating-address-city-filter` | No | list(string) | None | Filter by city |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Sites": [
        {
            "SiteId": "string",
            "AccountId": "string",
            "Name": "string",
            "Description": "string",
            "Tags": {
                "string": "string"
            },
            "SiteArn": "string",
            "Notes": "string",
            "OperatingAddressCountryCode": "string",
            "OperatingAddressStateOrRegion": "string",
            "OperatingAddressCity": "string",
            "RackPhysicalProperties": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-site`

Updates the specified site properties.

**Synopsis:**
```bash
aws outposts update-site \
    --site-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--notes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--site-id` | **Yes** | string | -- | ID or ARN of the site |
| `--name` | No | string | -- | Updated name |
| `--description` | No | string | -- | Updated description |
| `--notes` | No | string | -- | Updated notes |

**Output Schema:**
```json
{
    "Site": {
        "SiteId": "string",
        "AccountId": "string",
        "Name": "string",
        "Description": "string",
        "Tags": {
            "string": "string"
        },
        "SiteArn": "string",
        "Notes": "string",
        "OperatingAddressCountryCode": "string",
        "OperatingAddressStateOrRegion": "string",
        "OperatingAddressCity": "string",
        "RackPhysicalProperties": {}
    }
}
```

---

### 2.5 `delete-site`

Deletes the specified site.

**Synopsis:**
```bash
aws outposts delete-site \
    --site-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--site-id` | **Yes** | string | -- | ID or ARN of the site to delete |

**Output Schema:**
```json
{}
```

---

### 2.6 `get-site-address`

Gets the site address for the specified site.

**Synopsis:**
```bash
aws outposts get-site-address \
    --site-id <value> \
    --address-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--site-id` | **Yes** | string | -- | ID or ARN of the site |
| `--address-type` | **Yes** | string | -- | Address type: `SHIPPING_ADDRESS` or `OPERATING_ADDRESS` |

**Output Schema:**
```json
{
    "SiteId": "string",
    "AddressType": "SHIPPING_ADDRESS|OPERATING_ADDRESS",
    "Address": {
        "ContactName": "string",
        "ContactPhoneNumber": "string",
        "AddressLine1": "string",
        "AddressLine2": "string",
        "AddressLine3": "string",
        "City": "string",
        "StateOrRegion": "string",
        "DistrictOrCounty": "string",
        "PostalCode": "string",
        "CountryCode": "string",
        "Municipality": "string"
    }
}
```

---

### 2.7 `update-site-address`

Updates the address of the specified site.

**Synopsis:**
```bash
aws outposts update-site-address \
    --site-id <value> \
    --address-type <value> \
    --address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--site-id` | **Yes** | string | -- | ID or ARN of the site |
| `--address-type` | **Yes** | string | -- | Address type: `SHIPPING_ADDRESS` or `OPERATING_ADDRESS` |
| `--address` | **Yes** | structure | -- | Address details (see Address Structure above) |

**Output Schema:**
```json
{
    "AddressType": "SHIPPING_ADDRESS|OPERATING_ADDRESS",
    "Address": {
        "ContactName": "string",
        "ContactPhoneNumber": "string",
        "AddressLine1": "string",
        "AddressLine2": "string",
        "AddressLine3": "string",
        "City": "string",
        "StateOrRegion": "string",
        "DistrictOrCounty": "string",
        "PostalCode": "string",
        "CountryCode": "string",
        "Municipality": "string"
    }
}
```

---

### 2.8 `update-site-rack-physical-properties`

Updates the physical properties of a rack at a site.

**Synopsis:**
```bash
aws outposts update-site-rack-physical-properties \
    --site-id <value> \
    [--power-draw-kva <value>] \
    [--power-phase <value>] \
    [--power-connector <value>] \
    [--power-feed-drop <value>] \
    [--uplink-gbps <value>] \
    [--uplink-count <value>] \
    [--fiber-optic-cable-type <value>] \
    [--optical-standard <value>] \
    [--maximum-supported-weight-lbs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--site-id` | **Yes** | string | -- | ID or ARN of the site |
| `--power-draw-kva` | No | string | -- | Power draw: `POWER_5_KVA`, `POWER_10_KVA`, `POWER_15_KVA`, `POWER_30_KVA` |
| `--power-phase` | No | string | -- | Power phase: `SINGLE_PHASE`, `THREE_PHASE` |
| `--power-connector` | No | string | -- | Power connector type: `L6_30P`, `IEC309`, `AH530P7W`, `AH532P6W` |
| `--power-feed-drop` | No | string | -- | Power feed drop: `ABOVE_RACK`, `BELOW_RACK` |
| `--uplink-gbps` | No | string | -- | Uplink speed: `UPLINK_1G`, `UPLINK_10G`, `UPLINK_40G`, `UPLINK_100G` |
| `--uplink-count` | No | string | -- | Number of uplinks: `UPLINK_COUNT_1` through `UPLINK_COUNT_16` |
| `--fiber-optic-cable-type` | No | string | -- | Cable type: `SINGLE_MODE`, `MULTI_MODE` |
| `--optical-standard` | No | string | -- | Optical standard (see Rack Physical Properties Structure) |
| `--maximum-supported-weight-lbs` | No | string | -- | Max weight: `NO_LIMIT`, `MAX_1400_LBS`, `MAX_1600_LBS`, `MAX_1800_LBS`, `MAX_2000_LBS` |

**Output Schema:**
```json
{
    "Site": {
        "SiteId": "string",
        "AccountId": "string",
        "Name": "string",
        "Description": "string",
        "Tags": {
            "string": "string"
        },
        "SiteArn": "string",
        "Notes": "string",
        "OperatingAddressCountryCode": "string",
        "OperatingAddressStateOrRegion": "string",
        "OperatingAddressCity": "string",
        "RackPhysicalProperties": {
            "PowerDrawKva": "string",
            "PowerPhase": "string",
            "PowerConnector": "string",
            "PowerFeedDrop": "string",
            "UplinkGbps": "string",
            "UplinkCount": "string",
            "FiberOpticCableType": "string",
            "OpticalStandard": "string",
            "MaximumSupportedWeightLbs": "string"
        }
    }
}
```
