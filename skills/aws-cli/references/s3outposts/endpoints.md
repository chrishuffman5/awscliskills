# Endpoints

### 1.1 `create-endpoint`

Creates an endpoint and associates it with the specified Outpost. The action can take up to 5 minutes to complete.

**Synopsis:**
```bash
aws s3outposts create-endpoint \
    --outpost-id <value> \
    --subnet-id <value> \
    --security-group-id <value> \
    [--access-type <value>] \
    [--customer-owned-ipv4-pool <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-id` | **Yes** | string | -- | ID of the Outpost (pattern: `op-[a-f0-9]{17}`) |
| `--subnet-id` | **Yes** | string | -- | Subnet ID in the selected VPC (must belong to the Outpost) |
| `--security-group-id` | **Yes** | string | -- | Security group ID for the endpoint |
| `--access-type` | No | string | `Private` | `Private` (VPC) or `CustomerOwnedIp` (on-premises) |
| `--customer-owned-ipv4-pool` | No | string | -- | CoIP pool ID (required if `access-type` is `CustomerOwnedIp`) |

**Output Schema:**
```json
{
    "EndpointArn": "string"
}
```

---

### 1.2 `delete-endpoint`

Deletes an endpoint. The action can take up to 5 minutes to complete.

**Synopsis:**
```bash
aws s3outposts delete-endpoint \
    --endpoint-id <value> \
    --outpost-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-id` | **Yes** | string | -- | Endpoint ID (19-char alphanumeric) |
| `--outpost-id` | **Yes** | string | -- | ID of the Outpost |

**Output Schema:** None (HTTP 200 on success).

---

### 1.3 `list-endpoints`

Lists endpoints associated with the specified Outpost. **Paginated operation.**

**Synopsis:**
```bash
aws s3outposts list-endpoints \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Endpoints": [
        {
            "EndpointArn": "string",
            "OutpostsId": "string",
            "CidrBlock": "string",
            "Status": "Pending|Available|Deleting|Create_Failed|Delete_Failed",
            "CreationTime": "timestamp",
            "NetworkInterfaces": [
                {
                    "NetworkInterfaceId": "string"
                }
            ],
            "VpcId": "string",
            "SubnetId": "string",
            "SecurityGroupId": "string",
            "AccessType": "Private|CustomerOwnedIp",
            "CustomerOwnedIpv4Pool": "string",
            "FailedReason": {
                "ErrorCode": "string",
                "Message": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `list-outposts-with-s3`

Lists the Outposts with S3 on Outposts capacity for your account. **Paginated operation.**

**Synopsis:**
```bash
aws s3outposts list-outposts-with-s3 \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Outposts": [
        {
            "OutpostArn": "string",
            "S3OutpostArn": "string",
            "OutpostId": "string",
            "OwnerId": "string",
            "CapacityInBytes": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `list-shared-endpoints`

Lists all endpoints associated with an Outpost that have been shared by using AWS Resource Access Manager (RAM). **Paginated operation.**

**Synopsis:**
```bash
aws s3outposts list-shared-endpoints \
    --outpost-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-id` | **Yes** | string | -- | ID of the Outpost |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Endpoints": [
        {
            "EndpointArn": "string",
            "OutpostsId": "string",
            "CidrBlock": "string",
            "Status": "Pending|Available|Deleting|Create_Failed|Delete_Failed",
            "CreationTime": "timestamp",
            "NetworkInterfaces": [
                {
                    "NetworkInterfaceId": "string"
                }
            ],
            "VpcId": "string",
            "SubnetId": "string",
            "SecurityGroupId": "string",
            "AccessType": "Private|CustomerOwnedIp",
            "CustomerOwnedIpv4Pool": "string",
            "FailedReason": {
                "ErrorCode": "string",
                "Message": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
