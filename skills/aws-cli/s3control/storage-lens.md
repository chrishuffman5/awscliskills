# Storage Lens

### 6.1 `put-storage-lens-configuration`

Creates or updates an S3 Storage Lens configuration for account-level storage metrics and analytics.

**Synopsis:**
```bash
aws s3control put-storage-lens-configuration \
    --config-id <value> \
    --account-id <value> \
    --storage-lens-configuration <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-id` | **Yes** | string | -- | Configuration ID (1-64 chars, pattern: `[a-zA-Z0-9\-\_\.]+`) |
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--storage-lens-configuration` | **Yes** | structure | -- | Storage Lens configuration (see below) |
| `--tags` | No | list | None | Tag set (max 50). Shorthand: `Key=string,Value=string ...` |

**StorageLensConfiguration Structure:**
```json
{
    "Id": "string",
    "AccountLevel": {
        "ActivityMetrics": {"IsEnabled": true|false},
        "BucketLevel": {
            "ActivityMetrics": {"IsEnabled": true|false},
            "PrefixLevel": {
                "StorageMetrics": {
                    "IsEnabled": true|false,
                    "SelectionCriteria": {
                        "Delimiter": "string",
                        "MaxDepth": "integer",
                        "MinStorageBytesPercentage": "double"
                    }
                }
            },
            "AdvancedCostOptimizationMetrics": {"IsEnabled": true|false},
            "AdvancedDataProtectionMetrics": {"IsEnabled": true|false},
            "DetailedStatusCodesMetrics": {"IsEnabled": true|false},
            "AdvancedPerformanceMetrics": {"IsEnabled": true|false}
        },
        "AdvancedCostOptimizationMetrics": {"IsEnabled": true|false},
        "AdvancedDataProtectionMetrics": {"IsEnabled": true|false},
        "DetailedStatusCodesMetrics": {"IsEnabled": true|false},
        "AdvancedPerformanceMetrics": {"IsEnabled": true|false},
        "StorageLensGroupLevel": {
            "SelectionCriteria": {
                "Include": ["string"],
                "Exclude": ["string"]
            }
        }
    },
    "Include": {
        "Buckets": ["string"],
        "Regions": ["string"]
    },
    "Exclude": {
        "Buckets": ["string"],
        "Regions": ["string"]
    },
    "DataExport": {
        "S3BucketDestination": {
            "Format": "CSV|Parquet",
            "OutputSchemaVersion": "V_1",
            "AccountId": "string",
            "Arn": "string",
            "Prefix": "string",
            "Encryption": {
                "SSES3": {},
                "SSEKMS": {"KeyId": "string"}
            }
        },
        "CloudWatchMetrics": {"IsEnabled": true|false}
    },
    "IsEnabled": true|false,
    "AwsOrg": {"Arn": "string"}
}
```

**Output:** None

---

### 6.2 `get-storage-lens-configuration`

Gets an S3 Storage Lens configuration.

**Synopsis:**
```bash
aws s3control get-storage-lens-configuration \
    --config-id <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-id` | **Yes** | string | -- | Configuration ID |
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output Schema:**
```json
{
    "StorageLensConfiguration": {
        "Id": "string",
        "AccountLevel": {
            "ActivityMetrics": {"IsEnabled": true|false},
            "BucketLevel": {
                "ActivityMetrics": {"IsEnabled": true|false},
                "PrefixLevel": {
                    "StorageMetrics": {
                        "IsEnabled": true|false,
                        "SelectionCriteria": {
                            "Delimiter": "string",
                            "MaxDepth": "integer",
                            "MinStorageBytesPercentage": "double"
                        }
                    }
                },
                "AdvancedCostOptimizationMetrics": {"IsEnabled": true|false},
                "AdvancedDataProtectionMetrics": {"IsEnabled": true|false},
                "DetailedStatusCodesMetrics": {"IsEnabled": true|false},
                "AdvancedPerformanceMetrics": {"IsEnabled": true|false}
            },
            "AdvancedCostOptimizationMetrics": {"IsEnabled": true|false},
            "AdvancedDataProtectionMetrics": {"IsEnabled": true|false},
            "DetailedStatusCodesMetrics": {"IsEnabled": true|false},
            "AdvancedPerformanceMetrics": {"IsEnabled": true|false},
            "StorageLensGroupLevel": {
                "SelectionCriteria": {
                    "Include": ["string"],
                    "Exclude": ["string"]
                }
            }
        },
        "Include": {
            "Buckets": ["string"],
            "Regions": ["string"]
        },
        "Exclude": {
            "Buckets": ["string"],
            "Regions": ["string"]
        },
        "DataExport": {
            "S3BucketDestination": {},
            "CloudWatchMetrics": {"IsEnabled": true|false}
        },
        "IsEnabled": true|false,
        "AwsOrg": {"Arn": "string"},
        "StorageLensArn": "string"
    }
}
```

---

### 6.3 `delete-storage-lens-configuration`

Deletes an S3 Storage Lens configuration.

**Synopsis:**
```bash
aws s3control delete-storage-lens-configuration \
    --config-id <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-id` | **Yes** | string | -- | Configuration ID |
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output:** None

---

### 6.4 `list-storage-lens-configurations`

Lists S3 Storage Lens configurations in the account. **Paginated.**

**Synopsis:**
```bash
aws s3control list-storage-lens-configurations \
    --account-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "StorageLensConfigurationList": [
        {
            "Id": "string",
            "StorageLensArn": "string",
            "HomeRegion": "string",
            "IsEnabled": true|false
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `put-storage-lens-configuration-tagging`

Sets the tags on a Storage Lens configuration. Replaces all existing tags.

**Synopsis:**
```bash
aws s3control put-storage-lens-configuration-tagging \
    --config-id <value> \
    --account-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-id` | **Yes** | string | -- | Configuration ID |
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--tags` | **Yes** | list | -- | Tag set. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 6.6 `get-storage-lens-configuration-tagging`

Gets the tags for a Storage Lens configuration.

**Synopsis:**
```bash
aws s3control get-storage-lens-configuration-tagging \
    --config-id <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-id` | **Yes** | string | -- | Configuration ID |
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 6.7 `delete-storage-lens-configuration-tagging`

Removes all tags from a Storage Lens configuration.

**Synopsis:**
```bash
aws s3control delete-storage-lens-configuration-tagging \
    --config-id <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-id` | **Yes** | string | -- | Configuration ID |
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output:** None

---

### 6.8 `create-storage-lens-group`

Creates a Storage Lens group for grouping metrics using custom filter criteria.

**Synopsis:**
```bash
aws s3control create-storage-lens-group \
    --account-id <value> \
    --storage-lens-group <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--storage-lens-group` | **Yes** | structure | -- | Storage Lens group definition |
| `--tags` | No | list | None | Key-value tags |

**StorageLensGroup Structure:**
```json
{
    "Name": "string",
    "Filter": {
        "MatchAnyPrefix": ["string"],
        "MatchAnySuffix": ["string"],
        "MatchAnyTag": [{"Key": "string", "Value": "string"}],
        "MatchObjectAge": {
            "DaysGreaterThan": "integer",
            "DaysLessThan": "integer"
        },
        "MatchObjectSize": {
            "BytesGreaterThan": "long",
            "BytesLessThan": "long"
        },
        "And": {},
        "Or": {}
    }
}
```

**Output:** None

---

### 6.9 `get-storage-lens-group`

Gets a Storage Lens group.

**Synopsis:**
```bash
aws s3control get-storage-lens-group \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Storage Lens group name |

**Output Schema:**
```json
{
    "StorageLensGroup": {
        "Name": "string",
        "Filter": {
            "MatchAnyPrefix": ["string"],
            "MatchAnySuffix": ["string"],
            "MatchAnyTag": [{"Key": "string", "Value": "string"}],
            "MatchObjectAge": {
                "DaysGreaterThan": "integer",
                "DaysLessThan": "integer"
            },
            "MatchObjectSize": {
                "BytesGreaterThan": "long",
                "BytesLessThan": "long"
            },
            "And": {},
            "Or": {}
        },
        "StorageLensGroupArn": "string"
    }
}
```

---

### 6.10 `list-storage-lens-groups`

Lists Storage Lens groups in the account. **Paginated.**

**Synopsis:**
```bash
aws s3control list-storage-lens-groups \
    --account-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "StorageLensGroupList": [
        {
            "Name": "string",
            "StorageLensGroupArn": "string",
            "HomeRegion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.11 `update-storage-lens-group`

Updates an existing Storage Lens group.

**Synopsis:**
```bash
aws s3control update-storage-lens-group \
    --account-id <value> \
    --name <value> \
    --storage-lens-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Storage Lens group name |
| `--storage-lens-group` | **Yes** | structure | -- | Updated group definition (same structure as create) |

**Output:** None

---

### 6.12 `delete-storage-lens-group`

Deletes a Storage Lens group.

**Synopsis:**
```bash
aws s3control delete-storage-lens-group \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Storage Lens group name |

**Output:** None
