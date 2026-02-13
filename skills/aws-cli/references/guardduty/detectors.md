# Detectors

### 1.1 `create-detector`

Creates a new Amazon GuardDuty detector. Each AWS account can have one detector per region.

**Synopsis:**
```bash
aws guardduty create-detector \
    --enable | --no-enable \
    [--client-token <value>] \
    [--finding-publishing-frequency <value>] \
    [--data-sources <value>] \
    [--tags <value>] \
    [--features <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enable` / `--no-enable` | **Yes** | boolean | -- | Whether the detector is enabled |
| `--client-token` | No | string | None | Idempotency token (0-64 chars) |
| `--finding-publishing-frequency` | No | string | `SIX_HOURS` | Export frequency: `FIFTEEN_MINUTES`, `ONE_HOUR`, `SIX_HOURS` |
| `--data-sources` | No | structure | None | Data sources to enable (deprecated, use --features) |
| `--tags` | No | map | None | Tags to add (max 200, keys 1-128 chars, values max 256 chars) |
| `--features` | No | list | None | Features to configure for the detector |

**Features Structure:**
```json
[
    {
        "Name": "S3_DATA_EVENTS|EKS_AUDIT_LOGS|EBS_MALWARE_PROTECTION|RDS_LOGIN_EVENTS|EKS_RUNTIME_MONITORING|LAMBDA_NETWORK_LOGS|RUNTIME_MONITORING",
        "Status": "ENABLED|DISABLED",
        "AdditionalConfiguration": [
            {
                "Name": "EKS_ADDON_MANAGEMENT|ECS_FARGATE_AGENT_MANAGEMENT|EC2_AGENT_MANAGEMENT",
                "Status": "ENABLED|DISABLED"
            }
        ]
    }
]
```

**Output Schema:**
```json
{
    "DetectorId": "string",
    "UnprocessedDataSources": {
        "MalwareProtection": {
            "ScanEc2InstanceWithFindings": {
                "EbsVolumes": {
                    "Status": "ENABLED|DISABLED",
                    "Reason": "string"
                }
            },
            "ServiceRole": "string"
        }
    }
}
```

---

### 1.2 `delete-detector`

Deletes an Amazon GuardDuty detector.

**Synopsis:**
```bash
aws guardduty delete-detector \
    --detector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The unique ID of the detector to delete (1-300 chars) |

**Output:** None (HTTP 200 on success)

---

### 1.3 `get-detector`

Retrieves an Amazon GuardDuty detector specified by the detector ID.

**Synopsis:**
```bash
aws guardduty get-detector \
    --detector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The unique ID of the detector to retrieve (1-300 chars) |

**Output Schema:**
```json
{
    "CreatedAt": "string",
    "UpdatedAt": "string",
    "Status": "ENABLED|DISABLED",
    "ServiceRole": "string",
    "FindingPublishingFrequency": "FIFTEEN_MINUTES|ONE_HOUR|SIX_HOURS",
    "Tags": {
        "string": "string"
    },
    "DataSources": {
        "CloudTrail": {
            "Status": "ENABLED|DISABLED"
        },
        "DNSLogs": {
            "Status": "ENABLED|DISABLED"
        },
        "FlowLogs": {
            "Status": "ENABLED|DISABLED"
        },
        "S3Logs": {
            "Status": "ENABLED|DISABLED"
        },
        "Kubernetes": {
            "AuditLogs": {
                "Status": "ENABLED|DISABLED"
            }
        },
        "MalwareProtection": {
            "ScanEc2InstanceWithFindings": {
                "EbsVolumes": {
                    "Status": "ENABLED|DISABLED",
                    "Reason": "string"
                }
            },
            "ServiceRole": "string"
        }
    },
    "Features": [
        {
            "Name": "string",
            "Status": "ENABLED|DISABLED",
            "UpdatedAt": "timestamp",
            "AdditionalConfiguration": [
                {
                    "Name": "string",
                    "Status": "ENABLED|DISABLED",
                    "UpdatedAt": "timestamp"
                }
            ]
        }
    ]
}
```

---

### 1.4 `list-detectors`

Lists all GuardDuty detector IDs. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-detectors \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (1-50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DetectorIds": ["string"],
    "NextToken": "string"
}
```

---

### 1.5 `update-detector`

Updates the Amazon GuardDuty detector specified by the detector ID.

**Synopsis:**
```bash
aws guardduty update-detector \
    --detector-id <value> \
    [--enable | --no-enable] \
    [--finding-publishing-frequency <value>] \
    [--data-sources <value>] \
    [--features <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The unique ID of the detector to update (1-300 chars) |
| `--enable` / `--no-enable` | No | boolean | None | Whether the detector is enabled |
| `--finding-publishing-frequency` | No | string | None | Export frequency: `FIFTEEN_MINUTES`, `ONE_HOUR`, `SIX_HOURS` |
| `--data-sources` | No | structure | None | Data sources to configure (deprecated, use --features) |
| `--features` | No | list | None | Features to configure |

**Output:** None (HTTP 200 on success)
