# HSM (Hardware Security Module)

### 10.1 `create-hsm-client-certificate`

Creates an HSM client certificate that a cluster uses to connect to an HSM.

**Synopsis:**
```bash
aws redshift create-hsm-client-certificate \
    --hsm-client-certificate-identifier <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hsm-client-certificate-identifier` | **Yes** | string | -- | Certificate identifier |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "HsmClientCertificate": {
        "HsmClientCertificateIdentifier": "string",
        "HsmClientCertificatePublicKey": "string",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 10.2 `delete-hsm-client-certificate`

Deletes an HSM client certificate.

**Synopsis:**
```bash
aws redshift delete-hsm-client-certificate \
    --hsm-client-certificate-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hsm-client-certificate-identifier` | **Yes** | string | -- | Certificate to delete |

No output on success.

---

### 10.3 `describe-hsm-client-certificates`

Returns HSM client certificate information. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-hsm-client-certificates \
    [--hsm-client-certificate-identifier <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hsm-client-certificate-identifier` | No | string | -- | Specific certificate |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "HsmClientCertificates": [
        {
            "HsmClientCertificateIdentifier": "string",
            "HsmClientCertificatePublicKey": "string",
            "Tags": [{"Key": "string", "Value": "string"}]
        }
    ],
    "Marker": "string"
}
```

---

### 10.4 `create-hsm-configuration`

Creates an HSM configuration that contains the information needed for a cluster to store and use encryption keys in an HSM.

**Synopsis:**
```bash
aws redshift create-hsm-configuration \
    --hsm-configuration-identifier <value> \
    --description <value> \
    --hsm-ip-address <value> \
    --hsm-partition-name <value> \
    --hsm-partition-password <value> \
    --hsm-server-public-certificate <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hsm-configuration-identifier` | **Yes** | string | -- | Configuration identifier |
| `--description` | **Yes** | string | -- | Description |
| `--hsm-ip-address` | **Yes** | string | -- | HSM IP address |
| `--hsm-partition-name` | **Yes** | string | -- | HSM partition name |
| `--hsm-partition-password` | **Yes** | string | -- | HSM partition password |
| `--hsm-server-public-certificate` | **Yes** | string | -- | HSM server public certificate |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "HsmConfiguration": {
        "HsmConfigurationIdentifier": "string",
        "Description": "string",
        "HsmIpAddress": "string",
        "HsmPartitionName": "string",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 10.5 `delete-hsm-configuration`

Deletes an HSM configuration.

**Synopsis:**
```bash
aws redshift delete-hsm-configuration \
    --hsm-configuration-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hsm-configuration-identifier` | **Yes** | string | -- | Configuration to delete |

No output on success.

---

### 10.6 `describe-hsm-configurations`

Returns HSM configuration information. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-hsm-configurations \
    [--hsm-configuration-identifier <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hsm-configuration-identifier` | No | string | -- | Specific configuration |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "HsmConfigurations": [
        {
            "HsmConfigurationIdentifier": "string",
            "Description": "string",
            "HsmIpAddress": "string",
            "HsmPartitionName": "string",
            "Tags": [{"Key": "string", "Value": "string"}]
        }
    ],
    "Marker": "string"
}
```
