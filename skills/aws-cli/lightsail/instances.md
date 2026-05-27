# Instances

### 1.1 `create-instances`

Creates one or more Amazon Lightsail instances.

**Synopsis:**
```bash
aws lightsail create-instances \
    --instance-names <value> \
    --availability-zone <value> \
    --blueprint-id <value> \
    --bundle-id <value> \
    [--custom-image-name <value>] \
    [--user-data <value>] \
    [--key-pair-name <value>] \
    [--tags <value>] \
    [--add-ons <value>] \
    [--ip-address-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-names` | **Yes** | list(string) | -- | Names for the instances to create |
| `--availability-zone` | **Yes** | string | -- | Availability zone (e.g., `us-east-1a`) |
| `--blueprint-id` | **Yes** | string | -- | Instance image blueprint ID (e.g., `amazon_linux_2`) |
| `--bundle-id` | **Yes** | string | -- | Instance hardware bundle ID (e.g., `micro_3_0`) |
| `--custom-image-name` | No | string | None | Deprecated. Use `--blueprint-id` instead |
| `--user-data` | No | string | None | Launch script (base64-encoded or plain text) |
| `--key-pair-name` | No | string | None | SSH key pair name |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |
| `--add-ons` | No | list | None | Add-on configurations (e.g., auto snapshots) |
| `--ip-address-type` | No | string | `dualstack` | IP address type: `dualstack`, `ipv4`, `ipv6` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance",
            "createdAt": "timestamp",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            },
            "isTerminal": true|false,
            "operationType": "CreateInstance",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "statusChangedAt": "timestamp",
            "errorCode": "string",
            "errorDetails": "string"
        }
    ]
}
```

---

### 1.2 `create-instances-from-snapshot`

Creates one or more instances from a snapshot.

**Synopsis:**
```bash
aws lightsail create-instances-from-snapshot \
    --instance-names <value> \
    --availability-zone <value> \
    --bundle-id <value> \
    [--instance-snapshot-name <value>] \
    [--attached-disk-mapping <value>] \
    [--user-data <value>] \
    [--key-pair-name <value>] \
    [--tags <value>] \
    [--add-ons <value>] \
    [--ip-address-type <value>] \
    [--source-instance-name <value>] \
    [--restore-date <value>] \
    [--use-latest-restorable-auto-snapshot | --no-use-latest-restorable-auto-snapshot] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-names` | **Yes** | list(string) | -- | Names for the new instances |
| `--availability-zone` | **Yes** | string | -- | Availability zone for the new instances |
| `--bundle-id` | **Yes** | string | -- | Bundle ID for the new instances |
| `--instance-snapshot-name` | No | string | None | Name of the snapshot to restore from |
| `--attached-disk-mapping` | No | map | None | Mapping of attached disks for the new instances |
| `--user-data` | No | string | None | Launch script |
| `--key-pair-name` | No | string | None | SSH key pair name |
| `--tags` | No | list | None | Tags for the new instances |
| `--add-ons` | No | list | None | Add-on configurations |
| `--ip-address-type` | No | string | `dualstack` | IP address type: `dualstack`, `ipv4`, `ipv6` |
| `--source-instance-name` | No | string | None | Source instance name for auto snapshot restore |
| `--restore-date` | No | string | None | Date of the auto snapshot to restore (YYYY-MM-DD) |
| `--use-latest-restorable-auto-snapshot` | No | boolean | false | Use the latest auto snapshot |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance",
            "createdAt": "timestamp",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            },
            "isTerminal": true|false,
            "operationType": "CreateInstancesFromSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "statusChangedAt": "timestamp"
        }
    ]
}
```

---

### 1.3 `delete-instance`

Deletes a specific Amazon Lightsail instance.

**Synopsis:**
```bash
aws lightsail delete-instance \
    --instance-name <value> \
    [--force-delete-add-ons | --no-force-delete-add-ons] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance to delete |
| `--force-delete-add-ons` | No | boolean | false | Force deletion of add-ons associated with the instance |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance",
            "createdAt": "timestamp",
            "operationType": "DeleteInstance",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 1.4 `get-instance`

Returns information about a specific Lightsail instance.

**Synopsis:**
```bash
aws lightsail get-instance \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance |

**Output Schema:**
```json
{
    "instance": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "Instance",
        "tags": [
            {
                "key": "string",
                "value": "string"
            }
        ],
        "blueprintId": "string",
        "blueprintName": "string",
        "bundleId": "string",
        "addOns": [
            {
                "name": "string",
                "status": "string",
                "snapshotTimeOfDay": "string",
                "nextSnapshotTimeOfDay": "string"
            }
        ],
        "isStaticIp": true|false,
        "privateIpAddress": "string",
        "publicIpAddress": "string",
        "ipv6Addresses": ["string"],
        "ipAddressType": "dualstack|ipv4|ipv6",
        "hardware": {
            "cpuCount": "integer",
            "disks": [
                {
                    "name": "string",
                    "arn": "string",
                    "sizeInGb": "integer",
                    "isSystemDisk": true|false,
                    "path": "string",
                    "attachedTo": "string",
                    "attachmentState": "string"
                }
            ],
            "ramSizeInGb": "float"
        },
        "networking": {
            "monthlyTransfer": {
                "gbPerMonthAllocated": "integer"
            },
            "ports": [
                {
                    "fromPort": "integer",
                    "toPort": "integer",
                    "protocol": "tcp|udp|all|icmp|icmpv6",
                    "accessFrom": "string",
                    "accessType": "string",
                    "commonName": "string",
                    "accessDirection": "inbound|outbound",
                    "cidrs": ["string"],
                    "ipv6Cidrs": ["string"],
                    "cidrListAliases": ["string"]
                }
            ]
        },
        "state": {
            "code": "integer",
            "name": "pending|running|shutting-down|terminated|stopping|stopped"
        },
        "username": "string",
        "sshKeyName": "string",
        "metadataOptions": {
            "state": "pending|applied",
            "httpTokens": "optional|required",
            "httpEndpoint": "disabled|enabled",
            "httpPutResponseHopLimit": "integer",
            "httpProtocolIpv6": "disabled|enabled"
        }
    }
}
```

---

### 1.5 `get-instances`

Returns information about all Lightsail instances. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-instances \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "instances": [
        {
            "name": "string",
            "arn": "string",
            "blueprintId": "string",
            "bundleId": "string",
            "state": {
                "code": "integer",
                "name": "string"
            },
            "publicIpAddress": "string",
            "privateIpAddress": "string",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            }
        }
    ],
    "nextPageToken": "string"
}
```

---

### 1.6 `get-instance-state`

Returns the state of a specific Lightsail instance.

**Synopsis:**
```bash
aws lightsail get-instance-state \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance |

**Output Schema:**
```json
{
    "state": {
        "code": "integer",
        "name": "pending|running|shutting-down|terminated|stopping|stopped"
    }
}
```

---

### 1.7 `get-instance-metric-data`

Returns metric data for an instance.

**Synopsis:**
```bash
aws lightsail get-instance-metric-data \
    --instance-name <value> \
    --metric-name <value> \
    --period <value> \
    --start-time <value> \
    --end-time <value> \
    --unit <value> \
    --statistics <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance |
| `--metric-name` | **Yes** | string | -- | Metric name (e.g., `CPUUtilization`, `NetworkIn`, `NetworkOut`) |
| `--period` | **Yes** | integer | -- | Granularity in seconds (60, 300, 900, 3600, 86400) |
| `--start-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-time` | **Yes** | timestamp | -- | End of the time range |
| `--unit` | **Yes** | string | -- | Unit for the metric (e.g., `Percent`, `Bytes`) |
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

### 1.8 `get-instance-port-states`

Returns the firewall port states for a specific instance.

**Synopsis:**
```bash
aws lightsail get-instance-port-states \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance |

**Output Schema:**
```json
{
    "portStates": [
        {
            "fromPort": "integer",
            "toPort": "integer",
            "protocol": "tcp|udp|all|icmp|icmpv6",
            "state": "open|closed",
            "cidrs": ["string"],
            "ipv6Cidrs": ["string"],
            "cidrListAliases": ["string"]
        }
    ]
}
```

---

### 1.9 `open-instance-public-ports`

Opens firewall ports on a specific instance.

**Synopsis:**
```bash
aws lightsail open-instance-public-ports \
    --port-info <value> \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--port-info` | **Yes** | structure | -- | Port info. Shorthand: `fromPort=integer,toPort=integer,protocol=tcp|udp|all,cidrs=string,string,ipv6Cidrs=string,string,cidrListAliases=string,string` |
| `--instance-name` | **Yes** | string | -- | Name of the instance |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Instance",
        "operationType": "OpenInstancePublicPorts",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 1.10 `close-instance-public-ports`

Closes firewall ports on a specific instance.

**Synopsis:**
```bash
aws lightsail close-instance-public-ports \
    --port-info <value> \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--port-info` | **Yes** | structure | -- | Port info specifying the port(s) to close |
| `--instance-name` | **Yes** | string | -- | Name of the instance |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Instance",
        "operationType": "CloseInstancePublicPorts",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 1.11 `put-instance-public-ports`

Replaces all firewall port rules for an instance.

**Synopsis:**
```bash
aws lightsail put-instance-public-ports \
    --port-infos <value> \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--port-infos` | **Yes** | list | -- | List of port info structures replacing all existing rules |
| `--instance-name` | **Yes** | string | -- | Name of the instance |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Instance",
        "operationType": "PutInstancePublicPorts",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 1.12 `reboot-instance`

Reboots a specific Lightsail instance.

**Synopsis:**
```bash
aws lightsail reboot-instance \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance to reboot |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance",
            "operationType": "RebootInstance",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 1.13 `start-instance`

Starts a stopped Lightsail instance.

**Synopsis:**
```bash
aws lightsail start-instance \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance to start |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance",
            "operationType": "StartInstance",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 1.14 `stop-instance`

Stops a running Lightsail instance.

**Synopsis:**
```bash
aws lightsail stop-instance \
    --instance-name <value> \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance to stop |
| `--force` | No | boolean | false | Force stop the instance (may cause data loss) |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance",
            "operationType": "StopInstance",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 1.15 `get-blueprints`

Returns all available Lightsail instance blueprints.

**Synopsis:**
```bash
aws lightsail get-blueprints \
    [--include-inactive | --no-include-inactive] \
    [--page-token <value>] \
    [--app-category <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include-inactive` | No | boolean | false | Include inactive blueprints |
| `--page-token` | No | string | None | Pagination token |
| `--app-category` | No | string | None | Filter by app category: `LfR` |

**Output Schema:**
```json
{
    "blueprints": [
        {
            "blueprintId": "string",
            "name": "string",
            "group": "string",
            "type": "os|app",
            "description": "string",
            "isActive": true|false,
            "minPower": "integer",
            "version": "string",
            "versionCode": "string",
            "productUrl": "string",
            "licenseUrl": "string",
            "platform": "LINUX_UNIX|WINDOWS",
            "appCategory": "string"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 1.16 `get-bundles`

Returns all available Lightsail instance bundles (hardware sizes).

**Synopsis:**
```bash
aws lightsail get-bundles \
    [--include-inactive | --no-include-inactive] \
    [--page-token <value>] \
    [--app-category <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include-inactive` | No | boolean | false | Include inactive bundles |
| `--page-token` | No | string | None | Pagination token |
| `--app-category` | No | string | None | Filter by app category: `LfR` |

**Output Schema:**
```json
{
    "bundles": [
        {
            "price": "float",
            "cpuCount": "integer",
            "diskSizeInGb": "integer",
            "bundleId": "string",
            "instanceType": "string",
            "isActive": true|false,
            "name": "string",
            "power": "integer",
            "ramSizeInGb": "float",
            "transferPerMonthInGb": "integer",
            "supportedPlatforms": ["LINUX_UNIX|WINDOWS"],
            "supportedAppCategories": ["string"],
            "publicIpv4AddressCount": "integer"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 1.17 `get-instance-access-details`

Returns temporary SSH or RDP access details for a Lightsail instance.

**Synopsis:**
```bash
aws lightsail get-instance-access-details \
    --instance-name <value> \
    [--protocol <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance |
| `--protocol` | No | string | `ssh` | Access protocol: `ssh`, `rdp` |

**Output Schema:**
```json
{
    "accessDetails": {
        "certKey": "string",
        "expiresAt": "timestamp",
        "ipAddress": "string",
        "ipv6Addresses": ["string"],
        "password": "string",
        "passwordData": {
            "ciphertext": "string",
            "keyPairName": "string"
        },
        "privateKey": "string",
        "protocol": "ssh|rdp",
        "instanceName": "string",
        "username": "string",
        "hostKeys": [
            {
                "algorithm": "string",
                "publicKey": "string",
                "witnessedAt": "timestamp",
                "fingerprintSHA1": "string",
                "fingerprintSHA256": "string",
                "notValidBefore": "timestamp",
                "notValidAfter": "timestamp"
            }
        ]
    }
}
```

---

### 1.18 `update-instance-metadata-options`

Updates the metadata options for an instance (IMDSv2 settings).

**Synopsis:**
```bash
aws lightsail update-instance-metadata-options \
    --instance-name <value> \
    [--http-tokens <value>] \
    [--http-endpoint <value>] \
    [--http-put-response-hop-limit <value>] \
    [--http-protocol-ipv6 <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance |
| `--http-tokens` | No | string | None | Token usage: `optional` (IMDSv1/v2), `required` (IMDSv2 only) |
| `--http-endpoint` | No | string | None | IMDS endpoint: `disabled`, `enabled` |
| `--http-put-response-hop-limit` | No | integer | None | HTTP PUT response hop limit (1-64) |
| `--http-protocol-ipv6` | No | string | None | IPv6 IMDS endpoint: `disabled`, `enabled` |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Instance",
        "operationType": "UpdateInstanceMetadataOptions",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 1.19 `set-ip-address-type`

Sets the IP address type for a Lightsail resource.

**Synopsis:**
```bash
aws lightsail set-ip-address-type \
    --resource-type <value> \
    --resource-name <value> \
    --ip-address-type <value> \
    [--accept-bundle-update | --no-accept-bundle-update] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type: `Instance`, `Distribution`, `LoadBalancer` |
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--ip-address-type` | **Yes** | string | -- | IP address type: `dualstack`, `ipv4`, `ipv6` |
| `--accept-bundle-update` | No | boolean | false | Accept bundle update if required |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance",
            "operationType": "SetIpAddressType",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 1.20 `get-regions`

Returns all available AWS regions for Lightsail.

**Synopsis:**
```bash
aws lightsail get-regions \
    [--include-availability-zones | --no-include-availability-zones] \
    [--include-relational-database-availability-zones | --no-include-relational-database-availability-zones] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include-availability-zones` | No | boolean | false | Include availability zones in response |
| `--include-relational-database-availability-zones` | No | boolean | false | Include database availability zones |

**Output Schema:**
```json
{
    "regions": [
        {
            "continentCode": "string",
            "description": "string",
            "displayName": "string",
            "name": "string",
            "availabilityZones": [
                {
                    "zoneName": "string",
                    "state": "string"
                }
            ],
            "relationalDatabaseAvailabilityZones": [
                {
                    "zoneName": "string",
                    "state": "string"
                }
            ]
        }
    ]
}
```
