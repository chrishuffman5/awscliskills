# Records

### 2.1 `change-resource-record-sets`

Creates, updates, or deletes DNS records in a hosted zone. Changes are transactional: all succeed or all fail. DNS propagation typically completes within 60 seconds.

**Synopsis:**
```bash
aws route53 change-resource-record-sets \
    --hosted-zone-id <value> \
    --change-batch <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--change-batch` | **Yes** | structure | -- | JSON change batch. Supports `file://` syntax |

**Change Batch Structure:**
```json
{
    "Comment": "string",
    "Changes": [
        {
            "Action": "CREATE|DELETE|UPSERT",
            "ResourceRecordSet": {
                "Name": "string",
                "Type": "A|AAAA|CNAME|MX|TXT|NS|SOA|SRV|CAA|DS|NAPTR|PTR|SPF|TLSA|SSHFP|SVCB|HTTPS",
                "SetIdentifier": "string",
                "Weight": "long",
                "Region": "string",
                "GeoLocation": {
                    "ContinentCode": "string",
                    "CountryCode": "string",
                    "SubdivisionCode": "string"
                },
                "Failover": "PRIMARY|SECONDARY",
                "MultiValueAnswer": true|false,
                "TTL": "long",
                "ResourceRecords": [
                    {
                        "Value": "string"
                    }
                ],
                "AliasTarget": {
                    "HostedZoneId": "string",
                    "DNSName": "string",
                    "EvaluateTargetHealth": true|false
                },
                "HealthCheckId": "string",
                "CidrRoutingConfig": {
                    "CollectionId": "string",
                    "LocationName": "string"
                },
                "GeoProximityLocation": {
                    "AWSRegion": "string",
                    "LocalZoneGroup": "string",
                    "Coordinates": {
                        "Latitude": "string",
                        "Longitude": "string"
                    },
                    "Bias": "integer"
                }
            }
        }
    ]
}
```

**Action Types:**

| Action | Description |
|--------|-------------|
| `CREATE` | Creates a record. Fails if the record already exists |
| `DELETE` | Deletes an existing record. Must specify all original values exactly |
| `UPSERT` | Creates a new record or updates existing. Preferred for idempotent operations |

**Change Batch Field Constraints:**

| Field | Constraints |
|-------|-------------|
| `Comment` | Max 256 chars |
| `Changes` | Min 1 change |
| `Name` | Max 1024 chars |
| `SetIdentifier` | 1-128 chars (required for weighted, latency, failover, geolocation, multivalue) |
| `Weight` | 0-255 (for weighted routing) |
| `TTL` | 0-2147483647 (do not set for alias records) |
| `ResourceRecords[].Value` | Max 4000 chars |
| `AliasTarget.HostedZoneId` | Max 32 chars |
| `AliasTarget.DNSName` | Max 1024 chars |
| `HealthCheckId` | Max 64 chars |
| `GeoProximityLocation.Bias` | -99 to 99 |

> **Note:** Alias records must not include `TTL` or `ResourceRecords`; use `AliasTarget` instead. To delete a record, all values must match exactly.

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

### 2.2 `list-resource-record-sets`

Lists DNS records in a hosted zone. Returns up to 300 records per response. **Paginated operation.**

**Synopsis:**
```bash
aws route53 list-resource-record-sets \
    --hosted-zone-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | string | None | Items per API call |
| `--max-items` | No | string | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceRecordSets": [
        {
            "Name": "string",
            "Type": "A|AAAA|CAA|CNAME|DS|MX|NAPTR|NS|PTR|SOA|SPF|SRV|TXT|TLSA|SSHFP|SVCB|HTTPS",
            "SetIdentifier": "string",
            "Weight": "long",
            "Region": "string",
            "GeoLocation": {
                "ContinentCode": "string",
                "CountryCode": "string",
                "SubdivisionCode": "string"
            },
            "Failover": "PRIMARY|SECONDARY",
            "MultiValueAnswer": true|false,
            "TTL": "long",
            "ResourceRecords": [
                {
                    "Value": "string"
                }
            ],
            "AliasTarget": {
                "HostedZoneId": "string",
                "DNSName": "string",
                "EvaluateTargetHealth": true|false
            },
            "HealthCheckId": "string",
            "TrafficPolicyInstanceId": "string",
            "CidrRoutingConfig": {
                "CollectionId": "string",
                "LocationName": "string"
            },
            "GeoProximityLocation": {
                "AWSRegion": "string",
                "LocalZoneGroup": "string",
                "Coordinates": {
                    "Latitude": "string",
                    "Longitude": "string"
                },
                "Bias": "integer"
            }
        }
    ],
    "IsTruncated": true|false,
    "NextRecordName": "string",
    "NextRecordType": "string",
    "NextRecordIdentifier": "string",
    "MaxItems": "string"
}
```

---

### 2.3 `test-dns-answer`

Simulates a DNS query response from Route 53. Only supports public hosted zones.

**Synopsis:**
```bash
aws route53 test-dns-answer \
    --hosted-zone-id <value> \
    --record-name <value> \
    --record-type <value> \
    [--resolver-ip <value>] \
    [--edns0-client-subnet-ip <value>] \
    [--edns0-client-subnet-mask <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Hosted zone ID (max 32 chars) |
| `--record-name` | **Yes** | string | -- | Record name to query (max 1024 chars) |
| `--record-type` | **Yes** | string | -- | Record type: `A`, `AAAA`, `CNAME`, `MX`, `TXT`, `NS`, `SOA`, `SRV`, `CAA`, `DS`, `NAPTR`, `PTR`, `SPF`, `TLSA`, `SSHFP`, `SVCB`, `HTTPS` |
| `--resolver-ip` | No | string | None | DNS resolver IP to simulate (max 45 chars) |
| `--edns0-client-subnet-ip` | No | string | None | Client IP for EDNS0 (max 45 chars) |
| `--edns0-client-subnet-mask` | No | string | None | Subnet mask bits. IPv4: 0-32 (default 24), IPv6: 0-128 (default 64) |

**Output Schema:**
```json
{
    "Nameserver": "string",
    "RecordName": "string",
    "RecordType": "string",
    "RecordData": ["string"],
    "ResponseCode": "string",
    "Protocol": "string"
}
```

---

### 2.4 `get-change`

Returns the current status of a change batch request. Use to poll until status is `INSYNC`.

**Synopsis:**
```bash
aws route53 get-change \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Change batch ID returned by `change-resource-record-sets` (1-6500 chars) |

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

> **Tip:** Use `aws route53 wait resource-record-sets-changed --id <change-id>` to block until the change is `INSYNC`.

---
