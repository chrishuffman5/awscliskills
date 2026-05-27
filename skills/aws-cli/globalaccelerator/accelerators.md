# Accelerators

### 1.1 `create-accelerator`

Creates a standard accelerator that directs traffic to optimal endpoints.

**Synopsis:**
```bash
aws globalaccelerator create-accelerator \
    --name <value> \
    [--ip-address-type <value>] \
    [--ip-addresses <value>] \
    [--enabled | --no-enabled] \
    [--idempotency-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Accelerator name (max 64 chars, alphanumeric/hyphens/periods) |
| `--ip-address-type` | No | string | `IPV4` | IP address type: `IPV4` or `DUAL_STACK` |
| `--ip-addresses` | No | list(string) | None | 1-2 static IPv4 addresses from BYOIP pool |
| `--enabled` / `--no-enabled` | No | boolean | true | Whether the accelerator is enabled |
| `--idempotency-token` | No | string | None | Idempotency token (max 255 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Accelerator": {
        "AcceleratorArn": "string",
        "Name": "string",
        "IpAddressType": "IPV4|DUAL_STACK",
        "Enabled": "boolean",
        "IpSets": [
            {
                "IpAddresses": ["string"],
                "IpAddressFamily": "IPv4|IPv6"
            }
        ],
        "DnsName": "string",
        "DualStackDnsName": "string",
        "Status": "DEPLOYED|IN_PROGRESS",
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp",
        "Events": [
            {
                "Message": "string",
                "Timestamp": "timestamp"
            }
        ]
    }
}
```

---

### 1.2 `delete-accelerator`

Deletes an accelerator. The accelerator must be disabled and have no listeners.

**Synopsis:**
```bash
aws globalaccelerator delete-accelerator \
    --accelerator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator to delete |

**Output:** None on success.

---

### 1.3 `describe-accelerator`

Gets details about an accelerator.

**Synopsis:**
```bash
aws globalaccelerator describe-accelerator \
    --accelerator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |

**Output Schema:** Same as `create-accelerator`.

---

### 1.4 `list-accelerators`

Lists all standard accelerators. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-accelerators \
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
    "Accelerators": [
        {
            "AcceleratorArn": "string",
            "Name": "string",
            "IpAddressType": "IPV4|DUAL_STACK",
            "Enabled": "boolean",
            "IpSets": [],
            "DnsName": "string",
            "Status": "DEPLOYED|IN_PROGRESS",
            "CreatedTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-accelerator`

Updates accelerator settings (name, IP address type, enabled status).

**Synopsis:**
```bash
aws globalaccelerator update-accelerator \
    --accelerator-arn <value> \
    [--name <value>] \
    [--ip-address-type <value>] \
    [--ip-addresses <value>] \
    [--enabled | --no-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |
| `--name` | No | string | None | New accelerator name |
| `--ip-address-type` | No | string | None | `IPV4` or `DUAL_STACK` |
| `--ip-addresses` | No | list(string) | None | Static IPv4 addresses from BYOIP |
| `--enabled` / `--no-enabled` | No | boolean | None | Enable or disable the accelerator |

**Output Schema:** Same as `create-accelerator`.

---

### 1.6 `describe-accelerator-attributes`

Gets accelerator attributes (flow logs configuration).

**Synopsis:**
```bash
aws globalaccelerator describe-accelerator-attributes \
    --accelerator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |

**Output Schema:**
```json
{
    "AcceleratorAttributes": {
        "FlowLogsEnabled": "boolean",
        "FlowLogsS3Bucket": "string",
        "FlowLogsS3Prefix": "string"
    }
}
```

---

### 1.7 `update-accelerator-attributes`

Updates accelerator attributes (flow logs configuration).

**Synopsis:**
```bash
aws globalaccelerator update-accelerator-attributes \
    --accelerator-arn <value> \
    [--flow-logs-enabled | --no-flow-logs-enabled] \
    [--flow-logs-s3-bucket <value>] \
    [--flow-logs-s3-prefix <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |
| `--flow-logs-enabled` / `--no-flow-logs-enabled` | No | boolean | false | Enable or disable flow logs |
| `--flow-logs-s3-bucket` | No | string | None | S3 bucket for flow logs |
| `--flow-logs-s3-prefix` | No | string | None | S3 key prefix for flow logs |

**Output Schema:**
```json
{
    "AcceleratorAttributes": {
        "FlowLogsEnabled": "boolean",
        "FlowLogsS3Bucket": "string",
        "FlowLogsS3Prefix": "string"
    }
}
```
