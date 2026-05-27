# TLS Inspection

### 4.1 `create-tls-inspection-configuration`

Creates a TLS inspection configuration for decrypting and inspecting TLS-encrypted traffic.

**Synopsis:**
```bash
aws network-firewall create-tls-inspection-configuration \
    --tls-inspection-configuration-name <value> \
    --tls-inspection-configuration <value> \
    [--description <value>] \
    [--tags <value>] \
    [--encryption-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tls-inspection-configuration-name` | **Yes** | string | -- | Name (1-128 chars, alphanumeric and hyphens) |
| `--tls-inspection-configuration` | **Yes** | structure | -- | TLS inspection configuration object |
| `--description` | No | string | None | Description (max 512 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--encryption-configuration` | No | structure | None | KMS encryption config |

**TLS Inspection Configuration Structure:**
```json
{
    "ServerCertificateConfigurations": [
        {
            "ServerCertificates": [
                {
                    "ResourceArn": "string"
                }
            ],
            "Scopes": [
                {
                    "Sources": [{"AddressDefinition": "CIDR"}],
                    "Destinations": [{"AddressDefinition": "CIDR"}],
                    "SourcePorts": [{"FromPort": "integer", "ToPort": "integer"}],
                    "DestinationPorts": [{"FromPort": "integer", "ToPort": "integer"}],
                    "Protocols": ["integer"]
                }
            ],
            "CertificateAuthorityArn": "string",
            "CheckCertificateRevocationStatus": {
                "RevokedStatusAction": "PASS|DROP|REJECT",
                "UnknownStatusAction": "PASS|DROP|REJECT"
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "TLSInspectionConfigurationResponse": {
        "TLSInspectionConfigurationArn": "string",
        "TLSInspectionConfigurationName": "string",
        "TLSInspectionConfigurationId": "string",
        "TLSInspectionConfigurationStatus": "ACTIVE|DELETING|ERROR",
        "Description": "string",
        "Tags": [],
        "LastModifiedTime": "timestamp",
        "NumberOfAssociations": "integer",
        "EncryptionConfiguration": {},
        "Certificates": [
            {
                "CertificateArn": "string",
                "CertificateSerial": "string",
                "Status": "string",
                "StatusMessage": "string"
            }
        ],
        "CertificateAuthority": {
            "CertificateArn": "string",
            "CertificateSerial": "string",
            "Status": "string",
            "StatusMessage": "string"
        }
    }
}
```

---

### 4.2 `delete-tls-inspection-configuration`

Deletes the specified TLS inspection configuration.

**Synopsis:**
```bash
aws network-firewall delete-tls-inspection-configuration \
    [--tls-inspection-configuration-name <value>] \
    [--tls-inspection-configuration-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tls-inspection-configuration-name` | No* | string | None | Configuration name |
| `--tls-inspection-configuration-arn` | No* | string | None | Configuration ARN |

*Must specify either name or ARN.

**Output Schema:**
```json
{
    "TLSInspectionConfigurationResponse": {
        "TLSInspectionConfigurationArn": "string",
        "TLSInspectionConfigurationName": "string",
        "TLSInspectionConfigurationId": "string",
        "TLSInspectionConfigurationStatus": "DELETING"
    }
}
```

---

### 4.3 `describe-tls-inspection-configuration`

Returns the full details of the specified TLS inspection configuration.

**Synopsis:**
```bash
aws network-firewall describe-tls-inspection-configuration \
    [--tls-inspection-configuration-name <value>] \
    [--tls-inspection-configuration-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tls-inspection-configuration-name` | No* | string | None | Configuration name |
| `--tls-inspection-configuration-arn` | No* | string | None | Configuration ARN |

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "TLSInspectionConfiguration": {
        "ServerCertificateConfigurations": []
    },
    "TLSInspectionConfigurationResponse": {
        "TLSInspectionConfigurationArn": "string",
        "TLSInspectionConfigurationName": "string",
        "TLSInspectionConfigurationId": "string",
        "TLSInspectionConfigurationStatus": "ACTIVE|DELETING|ERROR",
        "Description": "string",
        "Tags": [],
        "LastModifiedTime": "timestamp",
        "NumberOfAssociations": "integer",
        "EncryptionConfiguration": {},
        "Certificates": [],
        "CertificateAuthority": {}
    }
}
```

---

### 4.4 `list-tls-inspection-configurations`

Lists all TLS inspection configurations. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-tls-inspection-configurations \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TLSInspectionConfigurations": [
        {
            "Name": "string",
            "Arn": "string",
            "ResourceArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-tls-inspection-configuration`

Updates the specified TLS inspection configuration.

**Synopsis:**
```bash
aws network-firewall update-tls-inspection-configuration \
    --update-token <value> \
    [--tls-inspection-configuration-name <value>] \
    [--tls-inspection-configuration-arn <value>] \
    --tls-inspection-configuration <value> \
    [--description <value>] \
    [--encryption-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--update-token` | **Yes** | string | -- | Token from describe for optimistic locking |
| `--tls-inspection-configuration-name` | No* | string | None | Configuration name |
| `--tls-inspection-configuration-arn` | No* | string | None | Configuration ARN |
| `--tls-inspection-configuration` | **Yes** | structure | -- | Updated configuration |
| `--description` | No | string | None | Updated description |
| `--encryption-configuration` | No | structure | None | KMS encryption config |

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "TLSInspectionConfigurationResponse": {
        "TLSInspectionConfigurationArn": "string",
        "TLSInspectionConfigurationName": "string",
        "TLSInspectionConfigurationId": "string",
        "TLSInspectionConfigurationStatus": "ACTIVE|DELETING|ERROR",
        "LastModifiedTime": "timestamp"
    }
}
```
