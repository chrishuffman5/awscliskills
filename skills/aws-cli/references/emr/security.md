# Security

### 5.1 `create-security-configuration`

Creates a security configuration for encryption, authentication, and authorization settings.

**Synopsis:**
```bash
aws emr create-security-configuration \
    --name <value> \
    --security-configuration <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Security configuration name |
| `--security-configuration` | **Yes** | string | -- | JSON security configuration (inline or `file://`) |

**Security Configuration JSON (example):**
```json
{
    "EncryptionConfiguration": {
        "EnableInTransitEncryption": true,
        "EnableAtRestEncryption": true,
        "InTransitEncryptionConfiguration": {
            "TLSCertificateConfiguration": {
                "CertificateProviderType": "PEM",
                "S3Object": "s3://bucket/certs.zip"
            }
        },
        "AtRestEncryptionConfiguration": {
            "S3EncryptionConfiguration": {
                "EncryptionMode": "SSE-S3|SSE-KMS|CSE-KMS|CSE-Custom",
                "AwsKmsKey": "arn:aws:kms:..."
            },
            "LocalDiskEncryptionConfiguration": {
                "EncryptionKeyProviderType": "AwsKms",
                "AwsKmsKey": "arn:aws:kms:..."
            }
        }
    },
    "AuthenticationConfiguration": {
        "KerberosConfiguration": {
            "Provider": "ClusterDedicatedKdc",
            "ClusterDedicatedKdcConfiguration": {
                "TicketLifetimeInHours": 24
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "Name": "string",
    "CreationDateTime": "timestamp"
}
```

---

### 5.2 `delete-security-configuration`

Deletes a security configuration.

**Synopsis:**
```bash
aws emr delete-security-configuration \
    --name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Security configuration to delete |

No output on success.

---

### 5.3 `describe-security-configuration`

Describes a security configuration.

**Synopsis:**
```bash
aws emr describe-security-configuration \
    --name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Security configuration name |

**Output Schema:**
```json
{
    "Name": "string",
    "SecurityConfiguration": "string (JSON)",
    "CreationDateTime": "timestamp"
}
```

---

### 5.4 `list-security-configurations`

Lists security configurations. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-security-configurations \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "SecurityConfigurations": [
        {
            "Name": "string",
            "CreationDateTime": "timestamp"
        }
    ],
    "Marker": "string"
}
```

---

### 5.5 `put-block-public-access-configuration`

Sets the block public access configuration for the account in the current region.

**Synopsis:**
```bash
aws emr put-block-public-access-configuration \
    --block-public-access-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--block-public-access-configuration` | **Yes** | structure | -- | Configuration (JSON) |

**Configuration JSON:**
```json
{
    "BlockPublicSecurityGroupRules": true,
    "PermittedPublicSecurityGroupRuleRanges": [
        {
            "MinRange": 22,
            "MaxRange": 22
        }
    ]
}
```

No output on success.

---

### 5.6 `get-block-public-access-configuration`

Gets the block public access configuration for the account in the current region.

**Synopsis:**
```bash
aws emr get-block-public-access-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

No parameters required.

**Output Schema:**
```json
{
    "BlockPublicAccessConfiguration": {
        "BlockPublicSecurityGroupRules": "boolean",
        "PermittedPublicSecurityGroupRuleRanges": [
            {
                "MinRange": "integer",
                "MaxRange": "integer"
            }
        ]
    },
    "BlockPublicAccessConfigurationMetadata": {
        "CreationDateTime": "timestamp",
        "CreatedByArn": "string"
    }
}
```

---

### 5.7 `delete-block-public-access-configuration`

Deletes the block public access configuration (reverts to default).

**Synopsis:**
```bash
aws emr delete-block-public-access-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

No parameters required. No output on success.
