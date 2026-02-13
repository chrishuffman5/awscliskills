# Resolver Endpoints

### 1.1 `create-resolver-endpoint`

Creates an inbound or outbound resolver endpoint for hybrid DNS. Inbound endpoints allow on-premises DNS resolvers to forward queries to Route 53 Resolver. Outbound endpoints allow Route 53 Resolver to forward queries to on-premises DNS resolvers.

**Synopsis:**
```bash
aws route53resolver create-resolver-endpoint \
    --creator-request-id <value> \
    --security-group-ids <value> \
    --direction <value> \
    --ip-addresses <value> \
    [--name <value>] \
    [--outpost-arn <value>] \
    [--preferred-instance-type <value>] \
    [--tags <value>] \
    [--resolver-endpoint-type <value>] \
    [--protocols <value>] \
    [--rni-enhanced-metrics-enabled | --no-rni-enhanced-metrics-enabled] \
    [--target-name-server-metrics-enabled | --no-target-name-server-metrics-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creator-request-id` | **Yes** | string | -- | Idempotency token (max 255 chars) |
| `--security-group-ids` | **Yes** | list(string) | -- | Security groups controlling access (max 64 chars each). Must allow TCP/UDP port 53 |
| `--direction` | **Yes** | string | -- | `INBOUND`, `OUTBOUND`, or `INBOUND_DELEGATION` |
| `--ip-addresses` | **Yes** | list(structure) | -- | Subnets and IPs for DNS queries (min 2, max 20) |
| `--name` | No | string | None | Friendly name (max 64 chars) |
| `--outpost-arn` | No | string | None | ARN of the Outpost (requires `--preferred-instance-type`) |
| `--preferred-instance-type` | No | string | None | EC2 instance type (requires `--outpost-arn`) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |
| `--resolver-endpoint-type` | No | string | None | IP type: `IPV4`, `IPV6`, or `DUALSTACK` |
| `--protocols` | No | list(string) | None | Protocols: `Do53`, `DoH`, `DoH-FIPS` (max 2) |
| `--rni-enhanced-metrics-enabled` | No | boolean | false | Enable 1-minute RNI metrics in CloudWatch |
| `--target-name-server-metrics-enabled` | No | boolean | false | Enable target name server metrics (outbound only) |

**ip-addresses Structure:**
```json
[
    {
        "SubnetId": "string",
        "Ip": "string",
        "Ipv6": "string"
    }
]
```
Shorthand: `SubnetId=string,Ip=string SubnetId=string,Ip=string`

**Output Schema:**
```json
{
    "ResolverEndpoint": {
        "Id": "string",
        "CreatorRequestId": "string",
        "Arn": "string",
        "Name": "string",
        "SecurityGroupIds": ["string"],
        "Direction": "INBOUND|OUTBOUND|INBOUND_DELEGATION",
        "IpAddressCount": "integer",
        "HostVPCId": "string",
        "Status": "CREATING|OPERATIONAL|UPDATING|AUTO_RECOVERING|ACTION_NEEDED|DELETING",
        "StatusMessage": "string",
        "CreationTime": "string",
        "ModificationTime": "string",
        "OutpostArn": "string",
        "PreferredInstanceType": "string",
        "ResolverEndpointType": "IPV4|IPV6|DUALSTACK",
        "Protocols": ["Do53|DoH|DoH-FIPS"],
        "RniEnhancedMetricsEnabled": "boolean",
        "TargetNameServerMetricsEnabled": "boolean"
    }
}
```

---

### 1.2 `delete-resolver-endpoint`

Deletes a resolver endpoint. Associated resolver rules must be disassociated first.

**Synopsis:**
```bash
aws route53resolver delete-resolver-endpoint \
    --resolver-endpoint-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-endpoint-id` | **Yes** | string | -- | The endpoint ID (max 64 chars) |

**Output Schema:**
Same as `create-resolver-endpoint` output.

---

### 1.3 `get-resolver-endpoint`

Gets details of a resolver endpoint.

**Synopsis:**
```bash
aws route53resolver get-resolver-endpoint \
    --resolver-endpoint-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-endpoint-id` | **Yes** | string | -- | The endpoint ID (max 64 chars) |

**Output Schema:**
Same as `create-resolver-endpoint` output.

---

### 1.4 `list-resolver-endpoints`

Lists all resolver endpoints in the account. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-resolver-endpoints \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:** `CreatorRequestId`, `Direction`, `HostVPCId`, `IpAddressCount`, `Name`, `SecurityGroupIds`, `Status`

**Output Schema:**
```json
{
    "ResolverEndpoints": [
        {
            "Id": "string",
            "CreatorRequestId": "string",
            "Arn": "string",
            "Name": "string",
            "SecurityGroupIds": ["string"],
            "Direction": "INBOUND|OUTBOUND|INBOUND_DELEGATION",
            "IpAddressCount": "integer",
            "HostVPCId": "string",
            "Status": "string",
            "StatusMessage": "string",
            "CreationTime": "string",
            "ModificationTime": "string",
            "ResolverEndpointType": "string",
            "Protocols": ["string"]
        }
    ],
    "NextToken": "string",
    "MaxResults": "integer"
}
```

---

### 1.5 `update-resolver-endpoint`

Updates the name, protocols, or endpoint type of a resolver endpoint.

**Synopsis:**
```bash
aws route53resolver update-resolver-endpoint \
    --resolver-endpoint-id <value> \
    [--name <value>] \
    [--resolver-endpoint-type <value>] \
    [--update-ip-addresses <value>] \
    [--protocols <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-endpoint-id` | **Yes** | string | -- | The endpoint ID (max 64 chars) |
| `--name` | No | string | None | New friendly name (max 64 chars) |
| `--resolver-endpoint-type` | No | string | None | New IP type: `IPV4`, `IPV6`, or `DUALSTACK` |
| `--update-ip-addresses` | No | list(structure) | None | IP addresses to update with new subnets |
| `--protocols` | No | list(string) | None | New protocols: `Do53`, `DoH`, `DoH-FIPS` |

**Output Schema:**
Same as `create-resolver-endpoint` output.

---

### 1.6 `associate-resolver-endpoint-ip-address`

Adds an IP address to an existing resolver endpoint. The endpoint must already have at least 2 IP addresses.

**Synopsis:**
```bash
aws route53resolver associate-resolver-endpoint-ip-address \
    --resolver-endpoint-id <value> \
    --ip-address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-endpoint-id` | **Yes** | string | -- | The endpoint ID (max 64 chars) |
| `--ip-address` | **Yes** | structure | -- | The IP to add. Shorthand: `SubnetId=string,Ip=string,Ipv6=string` |

**Output Schema:**
Same as `create-resolver-endpoint` output.

---

### 1.7 `disassociate-resolver-endpoint-ip-address`

Removes an IP address from a resolver endpoint. The endpoint must retain at least 2 IP addresses.

**Synopsis:**
```bash
aws route53resolver disassociate-resolver-endpoint-ip-address \
    --resolver-endpoint-id <value> \
    --ip-address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-endpoint-id` | **Yes** | string | -- | The endpoint ID (max 64 chars) |
| `--ip-address` | **Yes** | structure | -- | The IP to remove. Shorthand: `IpId=string,SubnetId=string,Ip=string,Ipv6=string` |

**Output Schema:**
Same as `create-resolver-endpoint` output.

---

### 1.8 `list-resolver-endpoint-ip-addresses`

Lists the IP addresses associated with a resolver endpoint. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-resolver-endpoint-ip-addresses \
    --resolver-endpoint-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-endpoint-id` | **Yes** | string | -- | The endpoint ID (max 64 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "IpAddresses": [
        {
            "IpId": "string",
            "SubnetId": "string",
            "Ip": "string",
            "Ipv6": "string",
            "Status": "CREATING|FAILED_CREATION|ATTACHING|ATTACHED|REMAP_DETACHING|REMAP_ATTACHING|DETACHING|FAILED_RESOURCE_GONE|DELETING|DELETE_FAILED_FAS_EXPIRED|UPDATING",
            "StatusMessage": "string",
            "CreationTime": "string",
            "ModificationTime": "string"
        }
    ],
    "NextToken": "string",
    "MaxResults": "integer"
}
```
