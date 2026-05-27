# Backup Gateway

Commands use `aws backup-gateway` (separate service from `aws backup`). Backup Gateway enables backup of on-premises VMware virtual machines to AWS.

---

## Gateway Management

### 15.1 `create-gateway`

Creates a backup gateway for connecting on-premises environments to AWS Backup.

**Synopsis:**
```bash
aws backup-gateway create-gateway \
    --activation-key <value> \
    --gateway-display-name <value> \
    --gateway-type <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--activation-key` | **Yes** | string | -- | Gateway activation key (1-50 chars, alphanumeric + dash) |
| `--gateway-display-name` | **Yes** | string | -- | Display name (1-100 chars) |
| `--gateway-type` | **Yes** | string | -- | Gateway type (`BACKUP_VM`) |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "GatewayArn": "string"
}
```

---

### 15.2 `get-gateway`

Returns details of a backup gateway.

**Synopsis:**
```bash
aws backup-gateway get-gateway \
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
    "Gateway": {
        "GatewayArn": "string",
        "GatewayDisplayName": "string",
        "GatewayType": "BACKUP_VM",
        "HypervisorId": "string",
        "LastSeenTime": "timestamp",
        "MaintenanceStartTime": {
            "DayOfMonth": "integer",
            "DayOfWeek": "integer",
            "HourOfDay": "integer",
            "MinuteOfHour": "integer"
        },
        "NextUpdateAvailabilityTime": "timestamp",
        "VpcEndpoint": "string"
    }
}
```

---

### 15.3 `list-gateways`

Lists all backup gateways. **Paginated operation.**

**Synopsis:**
```bash
aws backup-gateway list-gateways \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "Gateways": [
        {
            "GatewayArn": "string",
            "GatewayDisplayName": "string",
            "GatewayType": "BACKUP_VM",
            "HypervisorId": "string",
            "LastSeenTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 15.4 `update-gateway-information`

Updates a gateway's display name or other information.

**Synopsis:**
```bash
aws backup-gateway update-gateway-information \
    --gateway-arn <value> \
    [--gateway-display-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--gateway-display-name` | No | string | None | New display name |

**Output Schema:**
```json
{
    "GatewayArn": "string"
}
```

---

### 15.5 `update-gateway-software-now`

Triggers an immediate software update for the gateway.

**Synopsis:**
```bash
aws backup-gateway update-gateway-software-now \
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
    "GatewayArn": "string"
}
```

---

### 15.6 `put-maintenance-start-time`

Sets the maintenance window start time for the gateway.

**Synopsis:**
```bash
aws backup-gateway put-maintenance-start-time \
    --gateway-arn <value> \
    --hour-of-day <value> \
    --minute-of-hour <value> \
    [--day-of-week <value>] \
    [--day-of-month <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--hour-of-day` | **Yes** | integer | -- | Hour (0-23) |
| `--minute-of-hour` | **Yes** | integer | -- | Minute (0-59) |
| `--day-of-week` | No | integer | None | Day of week (0=Sunday, 6=Saturday) |
| `--day-of-month` | No | integer | None | Day of month (1-31) |

**Output Schema:**
```json
{
    "GatewayArn": "string"
}
```

---

### 15.7 `delete-gateway`

Deletes a backup gateway.

**Synopsis:**
```bash
aws backup-gateway delete-gateway \
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
    "GatewayArn": "string"
}
```

---

### 15.8 `associate-gateway-to-server`

Associates a gateway with a hypervisor server.

**Synopsis:**
```bash
aws backup-gateway associate-gateway-to-server \
    --gateway-arn <value> \
    --server-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--server-arn` | **Yes** | string | -- | Server (hypervisor) ARN |

**Output Schema:**
```json
{
    "GatewayArn": "string"
}
```

---

### 15.9 `disassociate-gateway-from-server`

Disassociates a gateway from a hypervisor server.

**Synopsis:**
```bash
aws backup-gateway disassociate-gateway-from-server \
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
    "GatewayArn": "string"
}
```

---

### 15.10 `get-bandwidth-rate-limit-schedule`

Returns the bandwidth rate limit schedule for a gateway.

**Synopsis:**
```bash
aws backup-gateway get-bandwidth-rate-limit-schedule \
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
    "BandwidthRateLimitIntervals": [
        {
            "AverageUploadRateLimitInBitsPerSec": "long",
            "DaysOfWeek": ["integer"],
            "EndHourOfDay": "integer",
            "EndMinuteOfHour": "integer",
            "StartHourOfDay": "integer",
            "StartMinuteOfHour": "integer"
        }
    ],
    "GatewayArn": "string"
}
```

---

### 15.11 `put-bandwidth-rate-limit-schedule`

Sets the bandwidth rate limit schedule for a gateway.

**Synopsis:**
```bash
aws backup-gateway put-bandwidth-rate-limit-schedule \
    --gateway-arn <value> \
    --bandwidth-rate-limit-intervals <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--bandwidth-rate-limit-intervals` | **Yes** | list | -- | Bandwidth schedule intervals (0-20 items) |

**Bandwidth Rate Limit Interval Structure:**
```json
{
    "AverageUploadRateLimitInBitsPerSec": "long (min: 51200, max: 8000000000000)",
    "DaysOfWeek": ["integer (0-6, 0=Sunday)"],
    "EndHourOfDay": "integer (0-23)",
    "EndMinuteOfHour": "integer (0-59)",
    "StartHourOfDay": "integer (0-23)",
    "StartMinuteOfHour": "integer (0-59)"
}
```

**Output Schema:**
```json
{
    "GatewayArn": "string"
}
```

---

## Hypervisor Management

### 15.12 `import-hypervisor-configuration`

Imports an on-premises hypervisor configuration into AWS Backup Gateway.

**Synopsis:**
```bash
aws backup-gateway import-hypervisor-configuration \
    --host <value> \
    --name <value> \
    [--kms-key-arn <value>] \
    [--password <value>] \
    [--username <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--host` | **Yes** | string | -- | Hypervisor host IP or FQDN (3-128 chars) |
| `--name` | **Yes** | string | -- | Hypervisor name (1-100 chars) |
| `--kms-key-arn` | No | string | None | KMS key ARN for encryption |
| `--password` | No | string | None | Hypervisor password |
| `--username` | No | string | None | Hypervisor username |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "HypervisorArn": "string"
}
```

---

### 15.13 `get-hypervisor`

Returns details of a hypervisor.

**Synopsis:**
```bash
aws backup-gateway get-hypervisor \
    --hypervisor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hypervisor-arn` | **Yes** | string | -- | Hypervisor ARN |

**Output Schema:**
```json
{
    "Hypervisor": {
        "Host": "string",
        "HypervisorArn": "string",
        "KmsKeyArn": "string",
        "LastSuccessfulMetadataSyncTime": "timestamp",
        "LatestMetadataSyncStatus": "CREATED|RUNNING|FAILED|PARTIALLY_FAILED|SUCCEEDED",
        "LatestMetadataSyncStatusMessage": "string",
        "LogGroupArn": "string",
        "Name": "string",
        "State": "PENDING|ONLINE|OFFLINE|ERROR"
    }
}
```

---

### 15.14 `list-hypervisors`

Lists all hypervisors. **Paginated operation.**

**Synopsis:**
```bash
aws backup-gateway list-hypervisors \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "Hypervisors": [
        {
            "Host": "string",
            "HypervisorArn": "string",
            "KmsKeyArn": "string",
            "Name": "string",
            "State": "PENDING|ONLINE|OFFLINE|ERROR"
        }
    ],
    "NextToken": "string"
}
```

---

### 15.15 `update-hypervisor`

Updates a hypervisor's configuration.

**Synopsis:**
```bash
aws backup-gateway update-hypervisor \
    --hypervisor-arn <value> \
    [--host <value>] \
    [--log-group-arn <value>] \
    [--name <value>] \
    [--password <value>] \
    [--username <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hypervisor-arn` | **Yes** | string | -- | Hypervisor ARN |
| `--host` | No | string | None | New host IP or FQDN |
| `--log-group-arn` | No | string | None | CloudWatch log group ARN |
| `--name` | No | string | None | New name |
| `--password` | No | string | None | New password |
| `--username` | No | string | None | New username |

**Output Schema:**
```json
{
    "HypervisorArn": "string"
}
```

---

### 15.16 `delete-hypervisor`

Deletes a hypervisor.

**Synopsis:**
```bash
aws backup-gateway delete-hypervisor \
    --hypervisor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hypervisor-arn` | **Yes** | string | -- | Hypervisor ARN |

**Output Schema:**
```json
{
    "HypervisorArn": "string"
}
```

---

### 15.17 `get-hypervisor-property-mappings`

Returns VMware-to-AWS tag mappings for a hypervisor.

**Synopsis:**
```bash
aws backup-gateway get-hypervisor-property-mappings \
    --hypervisor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hypervisor-arn` | **Yes** | string | -- | Hypervisor ARN |

**Output Schema:**
```json
{
    "HypervisorArn": "string",
    "IamRoleArn": "string",
    "VmwareToAwsTagMappings": [
        {
            "AwsTagKey": "string",
            "AwsTagValue": "string",
            "VmwareCategory": "string",
            "VmwareTagName": "string"
        }
    ]
}
```

---

### 15.18 `put-hypervisor-property-mappings`

Sets VMware-to-AWS tag mappings for a hypervisor.

**Synopsis:**
```bash
aws backup-gateway put-hypervisor-property-mappings \
    --hypervisor-arn <value> \
    --iam-role-arn <value> \
    --vmware-to-aws-tag-mappings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hypervisor-arn` | **Yes** | string | -- | Hypervisor ARN |
| `--iam-role-arn` | **Yes** | string | -- | IAM role ARN for tag mapping |
| `--vmware-to-aws-tag-mappings` | **Yes** | list | -- | Tag mapping list |

**Output Schema:**
```json
{
    "HypervisorArn": "string"
}
```

---

### 15.19 `test-hypervisor-configuration`

Tests connectivity to a hypervisor.

**Synopsis:**
```bash
aws backup-gateway test-hypervisor-configuration \
    --gateway-arn <value> \
    --host <value> \
    [--password <value>] \
    [--username <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--host` | **Yes** | string | -- | Hypervisor host IP or FQDN |
| `--password` | No | string | None | Hypervisor password |
| `--username` | No | string | None | Hypervisor username |

**Output:** None

---

## Virtual Machine Management

### 15.20 `get-virtual-machine`

Returns details of a virtual machine discovered by the gateway.

**Synopsis:**
```bash
aws backup-gateway get-virtual-machine \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Virtual machine ARN |

**Output Schema:**
```json
{
    "VirtualMachine": {
        "HostName": "string",
        "HypervisorId": "string",
        "LastBackupDate": "timestamp",
        "Name": "string",
        "Path": "string",
        "ResourceArn": "string",
        "VmwareTags": [
            {
                "VmwareCategory": "string",
                "VmwareTagDescription": "string",
                "VmwareTagName": "string"
            }
        ]
    }
}
```

---

### 15.21 `list-virtual-machines`

Lists virtual machines discovered by backup gateways. **Paginated operation.**

**Synopsis:**
```bash
aws backup-gateway list-virtual-machines \
    [--hypervisor-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hypervisor-arn` | No | string | None | Filter by hypervisor ARN |

**Output Schema:**
```json
{
    "VirtualMachines": [
        {
            "HostName": "string",
            "HypervisorId": "string",
            "LastBackupDate": "timestamp",
            "Name": "string",
            "Path": "string",
            "ResourceArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 15.22 `start-virtual-machines-metadata-sync`

Triggers a metadata sync for virtual machines on a hypervisor.

**Synopsis:**
```bash
aws backup-gateway start-virtual-machines-metadata-sync \
    --hypervisor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hypervisor-arn` | **Yes** | string | -- | Hypervisor ARN |

**Output Schema:**
```json
{
    "HypervisorArn": "string"
}
```

---

## Tagging (Backup Gateway)

### 15.23 `tag-resource`

Adds tags to a backup-gateway resource.

**Synopsis:**
```bash
aws backup-gateway tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | Tags (Key/Value pairs, max 50) |

**Output Schema:**
```json
{
    "ResourceARN": "string"
}
```

---

### 15.24 `untag-resource`

Removes tags from a backup-gateway resource.

**Synopsis:**
```bash
aws backup-gateway untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output Schema:**
```json
{
    "ResourceARN": "string"
}
```

---

### 15.25 `list-tags-for-resource`

Lists tags for a backup-gateway resource.

**Synopsis:**
```bash
aws backup-gateway list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
