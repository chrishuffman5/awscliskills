# Data Lake

### 1.1 `create-data-lake`

Creates an Amazon Security Lake data lake with the specified configuration for one or more regions.

**Synopsis:**
```bash
aws securitylake create-data-lake \
    --configurations <value> \
    --meta-store-manager-role-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configurations` | **Yes** | list(structure) | -- | Region-specific data lake configurations (encryption, lifecycle, replication) |
| `--meta-store-manager-role-arn` | **Yes** | string | -- | IAM role ARN used to create/update the Glue table with partitions |
| `--tags` | No | list(structure) | None | Tags to associate (max 50). Structure: `key=string,value=string` |

**Configuration Structure:**
```json
{
    "encryptionConfiguration": {
        "kmsKeyId": "string"
    },
    "lifecycleConfiguration": {
        "expiration": {
            "days": "integer"
        },
        "transitions": [
            {
                "days": "integer",
                "storageClass": "string"
            }
        ]
    },
    "region": "string",
    "replicationConfiguration": {
        "regions": ["string"],
        "roleArn": "string"
    }
}
```

**Output Schema:**
```json
{
    "dataLakes": [
        {
            "createStatus": "INITIALIZED|PENDING|COMPLETED|FAILED",
            "dataLakeArn": "string",
            "encryptionConfiguration": {
                "kmsKeyId": "string"
            },
            "lifecycleConfiguration": {
                "expiration": {
                    "days": "integer"
                },
                "transitions": [
                    {
                        "days": "integer",
                        "storageClass": "string"
                    }
                ]
            },
            "region": "string",
            "replicationConfiguration": {
                "regions": ["string"],
                "roleArn": "string"
            },
            "s3BucketArn": "string",
            "updateStatus": {
                "exception": {
                    "code": "string",
                    "reason": "string"
                },
                "requestId": "string",
                "status": "INITIALIZED|PENDING|COMPLETED|FAILED"
            }
        }
    ]
}
```

---

### 1.2 `delete-data-lake`

Deletes the Amazon Security Lake data lake. When you delete the data lake, Security Lake is disabled in the specified regions.

**Synopsis:**
```bash
aws securitylake delete-data-lake \
    --regions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--regions` | **Yes** | list(string) | -- | List of regions where the data lake should be deleted |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.3 `update-data-lake`

Updates the configuration of an existing Security Lake data lake.

**Synopsis:**
```bash
aws securitylake update-data-lake \
    --configurations <value> \
    [--meta-store-manager-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configurations` | **Yes** | list(structure) | -- | Region-specific data lake configurations to update |
| `--meta-store-manager-role-arn` | No | string | -- | IAM role ARN for Glue table management |

**Output Schema:**
```json
{
    "dataLakes": [
        {
            "createStatus": "INITIALIZED|PENDING|COMPLETED|FAILED",
            "dataLakeArn": "string",
            "encryptionConfiguration": {
                "kmsKeyId": "string"
            },
            "lifecycleConfiguration": {
                "expiration": {
                    "days": "integer"
                },
                "transitions": [
                    {
                        "days": "integer",
                        "storageClass": "string"
                    }
                ]
            },
            "region": "string",
            "replicationConfiguration": {
                "regions": ["string"],
                "roleArn": "string"
            },
            "s3BucketArn": "string",
            "updateStatus": {
                "exception": {
                    "code": "string",
                    "reason": "string"
                },
                "requestId": "string",
                "status": "INITIALIZED|PENDING|COMPLETED|FAILED"
            }
        }
    ]
}
```

---

### 1.4 `list-data-lakes`

Lists Amazon Security Lake data lakes for the specified regions.

**Synopsis:**
```bash
aws securitylake list-data-lakes \
    [--regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--regions` | No | list(string) | All regions | AWS regions to list data lakes for |

**Output Schema:**
```json
{
    "dataLakes": [
        {
            "createStatus": "INITIALIZED|PENDING|COMPLETED|FAILED",
            "dataLakeArn": "string",
            "encryptionConfiguration": {
                "kmsKeyId": "string"
            },
            "lifecycleConfiguration": {
                "expiration": {
                    "days": "integer"
                },
                "transitions": [
                    {
                        "days": "integer",
                        "storageClass": "string"
                    }
                ]
            },
            "region": "string",
            "replicationConfiguration": {
                "regions": ["string"],
                "roleArn": "string"
            },
            "s3BucketArn": "string",
            "updateStatus": {
                "exception": {
                    "code": "string",
                    "reason": "string"
                },
                "requestId": "string",
                "status": "INITIALIZED|PENDING|COMPLETED|FAILED"
            }
        }
    ]
}
```

---

### 1.5 `create-data-lake-exception-subscription`

Creates a notification subscription for exceptions in your data lake. When errors occur, you are notified through the specified protocol.

**Synopsis:**
```bash
aws securitylake create-data-lake-exception-subscription \
    --notification-endpoint <value> \
    --subscription-protocol <value> \
    [--exception-time-to-live <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notification-endpoint` | **Yes** | string | -- | The endpoint to receive exception notifications (e.g., email address or URL) |
| `--subscription-protocol` | **Yes** | string | -- | Protocol for notifications: `HTTP`, `HTTPS`, `EMAIL`, `EMAIL_JSON`, `SMS`, `SQS`, `LAMBDA`, `APP`, `FIREHOSE` |
| `--exception-time-to-live` | No | long | -- | Time-to-live (TTL) for the exception message in days |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.6 `delete-data-lake-exception-subscription`

Deletes the exception notification subscription for the data lake.

**Synopsis:**
```bash
aws securitylake delete-data-lake-exception-subscription \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**

No output on success (HTTP 200).

---

### 1.7 `get-data-lake-exception-subscription`

Retrieves the details of the exception notification subscription for the data lake.

**Synopsis:**
```bash
aws securitylake get-data-lake-exception-subscription \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**
```json
{
    "exceptionTimeToLive": "long",
    "notificationEndpoint": "string",
    "subscriptionProtocol": "string"
}
```

---

### 1.8 `update-data-lake-exception-subscription`

Updates the exception notification subscription for the data lake.

**Synopsis:**
```bash
aws securitylake update-data-lake-exception-subscription \
    --notification-endpoint <value> \
    --subscription-protocol <value> \
    [--exception-time-to-live <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notification-endpoint` | **Yes** | string | -- | The endpoint to receive exception notifications |
| `--subscription-protocol` | **Yes** | string | -- | Protocol for notifications |
| `--exception-time-to-live` | No | long | -- | TTL for exception messages in days |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.9 `list-data-lake-exceptions`

Lists the exceptions that Security Lake has generated during data lake creation or updates. **Paginated operation.**

**Synopsis:**
```bash
aws securitylake list-data-lake-exceptions \
    [--regions <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--regions` | No | list(string) | All regions | Regions to list exceptions for |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "exceptions": [
        {
            "exception": "string",
            "region": "string",
            "remediation": "string",
            "timestamp": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.10 `get-data-lake-sources`

Retrieves a snapshot of the current region, including whether each source is contributing data to the data lake. **Paginated operation.**

**Synopsis:**
```bash
aws securitylake get-data-lake-sources \
    [--accounts <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accounts` | No | list(string) | All accounts | AWS account IDs to retrieve source status for |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "dataLakeArn": "string",
    "dataLakeSources": [
        {
            "account": "string",
            "eventClasses": [
                {
                    "eventClass": "string",
                    "logSources": [
                        {
                            "account": "string",
                            "region": "string",
                            "sources": [
                                {
                                    "eventClasses": ["string"],
                                    "sourceName": "string",
                                    "sourceStatuses": [
                                        {
                                            "resource": "string",
                                            "status": "ACTIVE|DEACTIVATED|PENDING"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ],
            "sourceName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.11 `create-data-lake-organization-configuration`

Automatically enables Security Lake for new member accounts in your organization.

**Synopsis:**
```bash
aws securitylake create-data-lake-organization-configuration \
    [--auto-enable-new-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-enable-new-account` | No | list(structure) | None | Configuration for auto-enabling sources in new accounts |

**Auto-enable Structure:**
```json
{
    "region": "string",
    "sources": [
        {
            "sourceName": "ROUTE53|VPC_FLOW|SH_FINDINGS|CLOUD_TRAIL_MGMT|LAMBDA_EXECUTION|S3_DATA|EKS_AUDIT|WAF",
            "sourceVersion": "string"
        }
    ]
}
```

**Output Schema:**

No output on success (HTTP 200).

---

### 1.12 `delete-data-lake-organization-configuration`

Removes automatic Security Lake configuration for new organization member accounts.

**Synopsis:**
```bash
aws securitylake delete-data-lake-organization-configuration \
    [--auto-enable-new-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-enable-new-account` | No | list(structure) | None | Configuration to remove for auto-enabling |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.13 `get-data-lake-organization-configuration`

Retrieves the organization auto-enable configuration for Security Lake.

**Synopsis:**
```bash
aws securitylake get-data-lake-organization-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**
```json
{
    "autoEnableNewAccount": [
        {
            "region": "string",
            "sources": [
                {
                    "sourceName": "string",
                    "sourceVersion": "string"
                }
            ]
        }
    ]
}
```

---

### 1.14 `register-data-lake-delegated-administrator`

Designates an account as the delegated administrator for Security Lake in your organization. Only the management account can call this.

**Synopsis:**
```bash
aws securitylake register-data-lake-delegated-administrator \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID to designate as delegated administrator |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.15 `deregister-data-lake-delegated-administrator`

Removes the delegated administrator for Security Lake. Only the management account can call this.

**Synopsis:**
```bash
aws securitylake deregister-data-lake-delegated-administrator \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**

No output on success (HTTP 200).
