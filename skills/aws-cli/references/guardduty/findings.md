# Findings

### 2.1 `get-findings`

Describes Amazon GuardDuty findings specified by finding IDs.

**Synopsis:**
```bash
aws guardduty get-findings \
    --detector-id <value> \
    --finding-ids <value> \
    [--sort-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--finding-ids` | **Yes** | list(string) | -- | Finding IDs to retrieve (max 50, each 1-300 chars) |
| `--sort-criteria` | No | structure | None | Sort criteria for the findings |

**Sort Criteria Structure:**
```json
{
    "AttributeName": "string",
    "OrderBy": "ASC|DESC"
}
```

**Output Schema:**
```json
{
    "Findings": [
        {
            "AccountId": "string",
            "Arn": "string",
            "Confidence": "double",
            "CreatedAt": "string",
            "Description": "string",
            "Id": "string",
            "Partition": "string",
            "Region": "string",
            "Severity": "double",
            "Title": "string",
            "Type": "string",
            "UpdatedAt": "string",
            "Resource": {
                "ResourceType": "string",
                "AccessKeyDetails": {
                    "AccessKeyId": "string",
                    "PrincipalId": "string",
                    "UserName": "string",
                    "UserType": "string"
                },
                "InstanceDetails": {
                    "AvailabilityZone": "string",
                    "ImageId": "string",
                    "InstanceId": "string",
                    "InstanceState": "string",
                    "InstanceType": "string",
                    "LaunchTime": "string",
                    "NetworkInterfaces": [],
                    "Platform": "string",
                    "Tags": []
                },
                "S3BucketDetails": [],
                "EksClusterDetails": {},
                "EcsClusterDetails": {},
                "ContainerDetails": {},
                "RdsDbInstanceDetails": {},
                "LambdaDetails": {}
            },
            "Service": {
                "Action": {
                    "ActionType": "string",
                    "AwsApiCallAction": {},
                    "DnsRequestAction": {},
                    "NetworkConnectionAction": {},
                    "PortProbeAction": {}
                },
                "Evidence": {
                    "ThreatIntelligenceDetails": [
                        {
                            "ThreatListName": "string",
                            "ThreatNames": ["string"]
                        }
                    ]
                },
                "Archived": "boolean",
                "Count": "integer",
                "DetectorId": "string",
                "EventFirstSeen": "string",
                "EventLastSeen": "string",
                "ResourceRole": "string",
                "ServiceName": "string",
                "UserFeedback": "string",
                "FeatureName": "string",
                "EbsVolumeScanDetails": {},
                "RuntimeDetails": {},
                "Detection": {}
            },
            "SchemaVersion": "string"
        }
    ]
}
```

---

### 2.2 `list-findings`

Lists Amazon GuardDuty findings for the specified detector. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-findings \
    --detector-id <value> \
    [--finding-criteria <value>] \
    [--sort-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--finding-criteria` | No | structure | None | Criteria for filtering findings |
| `--sort-criteria` | No | structure | None | Sort criteria for the findings |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (1-50) |
| `--max-items` | No | integer | None | Total items to return |

**Finding Criteria Structure:**
```json
{
    "Criterion": {
        "string": {
            "Eq": ["string"],
            "Neq": ["string"],
            "Gt": "integer",
            "Gte": "integer",
            "Lt": "integer",
            "Lte": "integer",
            "Equals": ["string"],
            "NotEquals": ["string"],
            "GreaterThan": "long",
            "GreaterThanOrEqual": "long",
            "LessThan": "long",
            "LessThanOrEqual": "long"
        }
    }
}
```

**Output Schema:**
```json
{
    "FindingIds": ["string"],
    "NextToken": "string"
}
```

---

### 2.3 `get-findings-statistics`

Lists Amazon GuardDuty finding statistics for the specified detector.

**Synopsis:**
```bash
aws guardduty get-findings-statistics \
    --detector-id <value> \
    --finding-statistic-types <value> \
    [--finding-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--finding-statistic-types` | **Yes** | list(string) | -- | Statistic types: `COUNT_BY_SEVERITY` |
| `--finding-criteria` | No | structure | None | Criteria for filtering findings |

**Output Schema:**
```json
{
    "FindingStatistics": {
        "CountBySeverity": {
            "string": "integer"
        }
    }
}
```

---

### 2.4 `archive-findings`

Archives Amazon GuardDuty findings specified by the list of finding IDs.

**Synopsis:**
```bash
aws guardduty archive-findings \
    --detector-id <value> \
    --finding-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--finding-ids` | **Yes** | list(string) | -- | Finding IDs to archive (max 50) |

**Output:** None (HTTP 200 on success)

---

### 2.5 `unarchive-findings`

Unarchives Amazon GuardDuty findings specified by the list of finding IDs.

**Synopsis:**
```bash
aws guardduty unarchive-findings \
    --detector-id <value> \
    --finding-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--finding-ids` | **Yes** | list(string) | -- | Finding IDs to unarchive (max 50) |

**Output:** None (HTTP 200 on success)

---

### 2.6 `update-findings-feedback`

Marks the specified GuardDuty findings as useful or not useful.

**Synopsis:**
```bash
aws guardduty update-findings-feedback \
    --detector-id <value> \
    --finding-ids <value> \
    --feedback <value> \
    [--comments <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--finding-ids` | **Yes** | list(string) | -- | Finding IDs to update (max 50) |
| `--feedback` | **Yes** | string | -- | Feedback value: `USEFUL` or `NOT_USEFUL` |
| `--comments` | No | string | None | Additional feedback comments |

**Output:** None (HTTP 200 on success)

---

### 2.7 `create-sample-findings`

Generates example findings of types specified by the list of finding types. Used for testing.

**Synopsis:**
```bash
aws guardduty create-sample-findings \
    --detector-id <value> \
    [--finding-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--finding-types` | No | list(string) | None | Types of sample findings to generate |

**Output:** None (HTTP 200 on success)
