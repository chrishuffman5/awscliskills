# Custom Routing

Commands for managing custom routing accelerators, listeners, endpoint groups, endpoints, and traffic in AWS Global Accelerator. Custom routing accelerators map traffic deterministically to specific EC2 instances in VPC subnets.

## Custom Routing Accelerators

### 4.1 `create-custom-routing-accelerator`

Creates a custom routing accelerator. Custom routing directs traffic to specific EC2 instances and ports.

**Synopsis:**
```bash
aws globalaccelerator create-custom-routing-accelerator \
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
| `--name` | **Yes** | string | -- | Accelerator name (max 64 chars) |
| `--ip-address-type` | No | string | `IPV4` | Must be `IPV4` for custom routing |
| `--ip-addresses` | No | list(string) | None | 1-2 static IPv4 from BYOIP |
| `--enabled` / `--no-enabled` | No | boolean | true | Whether the accelerator is enabled |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "Accelerator": {
        "AcceleratorArn": "string",
        "Name": "string",
        "IpAddressType": "IPV4",
        "Enabled": "boolean",
        "IpSets": [
            {
                "IpAddresses": ["string"],
                "IpAddressFamily": "IPv4"
            }
        ],
        "DnsName": "string",
        "Status": "DEPLOYED|IN_PROGRESS",
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 4.2 `delete-custom-routing-accelerator`

Deletes a custom routing accelerator. Must be disabled with no listeners.

**Synopsis:**
```bash
aws globalaccelerator delete-custom-routing-accelerator \
    --accelerator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the custom routing accelerator |

**Output:** None on success.

---

### 4.3 `describe-custom-routing-accelerator`

Gets details about a custom routing accelerator.

**Synopsis:**
```bash
aws globalaccelerator describe-custom-routing-accelerator \
    --accelerator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |

**Output Schema:** Same as `create-custom-routing-accelerator`.

---

### 4.4 `list-custom-routing-accelerators`

Lists all custom routing accelerators. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-custom-routing-accelerators \
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
    "Accelerators": ["..."],
    "NextToken": "string"
}
```

---

### 4.5 `update-custom-routing-accelerator`

Updates a custom routing accelerator.

**Synopsis:**
```bash
aws globalaccelerator update-custom-routing-accelerator \
    --accelerator-arn <value> \
    [--name <value>] \
    [--ip-address-type <value>] \
    [--enabled | --no-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |
| `--name` | No | string | None | New name |
| `--ip-address-type` | No | string | None | `IPV4` |
| `--enabled` / `--no-enabled` | No | boolean | None | Enable or disable |

**Output Schema:** Same as `create-custom-routing-accelerator`.

---

### 4.6 `describe-custom-routing-accelerator-attributes`

Gets custom routing accelerator attributes (flow logs).

**Synopsis:**
```bash
aws globalaccelerator describe-custom-routing-accelerator-attributes \
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

### 4.7 `update-custom-routing-accelerator-attributes`

Updates custom routing accelerator attributes.

**Synopsis:**
```bash
aws globalaccelerator update-custom-routing-accelerator-attributes \
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
| `--flow-logs-enabled` / `--no-flow-logs-enabled` | No | boolean | false | Enable flow logs |
| `--flow-logs-s3-bucket` | No | string | None | S3 bucket |
| `--flow-logs-s3-prefix` | No | string | None | S3 key prefix |

**Output Schema:** Same as `describe-custom-routing-accelerator-attributes`.

---

## Custom Routing Listeners

### 4.8 `create-custom-routing-listener`

Creates a listener for a custom routing accelerator.

**Synopsis:**
```bash
aws globalaccelerator create-custom-routing-listener \
    --accelerator-arn <value> \
    --port-ranges <value> \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the custom routing accelerator |
| `--port-ranges` | **Yes** | list | -- | Port ranges (1-10). Shorthand: `FromPort=integer,ToPort=integer ...` |
| `--idempotency-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "Listener": {
        "ListenerArn": "string",
        "PortRanges": [
            {
                "FromPort": "integer",
                "ToPort": "integer"
            }
        ]
    }
}
```

---

### 4.9 `delete-custom-routing-listener`

Deletes a custom routing listener.

**Synopsis:**
```bash
aws globalaccelerator delete-custom-routing-listener \
    --listener-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener to delete |

**Output:** None on success.

---

### 4.10 `describe-custom-routing-listener`

Gets details about a custom routing listener.

**Synopsis:**
```bash
aws globalaccelerator describe-custom-routing-listener \
    --listener-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |

**Output Schema:** Same as `create-custom-routing-listener`.

---

### 4.11 `list-custom-routing-listeners`

Lists custom routing listeners for an accelerator. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-custom-routing-listeners \
    --accelerator-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Listeners": ["..."],
    "NextToken": "string"
}
```

---

### 4.12 `update-custom-routing-listener`

Updates a custom routing listener.

**Synopsis:**
```bash
aws globalaccelerator update-custom-routing-listener \
    --listener-arn <value> \
    --port-ranges <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--port-ranges` | **Yes** | list | -- | Updated port ranges |

**Output Schema:** Same as `create-custom-routing-listener`.

---

## Custom Routing Endpoint Groups

### 4.13 `create-custom-routing-endpoint-group`

Creates an endpoint group for a custom routing listener.

**Synopsis:**
```bash
aws globalaccelerator create-custom-routing-endpoint-group \
    --listener-arn <value> \
    --endpoint-group-region <value> \
    --destination-configurations <value> \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the custom routing listener |
| `--endpoint-group-region` | **Yes** | string | -- | AWS Region for the endpoint group |
| `--destination-configurations` | **Yes** | list | -- | Destination port ranges and protocols (1-100) |
| `--idempotency-token` | No | string | None | Idempotency token |

**Destination Configuration (shorthand):**
```
FromPort=integer,ToPort=integer,Protocols=TCP,UDP ...
```

**Output Schema:**
```json
{
    "EndpointGroup": {
        "EndpointGroupArn": "string",
        "EndpointGroupRegion": "string",
        "DestinationDescriptions": [
            {
                "FromPort": "integer",
                "ToPort": "integer",
                "Protocols": ["TCP|UDP"]
            }
        ],
        "EndpointDescriptions": [
            {
                "EndpointId": "string"
            }
        ]
    }
}
```

---

### 4.14 `delete-custom-routing-endpoint-group`

Deletes a custom routing endpoint group.

**Synopsis:**
```bash
aws globalaccelerator delete-custom-routing-endpoint-group \
    --endpoint-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |

**Output:** None on success.

---

### 4.15 `describe-custom-routing-endpoint-group`

Gets details about a custom routing endpoint group.

**Synopsis:**
```bash
aws globalaccelerator describe-custom-routing-endpoint-group \
    --endpoint-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |

**Output Schema:** Same as `create-custom-routing-endpoint-group`.

---

### 4.16 `list-custom-routing-endpoint-groups`

Lists custom routing endpoint groups for a listener. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-custom-routing-endpoint-groups \
    --listener-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EndpointGroups": ["..."],
    "NextToken": "string"
}
```

---

## Custom Routing Endpoints

### 4.17 `add-custom-routing-endpoints`

Adds VPC subnet endpoints to a custom routing endpoint group.

**Synopsis:**
```bash
aws globalaccelerator add-custom-routing-endpoints \
    --endpoint-configurations <value> \
    --endpoint-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-configurations` | **Yes** | list | -- | VPC subnet endpoints. Shorthand: `EndpointId=string,AttachmentArn=string ...` |
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |

**Output Schema:**
```json
{
    "EndpointDescriptions": [
        {
            "EndpointId": "string"
        }
    ],
    "EndpointGroupArn": "string"
}
```

---

### 4.18 `remove-custom-routing-endpoints`

Removes VPC subnet endpoints from a custom routing endpoint group.

**Synopsis:**
```bash
aws globalaccelerator remove-custom-routing-endpoints \
    --endpoint-ids <value> \
    --endpoint-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-ids` | **Yes** | list(string) | -- | VPC subnet IDs to remove |
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |

**Output:** None on success.

---

## Custom Routing Traffic Control

### 4.19 `allow-custom-routing-traffic`

Allows traffic to specific EC2 instance destinations in a VPC subnet endpoint.

**Synopsis:**
```bash
aws globalaccelerator allow-custom-routing-traffic \
    --endpoint-group-arn <value> \
    --endpoint-id <value> \
    [--destination-addresses <value>] \
    [--destination-ports <value>] \
    [--allow-all-traffic-to-endpoint | --no-allow-all-traffic-to-endpoint] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |
| `--endpoint-id` | **Yes** | string | -- | VPC subnet ID |
| `--destination-addresses` | No* | list(string) | None | EC2 instance IP addresses (max 100) |
| `--destination-ports` | No | list(integer) | None | Destination ports (max 100) |
| `--allow-all-traffic-to-endpoint` | No | boolean | false | Allow all traffic to subnet |

*Required when `--allow-all-traffic-to-endpoint` is false or not specified.

**Output:** None on success.

---

### 4.20 `deny-custom-routing-traffic`

Denies traffic to specific EC2 instance destinations in a VPC subnet endpoint.

**Synopsis:**
```bash
aws globalaccelerator deny-custom-routing-traffic \
    --endpoint-group-arn <value> \
    --endpoint-id <value> \
    [--destination-addresses <value>] \
    [--destination-ports <value>] \
    [--deny-all-traffic-to-endpoint | --no-deny-all-traffic-to-endpoint] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-group-arn` | **Yes** | string | -- | ARN of the endpoint group |
| `--endpoint-id` | **Yes** | string | -- | VPC subnet ID |
| `--destination-addresses` | No* | list(string) | None | EC2 instance IP addresses (max 100) |
| `--destination-ports` | No | list(integer) | None | Destination ports (max 100) |
| `--deny-all-traffic-to-endpoint` | No | boolean | false | Deny all traffic to subnet |

*Required when `--deny-all-traffic-to-endpoint` is false or not specified.

**Output:** None on success.

---

### 4.21 `list-custom-routing-port-mappings`

Lists port mappings for a custom routing accelerator. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-custom-routing-port-mappings \
    --accelerator-arn <value> \
    [--endpoint-group-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |
| `--endpoint-group-arn` | No | string | None | Filter by endpoint group ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PortMappings": [
        {
            "AcceleratorPort": "integer",
            "EndpointGroupArn": "string",
            "EndpointId": "string",
            "DestinationSocketAddress": {
                "IpAddress": "string",
                "Port": "integer"
            },
            "Protocols": ["TCP|UDP"],
            "DestinationTrafficState": "ALLOW|DENY"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.22 `list-custom-routing-port-mappings-by-destination`

Lists port mappings for a specific destination (EC2 instance). **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-custom-routing-port-mappings-by-destination \
    --endpoint-id <value> \
    --destination-address <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-id` | **Yes** | string | -- | VPC subnet ID |
| `--destination-address` | **Yes** | string | -- | EC2 instance IP address |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DestinationPortMappings": [
        {
            "AcceleratorArn": "string",
            "AcceleratorSocketAddresses": [
                {
                    "IpAddress": "string",
                    "Port": "integer"
                }
            ],
            "EndpointGroupArn": "string",
            "EndpointId": "string",
            "EndpointGroupRegion": "string",
            "DestinationSocketAddress": {
                "IpAddress": "string",
                "Port": "integer"
            },
            "IpAddressType": "IPV4|DUAL_STACK",
            "DestinationTrafficState": "ALLOW|DENY"
        }
    ],
    "NextToken": "string"
}
```
