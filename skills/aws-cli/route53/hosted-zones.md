# Hosted Zones

### 1.1 `create-hosted-zone`

Creates a new hosted zone. For public hosted zones, Route 53 automatically creates NS and SOA records. For private hosted zones, you must associate a VPC.

**Synopsis:**
```bash
aws route53 create-hosted-zone \
    --name <value> \
    --caller-reference <value> \
    [--vpc <value>] \
    [--hosted-zone-config <value>] \
    [--delegation-set-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain name (max 1024 chars). Trailing dot optional |
| `--caller-reference` | **Yes** | string | -- | Unique string for retry safety (1-128 chars) |
| `--vpc` | No | structure | None | VPC to associate (private zones). Shorthand: `VPCRegion=string,VPCId=string` |
| `--hosted-zone-config` | No | structure | None | Shorthand: `Comment=string,PrivateZone=boolean` |
| `--delegation-set-id` | No | string | None | Reusable delegation set ID (max 32 chars) |

**Output Schema:**
```json
{
    "HostedZone": {
        "Id": "string",
        "Name": "string",
        "CallerReference": "string",
        "Config": {
            "Comment": "string",
            "PrivateZone": true|false
        },
        "ResourceRecordSetCount": "long",
        "LinkedService": {
            "ServicePrincipal": "string",
            "Description": "string"
        }
    },
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    },
    "DelegationSet": {
        "Id": "string",
        "CallerReference": "string",
        "NameServers": ["string"]
    },
    "VPC": {
        "VPCRegion": "string",
        "VPCId": "string"
    },
    "Location": "string"
}
```

---

### 1.2 `delete-hosted-zone`

Deletes a hosted zone. The zone must contain only default SOA and NS records, and DNSSEC signing must be disabled.

**Synopsis:**
```bash
aws route53 delete-hosted-zone \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    }
}
```

---

### 1.3 `get-hosted-zone`

Gets information about a specified hosted zone including its nameservers.

**Synopsis:**
```bash
aws route53 get-hosted-zone \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |

**Output Schema:**
```json
{
    "HostedZone": {
        "Id": "string",
        "Name": "string",
        "CallerReference": "string",
        "Config": {
            "Comment": "string",
            "PrivateZone": true|false
        },
        "ResourceRecordSetCount": "long",
        "LinkedService": {
            "ServicePrincipal": "string",
            "Description": "string"
        }
    },
    "DelegationSet": {
        "Id": "string",
        "CallerReference": "string",
        "NameServers": ["string"]
    },
    "VPCs": [
        {
            "VPCRegion": "string",
            "VPCId": "string"
        }
    ]
}
```

---

### 1.4 `list-hosted-zones`

Lists all hosted zones owned by the current account. **Paginated operation.**

**Synopsis:**
```bash
aws route53 list-hosted-zones \
    [--delegation-set-id <value>] \
    [--hosted-zone-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delegation-set-id` | No | string | None | Filter by reusable delegation set (max 32 chars) |
| `--hosted-zone-type` | No | string | None | Filter: `PrivateHostedZone` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "HostedZones": [
        {
            "Id": "string",
            "Name": "string",
            "CallerReference": "string",
            "Config": {
                "Comment": "string",
                "PrivateZone": true|false
            },
            "ResourceRecordSetCount": "long",
            "LinkedService": {
                "ServicePrincipal": "string",
                "Description": "string"
            }
        }
    ],
    "Marker": "string",
    "IsTruncated": true|false,
    "NextMarker": "string",
    "MaxItems": "string"
}
```

---

### 1.5 `list-hosted-zones-by-name`

Lists hosted zones ordered by domain name, with optional filtering by name prefix.

**Synopsis:**
```bash
aws route53 list-hosted-zones-by-name \
    [--dns-name <value>] \
    [--hosted-zone-id <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dns-name` | No | string | None | Start listing from this domain name (max 1024 chars) |
| `--hosted-zone-id` | No | string | None | Start listing from this hosted zone ID (max 32 chars) |
| `--max-items` | No | string | None | Maximum items to return (max 100) |

**Output Schema:**
```json
{
    "HostedZones": [
        {
            "Id": "string",
            "Name": "string",
            "CallerReference": "string",
            "Config": {
                "Comment": "string",
                "PrivateZone": true|false
            },
            "ResourceRecordSetCount": "long",
            "LinkedService": {
                "ServicePrincipal": "string",
                "Description": "string"
            }
        }
    ],
    "DNSName": "string",
    "HostedZoneId": "string",
    "IsTruncated": true|false,
    "NextDNSName": "string",
    "NextHostedZoneId": "string",
    "MaxItems": "string"
}
```

---

### 1.6 `update-hosted-zone-comment`

Updates the comment for a specified hosted zone.

**Synopsis:**
```bash
aws route53 update-hosted-zone-comment \
    --id <value> \
    [--comment <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--comment` | No | string | None | New comment (max 256 chars). Omit to remove existing comment |

**Output Schema:**
```json
{
    "HostedZone": {
        "Id": "string",
        "Name": "string",
        "CallerReference": "string",
        "Config": {
            "Comment": "string",
            "PrivateZone": true|false
        },
        "ResourceRecordSetCount": "long",
        "LinkedService": {
            "ServicePrincipal": "string",
            "Description": "string"
        }
    }
}
```

---

### 1.7 `associate-vpc-with-hosted-zone`

Associates a VPC with a private hosted zone.

**Synopsis:**
```bash
aws route53 associate-vpc-with-hosted-zone \
    --hosted-zone-id <value> \
    --vpc <value> \
    [--comment <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Private hosted zone ID (max 32 chars) |
| `--vpc` | **Yes** | structure | -- | Shorthand: `VPCRegion=string,VPCId=string` |
| `--comment` | No | string | None | Comment about the association |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    }
}
```

---

### 1.8 `disassociate-vpc-from-hosted-zone`

Disassociates a VPC from a private hosted zone. At least one VPC must remain associated.

**Synopsis:**
```bash
aws route53 disassociate-vpc-from-hosted-zone \
    --hosted-zone-id <value> \
    --vpc <value> \
    [--comment <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Private hosted zone ID (max 32 chars) |
| `--vpc` | **Yes** | structure | -- | Shorthand: `VPCRegion=string,VPCId=string` |
| `--comment` | No | string | None | Comment about the disassociation |

**Output Schema:**
```json
{
    "ChangeInfo": {
        "Id": "string",
        "Status": "PENDING|INSYNC",
        "SubmittedAt": "timestamp",
        "Comment": "string"
    }
}
```

---

### 1.9 `list-hosted-zones-by-vpc`

Lists all private hosted zones associated with a specified VPC.

**Synopsis:**
```bash
aws route53 list-hosted-zones-by-vpc \
    --vpc-id <value> \
    --vpc-region <value> \
    [--max-items <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-id` | **Yes** | string | -- | VPC ID (max 1024 chars) |
| `--vpc-region` | **Yes** | string | -- | AWS region of the VPC (1-64 chars) |
| `--max-items` | No | string | None | Maximum items to return |
| `--next-token` | No | string | None | Pagination token (max 256 chars) |

**Output Schema:**
```json
{
    "HostedZoneSummaries": [
        {
            "HostedZoneId": "string",
            "Name": "string",
            "Owner": {
                "OwningAccount": "string",
                "OwningService": "string"
            }
        }
    ],
    "MaxItems": "string",
    "NextToken": "string"
}
```

---

### 1.10 `get-hosted-zone-count`

Returns the total number of hosted zones in the current account.

**Synopsis:**
```bash
aws route53 get-hosted-zone-count \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (only global options).

**Output Schema:**
```json
{
    "HostedZoneCount": "long"
}
```

---

### 1.11 `get-hosted-zone-limit`

Gets the specified limit for a hosted zone (e.g., max number of records or VPCs).

**Synopsis:**
```bash
aws route53 get-hosted-zone-limit \
    --type <value> \
    --hosted-zone-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | `MAX_RRSETS_BY_ZONE` or `MAX_VPCS_ASSOCIATED_BY_ZONE` |
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |

**Output Schema:**
```json
{
    "Limit": {
        "Type": "MAX_RRSETS_BY_ZONE|MAX_VPCS_ASSOCIATED_BY_ZONE",
        "Value": "long"
    },
    "Count": "long"
}
```

---
