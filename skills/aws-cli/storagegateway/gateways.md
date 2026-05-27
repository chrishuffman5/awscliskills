# Gateways

### 1.1 `activate-gateway`

Activates a Storage Gateway appliance. This is the first operation after deploying the gateway VM.

**Synopsis:**
```bash
aws storagegateway activate-gateway \
    --activation-key <value> \
    --gateway-name <value> \
    --gateway-timezone <value> \
    --gateway-region <value> \
    [--gateway-type <value>] \
    [--tape-drive-type <value>] \
    [--medium-changer-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--activation-key` | **Yes** | string | -- | Activation key from gateway HTTP endpoint (1-50 chars) |
| `--gateway-name` | **Yes** | string | -- | Gateway name (2-255 chars) |
| `--gateway-timezone` | **Yes** | string | -- | Time zone in format `GMT`, `GMT-hr:mm`, or `GMT+hr:mm` (3-10 chars) |
| `--gateway-region` | **Yes** | string | -- | AWS Region for data storage (1-25 chars) |
| `--gateway-type` | No | string | `CACHED` | Gateway type: `STORED`, `CACHED`, `VTL`, `FILE_S3`, `FILE_FSX_SMB` |
| `--tape-drive-type` | No | string | None | Tape drive type for VTL: `IBM-ULT3580-TD5` |
| `--medium-changer-type` | No | string | None | Medium changer: `STK-L700`, `AWS-Gateway-VTL`, `IBM-03584L32-0402` |
| `--tags` | No | list | None | Up to 50 key-value tags |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 1.2 `describe-gateway-information`

Returns metadata about a gateway including name, type, state, network interfaces, and software version.

**Synopsis:**
```bash
aws storagegateway describe-gateway-information \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN (50-500 chars) |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "GatewayId": "string",
    "GatewayName": "string",
    "GatewayTimezone": "string",
    "GatewayState": "string",
    "GatewayNetworkInterfaces": [
        {
            "Ipv4Address": "string",
            "MacAddress": "string",
            "Ipv6Address": "string"
        }
    ],
    "GatewayType": "string",
    "NextUpdateAvailabilityDate": "string",
    "LastSoftwareUpdate": "string",
    "Ec2InstanceId": "string",
    "Ec2InstanceRegion": "string",
    "Tags": [{"Key": "string", "Value": "string"}],
    "VPCEndpoint": "string",
    "CloudWatchLogGroupARN": "string",
    "HostEnvironment": "VMWARE|HYPER-V|EC2|KVM|OTHER|SNOWBALL",
    "EndpointType": "STANDARD|FIPS",
    "SoftwareUpdatesEndDate": "string",
    "DeprecationDate": "string",
    "GatewayCapacity": "Small|Medium|Large",
    "SupportedGatewayCapacities": ["string"],
    "HostEnvironmentId": "string",
    "SoftwareVersion": "string"
}
```

---

### 1.3 `update-gateway-information`

Updates the gateway name, timezone, and CloudWatch log group configuration.

**Synopsis:**
```bash
aws storagegateway update-gateway-information \
    --gateway-arn <value> \
    [--gateway-name <value>] \
    [--gateway-timezone <value>] \
    [--cloud-watch-log-group-arn <value>] \
    [--gateway-capacity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--gateway-name` | No | string | None | New gateway name (2-255 chars) |
| `--gateway-timezone` | No | string | None | New timezone |
| `--cloud-watch-log-group-arn` | No | string | None | CloudWatch log group ARN |
| `--gateway-capacity` | No | string | None | Metadata cache size: `Small`, `Medium`, `Large` |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "GatewayName": "string"
}
```

---

### 1.4 `update-gateway-software-now`

Triggers an immediate gateway software update.

**Synopsis:**
```bash
aws storagegateway update-gateway-software-now \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 1.5 `shutdown-gateway`

Shuts down a gateway. After shutdown, the gateway is no longer available for operations. Use `start-gateway` to restart.

**Synopsis:**
```bash
aws storagegateway shutdown-gateway \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 1.6 `start-gateway`

Starts a previously shut down gateway. Only works if the gateway VM is running.

**Synopsis:**
```bash
aws storagegateway start-gateway \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 1.7 `disable-gateway`

Disables a tape gateway when it is no longer functioning. Only supported for tape gateways.

**Synopsis:**
```bash
aws storagegateway disable-gateway \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 1.8 `delete-gateway`

Deletes a gateway and all its resources. This operation is irreversible.

**Synopsis:**
```bash
aws storagegateway delete-gateway \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 1.9 `list-gateways`

Lists gateways in the account and region. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway list-gateways \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Gateways": [
        {
            "GatewayId": "string",
            "GatewayARN": "string",
            "GatewayType": "string",
            "GatewayOperationalState": "string",
            "GatewayName": "string",
            "Ec2InstanceId": "string",
            "Ec2InstanceRegion": "string",
            "HostEnvironment": "string",
            "HostEnvironmentId": "string",
            "DeprecationDate": "string",
            "SoftwareVersion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.10 `list-local-disks`

Returns a list of local disks available on a gateway, including disk IDs, paths, sizes, and current allocation.

**Synopsis:**
```bash
aws storagegateway list-local-disks \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "Disks": [
        {
            "DiskId": "string",
            "DiskPath": "string",
            "DiskNode": "string",
            "DiskStatus": "string",
            "DiskSizeInBytes": "long",
            "DiskAllocationType": "string",
            "DiskAllocationResource": "string",
            "DiskAttributeList": ["string"]
        }
    ]
}
```

---

### 1.11 `describe-maintenance-start-time`

Returns the maintenance window schedule for a gateway.

**Synopsis:**
```bash
aws storagegateway describe-maintenance-start-time \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "HourOfDay": "integer",
    "MinuteOfHour": "integer",
    "DayOfWeek": "integer",
    "DayOfMonth": "integer",
    "Timezone": "string",
    "SoftwareUpdatePreferences": {
        "AutomaticUpdatePolicy": "ALL_VERSIONS|EMERGENCY_VERSIONS_ONLY"
    }
}
```

---

### 1.12 `update-maintenance-start-time`

Updates the maintenance window schedule for a gateway.

**Synopsis:**
```bash
aws storagegateway update-maintenance-start-time \
    --gateway-arn <value> \
    --hour-of-day <value> \
    --minute-of-hour <value> \
    [--day-of-week <value>] \
    [--day-of-month <value>] \
    [--software-update-preferences <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--hour-of-day` | **Yes** | integer | -- | Hour (0-23) |
| `--minute-of-hour` | **Yes** | integer | -- | Minute (0-59) |
| `--day-of-week` | No | integer | None | Day of week (0=Sunday to 6=Saturday) |
| `--day-of-month` | No | integer | None | Day of month (1-28) |
| `--software-update-preferences` | No | structure | None | Update policy: `ALL_VERSIONS` or `EMERGENCY_VERSIONS_ONLY` |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 1.13 `start-availability-monitor-test`

Starts an availability monitor test on a gateway. The test runs for 36 hours.

**Synopsis:**
```bash
aws storagegateway start-availability-monitor-test \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 1.14 `describe-availability-monitor-test`

Returns information about the availability monitor test status.

**Synopsis:**
```bash
aws storagegateway describe-availability-monitor-test \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "Status": "COMPLETE|FAILED|PENDING",
    "StartTime": "timestamp"
}
```

---

### 1.15 `set-local-console-password`

Sets the password for the local console on a gateway VM.

**Synopsis:**
```bash
aws storagegateway set-local-console-password \
    --gateway-arn <value> \
    --local-console-password <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--local-console-password` | **Yes** | string | -- | Password (6-512 chars) |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```
