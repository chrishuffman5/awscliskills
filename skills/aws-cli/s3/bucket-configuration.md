# Bucket Configuration

### 3.1 `put-bucket-policy`

Sets a bucket policy.

**Synopsis:**
```bash
aws s3api put-bucket-policy \
    --bucket <value> \
    --policy <value> \
    [--confirm-remove-self-bucket-access | --no-confirm-remove-self-bucket-access] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--policy` | **Yes** | string | -- | JSON policy document. Supports `file://` syntax |
| `--confirm-remove-self-bucket-access` | No | boolean | false | Confirm policy that removes your own access |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.2 `get-bucket-policy`

Returns the bucket policy.

**Synopsis:**
```bash
aws s3api get-bucket-policy \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 3.3 `delete-bucket-policy`

Deletes the bucket policy.

**Synopsis:**
```bash
aws s3api delete-bucket-policy \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.4 `get-bucket-policy-status`

Returns the policy status indicating whether the bucket is public.

**Synopsis:**
```bash
aws s3api get-bucket-policy-status \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "PolicyStatus": {
        "IsPublic": true|false
    }
}
```

---

### 3.5 `put-bucket-versioning`

Sets the versioning state of a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-versioning \
    --bucket <value> \
    --versioning-configuration <value> \
    [--mfa <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--versioning-configuration` | **Yes** | structure | -- | Shorthand: `MFADelete=Enabled\|Disabled,Status=Enabled\|Suspended` |
| `--mfa` | No | string | None | MFA device serial and token (for MFA Delete) |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.6 `get-bucket-versioning`

Returns the versioning state of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-versioning \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "Status": "Enabled|Suspended",
    "MFADelete": "Enabled|Disabled"
}
```

---

### 3.7 `put-bucket-lifecycle-configuration`

Sets lifecycle configuration rules for a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-lifecycle-configuration \
    --bucket <value> \
    --lifecycle-configuration <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--lifecycle-configuration` | **Yes** | structure | -- | JSON lifecycle rules. Supports `file://` syntax |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Lifecycle Configuration Structure:**
```json
{
    "Rules": [
        {
            "ID": "string",
            "Filter": {
                "Prefix": "string",
                "Tag": {"Key": "string", "Value": "string"},
                "And": {
                    "Prefix": "string",
                    "Tags": [{"Key": "string", "Value": "string"}]
                }
            },
            "Status": "Enabled|Disabled",
            "Transitions": [
                {
                    "Days": integer,
                    "Date": "timestamp",
                    "StorageClass": "GLACIER|STANDARD_IA|ONEZONE_IA|INTELLIGENT_TIERING|DEEP_ARCHIVE|GLACIER_IR"
                }
            ],
            "Expiration": {
                "Days": integer,
                "Date": "timestamp",
                "ExpiredObjectDeleteMarker": true|false
            },
            "NoncurrentVersionTransitions": [
                {
                    "NoncurrentDays": integer,
                    "StorageClass": "string",
                    "NewerNoncurrentVersions": integer
                }
            ],
            "NoncurrentVersionExpiration": {
                "NoncurrentDays": integer,
                "NewerNoncurrentVersions": integer
            },
            "AbortIncompleteMultipartUpload": {
                "DaysAfterInitiation": integer
            }
        }
    ]
}
```

**Output:** None on success.

---

### 3.8 `get-bucket-lifecycle-configuration`

Returns the lifecycle configuration for a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-lifecycle-configuration \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "Rules": [
        {
            "Expiration": {
                "Date": "timestamp",
                "Days": integer,
                "ExpiredObjectDeleteMarker": true|false
            },
            "ID": "string",
            "Prefix": "string",
            "Filter": {
                "Prefix": "string",
                "Tag": {"Key": "string", "Value": "string"},
                "ObjectSizeGreaterThan": long,
                "ObjectSizeLessThan": long,
                "And": {}
            },
            "Status": "Enabled|Disabled",
            "Transitions": [
                {
                    "Date": "timestamp",
                    "Days": integer,
                    "StorageClass": "string"
                }
            ],
            "NoncurrentVersionTransitions": [
                {
                    "NoncurrentDays": integer,
                    "StorageClass": "string",
                    "NewerNoncurrentVersions": integer
                }
            ],
            "NoncurrentVersionExpiration": {
                "NoncurrentDays": integer,
                "NewerNoncurrentVersions": integer
            },
            "AbortIncompleteMultipartUpload": {
                "DaysAfterInitiation": integer
            }
        }
    ]
}
```

---

### 3.9 `delete-bucket-lifecycle`

Deletes the lifecycle configuration from a bucket.

**Synopsis:**
```bash
aws s3api delete-bucket-lifecycle \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.10 `put-bucket-encryption`

Sets default server-side encryption for a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-encryption \
    --bucket <value> \
    --server-side-encryption-configuration <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--server-side-encryption-configuration` | **Yes** | structure | -- | Encryption configuration. Supports `file://` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Encryption Configuration Structure:**
```json
{
    "Rules": [
        {
            "ApplyServerSideEncryptionByDefault": {
                "SSEAlgorithm": "AES256|aws:kms|aws:kms:dsse",
                "KMSMasterKeyID": "string"
            },
            "BucketKeyEnabled": true|false
        }
    ]
}
```

**Output:** None on success.

---

### 3.11 `get-bucket-encryption`

Returns the default encryption configuration of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-encryption \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "ServerSideEncryptionConfiguration": {
        "Rules": [
            {
                "ApplyServerSideEncryptionByDefault": {
                    "SSEAlgorithm": "AES256|aws:kms|aws:kms:dsse",
                    "KMSMasterKeyID": "string"
                },
                "BucketKeyEnabled": true|false
            }
        ]
    }
}
```

---

### 3.12 `delete-bucket-encryption`

Resets the default encryption for a bucket to Amazon S3 managed keys (SSE-S3).

**Synopsis:**
```bash
aws s3api delete-bucket-encryption \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.13 `put-bucket-logging`

Sets the logging configuration for a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-logging \
    --bucket <value> \
    --bucket-logging-status <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--bucket-logging-status` | **Yes** | structure | -- | Logging configuration. Supports `file://` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Logging Configuration Structure:**
```json
{
    "LoggingEnabled": {
        "TargetBucket": "string",
        "TargetPrefix": "string",
        "TargetGrants": [
            {
                "Grantee": {
                    "Type": "CanonicalUser|AmazonCustomerByEmail|Group",
                    "ID": "string",
                    "EmailAddress": "string",
                    "URI": "string"
                },
                "Permission": "FULL_CONTROL|READ|WRITE"
            }
        ]
    }
}
```

**Output:** None on success.

---

### 3.14 `get-bucket-logging`

Returns the logging configuration of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-logging \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "LoggingEnabled": {
        "TargetBucket": "string",
        "TargetPrefix": "string",
        "TargetGrants": [
            {
                "Grantee": {
                    "Type": "CanonicalUser|AmazonCustomerByEmail|Group",
                    "ID": "string",
                    "EmailAddress": "string",
                    "URI": "string"
                },
                "Permission": "FULL_CONTROL|READ|WRITE"
            }
        ]
    }
}
```

---

### 3.15 `put-bucket-cors`

Sets the CORS configuration for a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-cors \
    --bucket <value> \
    --cors-configuration <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--cors-configuration` | **Yes** | structure | -- | CORS rules. Supports `file://` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**CORS Configuration Structure:**
```json
{
    "CORSRules": [
        {
            "AllowedHeaders": ["string"],
            "AllowedMethods": ["GET|PUT|POST|DELETE|HEAD"],
            "AllowedOrigins": ["string"],
            "ExposeHeaders": ["string"],
            "MaxAgeSeconds": integer,
            "ID": "string"
        }
    ]
}
```

**Output:** None on success.

---

### 3.16 `get-bucket-cors`

Returns the CORS configuration of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-cors \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "CORSRules": [
        {
            "ID": "string",
            "AllowedHeaders": ["string"],
            "AllowedMethods": ["string"],
            "AllowedOrigins": ["string"],
            "ExposeHeaders": ["string"],
            "MaxAgeSeconds": integer
        }
    ]
}
```

---

### 3.17 `delete-bucket-cors`

Deletes the CORS configuration from a bucket.

**Synopsis:**
```bash
aws s3api delete-bucket-cors \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.18 `put-bucket-website`

Sets the website configuration for a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-website \
    --bucket <value> \
    --website-configuration <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--website-configuration` | **Yes** | structure | -- | Website configuration. Supports `file://` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Website Configuration Structure:**
```json
{
    "ErrorDocument": {
        "Key": "string"
    },
    "IndexDocument": {
        "Suffix": "string"
    },
    "RedirectAllRequestsTo": {
        "HostName": "string",
        "Protocol": "http|https"
    },
    "RoutingRules": [
        {
            "Condition": {
                "HttpErrorCodeReturnedEquals": "string",
                "KeyPrefixEquals": "string"
            },
            "Redirect": {
                "HostName": "string",
                "HttpRedirectCode": "string",
                "Protocol": "http|https",
                "ReplaceKeyPrefixWith": "string",
                "ReplaceKeyWith": "string"
            }
        }
    ]
}
```

**Output:** None on success.

---

### 3.19 `get-bucket-website`

Returns the website configuration of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-website \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "RedirectAllRequestsTo": {
        "HostName": "string",
        "Protocol": "http|https"
    },
    "IndexDocument": {
        "Suffix": "string"
    },
    "ErrorDocument": {
        "Key": "string"
    },
    "RoutingRules": [
        {
            "Condition": {
                "HttpErrorCodeReturnedEquals": "string",
                "KeyPrefixEquals": "string"
            },
            "Redirect": {
                "HostName": "string",
                "HttpRedirectCode": "string",
                "Protocol": "http|https",
                "ReplaceKeyPrefixWith": "string",
                "ReplaceKeyWith": "string"
            }
        }
    ]
}
```

---

### 3.20 `delete-bucket-website`

Removes the website configuration from a bucket.

**Synopsis:**
```bash
aws s3api delete-bucket-website \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.21 `put-bucket-acl`

Sets the ACL for a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-acl \
    --bucket <value> \
    [--acl <value>] \
    [--access-control-policy <value>] \
    [--grant-full-control <value>] \
    [--grant-read <value>] \
    [--grant-read-acp <value>] \
    [--grant-write <value>] \
    [--grant-write-acp <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--acl` | No | string | None | `private`, `public-read`, `public-read-write`, `authenticated-read` |
| `--access-control-policy` | No | structure | None | Full ACL document. Supports `file://` |
| `--grant-full-control` | No | string | None | Grant grantee full control |
| `--grant-read` | No | string | None | Grant grantee list permission |
| `--grant-read-acp` | No | string | None | Grant grantee read ACL |
| `--grant-write` | No | string | None | Grant grantee create/delete |
| `--grant-write-acp` | No | string | None | Grant grantee write ACL |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.22 `get-bucket-acl`

Returns the ACL of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-acl \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "Owner": {
        "DisplayName": "string",
        "ID": "string"
    },
    "Grants": [
        {
            "Grantee": {
                "DisplayName": "string",
                "EmailAddress": "string",
                "ID": "string",
                "Type": "CanonicalUser|AmazonCustomerByEmail|Group",
                "URI": "string"
            },
            "Permission": "FULL_CONTROL|WRITE|WRITE_ACP|READ|READ_ACP"
        }
    ]
}
```

---

### 3.23 `put-bucket-replication`

Sets replication configuration for a bucket (requires versioning enabled).

**Synopsis:**
```bash
aws s3api put-bucket-replication \
    --bucket <value> \
    --replication-configuration <value> \
    [--token <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--replication-configuration` | **Yes** | structure | -- | Replication config. Supports `file://` |
| `--token` | No | string | None | Token for object lock-enabled bucket |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Replication Configuration Structure:**
```json
{
    "Role": "string",
    "Rules": [
        {
            "ID": "string",
            "Priority": integer,
            "Filter": {
                "Prefix": "string",
                "Tag": {"Key": "string", "Value": "string"},
                "And": {
                    "Prefix": "string",
                    "Tags": [{"Key": "string", "Value": "string"}]
                }
            },
            "Status": "Enabled|Disabled",
            "Destination": {
                "Bucket": "string",
                "Account": "string",
                "StorageClass": "string",
                "AccessControlTranslation": {
                    "Owner": "Destination"
                },
                "EncryptionConfiguration": {
                    "ReplicaKmsKeyID": "string"
                },
                "ReplicationTime": {
                    "Status": "Enabled|Disabled",
                    "Time": {"Minutes": integer}
                },
                "Metrics": {
                    "Status": "Enabled|Disabled",
                    "EventThreshold": {"Minutes": integer}
                }
            },
            "DeleteMarkerReplication": {
                "Status": "Enabled|Disabled"
            }
        }
    ]
}
```

**Output:** None on success.

---

### 3.24 `get-bucket-replication`

Returns the replication configuration of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-replication \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "ReplicationConfiguration": {
        "Role": "string",
        "Rules": [
            {
                "ID": "string",
                "Priority": integer,
                "Prefix": "string",
                "Filter": {},
                "Status": "Enabled|Disabled",
                "Destination": {
                    "Bucket": "string",
                    "Account": "string",
                    "StorageClass": "string"
                },
                "DeleteMarkerReplication": {
                    "Status": "Enabled|Disabled"
                }
            }
        ]
    }
}
```

---

### 3.25 `delete-bucket-replication`

Deletes the replication configuration from a bucket.

**Synopsis:**
```bash
aws s3api delete-bucket-replication \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.26 `put-bucket-tagging`

Sets the tag set for a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-tagging \
    --bucket <value> \
    --tagging <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--tagging` | **Yes** | structure | -- | `TagSet=[{Key=string,Value=string}]`. Supports `file://` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.27 `get-bucket-tagging`

Returns the tag set of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-tagging \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "TagSet": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 3.28 `delete-bucket-tagging`

Deletes the tag set from a bucket.

**Synopsis:**
```bash
aws s3api delete-bucket-tagging \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.29 `put-bucket-notification-configuration`

Enables notifications of specified events for a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-notification-configuration \
    --bucket <value> \
    --notification-configuration <value> \
    [--expected-bucket-owner <value>] \
    [--skip-destination-validation | --no-skip-destination-validation]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--notification-configuration` | **Yes** | structure | -- | Notification config. Supports `file://` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |
| `--skip-destination-validation` | No | boolean | false | Skip destination validation |

**Notification Configuration Structure:**
```json
{
    "TopicConfigurations": [
        {
            "Id": "string",
            "TopicArn": "string",
            "Events": ["s3:ObjectCreated:*", "s3:ObjectRemoved:*"],
            "Filter": {
                "Key": {
                    "FilterRules": [
                        {"Name": "prefix|suffix", "Value": "string"}
                    ]
                }
            }
        }
    ],
    "QueueConfigurations": [
        {
            "Id": "string",
            "QueueArn": "string",
            "Events": ["string"],
            "Filter": {}
        }
    ],
    "LambdaFunctionConfigurations": [
        {
            "Id": "string",
            "LambdaFunctionArn": "string",
            "Events": ["string"],
            "Filter": {}
        }
    ],
    "EventBridgeConfiguration": {}
}
```

**Output:** None on success.

---

### 3.30 `get-bucket-notification-configuration`

Returns the notification configuration of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-notification-configuration \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "TopicConfigurations": [
        {
            "Id": "string",
            "TopicArn": "string",
            "Events": ["string"],
            "Filter": {
                "Key": {
                    "FilterRules": [
                        {"Name": "prefix|suffix", "Value": "string"}
                    ]
                }
            }
        }
    ],
    "QueueConfigurations": [],
    "LambdaFunctionConfigurations": [],
    "EventBridgeConfiguration": {}
}
```

---

### 3.31 `put-public-access-block`

Sets the PublicAccessBlock configuration for a bucket.

**Synopsis:**
```bash
aws s3api put-public-access-block \
    --bucket <value> \
    --public-access-block-configuration <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--public-access-block-configuration` | **Yes** | structure | -- | Public access block settings |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Shorthand:**
```
BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true
```

**Output:** None on success.

---

### 3.32 `get-public-access-block`

Returns the PublicAccessBlock configuration for a bucket.

**Synopsis:**
```bash
aws s3api get-public-access-block \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "PublicAccessBlockConfiguration": {
        "BlockPublicAcls": true|false,
        "IgnorePublicAcls": true|false,
        "BlockPublicPolicy": true|false,
        "RestrictPublicBuckets": true|false
    }
}
```

---

### 3.33 `delete-public-access-block`

Removes the PublicAccessBlock configuration for a bucket.

**Synopsis:**
```bash
aws s3api delete-public-access-block \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.34 `put-bucket-accelerate-configuration`

Sets the transfer acceleration state of a bucket.

**Synopsis:**
```bash
aws s3api put-bucket-accelerate-configuration \
    --bucket <value> \
    --accelerate-configuration <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--accelerate-configuration` | **Yes** | structure | -- | Shorthand: `Status=Enabled\|Suspended` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output:** None on success.

---

### 3.35 `get-bucket-accelerate-configuration`

Returns the transfer acceleration state of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-accelerate-configuration \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "Status": "Enabled|Suspended",
    "RequestCharged": "requester"
}
```

---

