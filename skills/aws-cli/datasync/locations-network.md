# Locations (Network)

### 5.1 `create-location-nfs`

Creates a transfer location for an NFS file server.

**Synopsis:**
```bash
aws datasync create-location-nfs \
    --subdirectory <value> \
    --server-hostname <value> \
    --on-prem-config <value> \
    [--mount-options <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subdirectory` | **Yes** | string | -- | Export path on the NFS server (max 4096 chars) |
| `--server-hostname` | **Yes** | string | -- | NFS server hostname or IP (max 255 chars) |
| `--on-prem-config` | **Yes** | structure | -- | Agent ARNs for NFS access |
| `--mount-options` | No | structure | None | NFS mount version |
| `--tags` | No | list | None | Tags (max 50) |

**On-Prem Config Structure (shorthand):**
```
AgentArns=string,string
```

**Mount Options Structure (shorthand):**
```
Version=AUTOMATIC|NFS3|NFS4_0|NFS4_1
```

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 5.2 `create-location-smb`

Creates a transfer location for an SMB file server.

**Synopsis:**
```bash
aws datasync create-location-smb \
    --subdirectory <value> \
    --server-hostname <value> \
    --agent-arns <value> \
    [--user <value>] \
    [--domain <value>] \
    [--password <value>] \
    [--authentication-type <value>] \
    [--mount-options <value>] \
    [--tags <value>] \
    [--cmk-secret-config <value>] \
    [--custom-secret-config <value>] \
    [--dns-ip-addresses <value>] \
    [--kerberos-principal <value>] \
    [--kerberos-keytab <value>] \
    [--kerberos-krb5-conf <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subdirectory` | **Yes** | string | -- | SMB share name and optional subdirectory (max 4096 chars) |
| `--server-hostname` | **Yes** | string | -- | SMB server hostname or IP (max 255 chars) |
| `--agent-arns` | **Yes** | list(string) | -- | Agent ARNs for SMB access (max 8) |
| `--user` | No | string | None | NTLM user with mount permissions (max 104 chars) |
| `--domain` | No | string | None | Windows domain name (max 253 chars) |
| `--password` | No | string | None | User password (max 104 chars) |
| `--authentication-type` | No | string | `NTLM` | `NTLM` or `KERBEROS` |
| `--mount-options` | No | structure | None | SMB protocol version |
| `--tags` | No | list | None | Tags (max 50) |
| `--cmk-secret-config` | No | structure | None | DataSync-managed secret with customer-managed KMS key |
| `--custom-secret-config` | No | structure | None | Customer-managed Secrets Manager secret |
| `--dns-ip-addresses` | No | list(string) | None | DNS server IPs (max 2, Kerberos only) |
| `--kerberos-principal` | No | string | None | Kerberos identity (max 256 chars) |
| `--kerberos-keytab` | No | blob | None | Base64-encoded Kerberos keytab (max 65536 bytes) |
| `--kerberos-krb5-conf` | No | blob | None | Base64-encoded Kerberos config (max 131072 bytes) |

**Mount Options Structure (shorthand):**
```
Version=AUTOMATIC|SMB2|SMB3|SMB1|SMB2_0
```

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 5.3 `create-location-hdfs`

Creates a transfer location for a Hadoop Distributed File System (HDFS) cluster.

**Synopsis:**
```bash
aws datasync create-location-hdfs \
    --name-nodes <value> \
    --authentication-type <value> \
    --agent-arns <value> \
    [--subdirectory <value>] \
    [--block-size <value>] \
    [--replication-factor <value>] \
    [--kms-key-provider-uri <value>] \
    [--qop-configuration <value>] \
    [--simple-user <value>] \
    [--kerberos-principal <value>] \
    [--kerberos-keytab <value>] \
    [--kerberos-krb5-conf <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-nodes` | **Yes** | list | -- | NameNode hostname and port (min 1) |
| `--authentication-type` | **Yes** | string | -- | `SIMPLE` or `KERBEROS` |
| `--agent-arns` | **Yes** | list(string) | -- | Agent ARNs (max 8) |
| `--subdirectory` | No | string | `/` | HDFS subdirectory (max 4096 chars) |
| `--block-size` | No | integer | 134217728 | Block size in bytes (1048576-1073741824, multiple of 512) |
| `--replication-factor` | No | integer | 3 | DataNode replication count (1-512) |
| `--kms-key-provider-uri` | No | string | None | HDFS KMS URI |
| `--qop-configuration` | No | structure | None | Quality of Protection settings |
| `--simple-user` | Conditional | string | None | Username for SIMPLE auth (max 256 chars) |
| `--kerberos-principal` | Conditional | string | None | Kerberos principal (max 256 chars) |
| `--kerberos-keytab` | Conditional | blob | None | Kerberos keytab (max 65536 bytes) |
| `--kerberos-krb5-conf` | Conditional | blob | None | Kerberos config (max 131072 bytes) |
| `--tags` | No | list | None | Tags (max 50) |

**NameNode Structure (shorthand):**
```
Hostname=string,Port=integer ...
```

**QoP Configuration Structure (shorthand):**
```
RpcProtection=DISABLED|AUTHENTICATION|INTEGRITY|PRIVACY,DataTransferProtection=DISABLED|AUTHENTICATION|INTEGRITY|PRIVACY
```

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 5.4 `describe-location-nfs`

Gets details about an NFS location.

**Synopsis:**
```bash
aws datasync describe-location-nfs \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the NFS location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "OnPremConfig": {
        "AgentArns": ["string"]
    },
    "MountOptions": {
        "Version": "AUTOMATIC|NFS3|NFS4_0|NFS4_1"
    },
    "CreationTime": "timestamp"
}
```

---

### 5.5 `describe-location-smb`

Gets details about an SMB location.

**Synopsis:**
```bash
aws datasync describe-location-smb \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the SMB location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "AgentArns": ["string"],
    "User": "string",
    "Domain": "string",
    "MountOptions": {
        "Version": "AUTOMATIC|SMB2|SMB3|SMB1|SMB2_0"
    },
    "CreationTime": "timestamp",
    "AuthenticationType": "NTLM|KERBEROS",
    "DnsIpAddresses": ["string"],
    "KerberosPrincipal": "string"
}
```

---

### 5.6 `describe-location-hdfs`

Gets details about an HDFS location.

**Synopsis:**
```bash
aws datasync describe-location-hdfs \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the HDFS location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "NameNodes": [
        {
            "Hostname": "string",
            "Port": "integer"
        }
    ],
    "BlockSize": "integer",
    "ReplicationFactor": "integer",
    "KmsKeyProviderUri": "string",
    "QopConfiguration": {
        "RpcProtection": "DISABLED|AUTHENTICATION|INTEGRITY|PRIVACY",
        "DataTransferProtection": "DISABLED|AUTHENTICATION|INTEGRITY|PRIVACY"
    },
    "AuthenticationType": "SIMPLE|KERBEROS",
    "SimpleUser": "string",
    "KerberosPrincipal": "string",
    "AgentArns": ["string"],
    "CreationTime": "timestamp"
}
```

---

### 5.7 `update-location-nfs`

Updates an NFS location configuration.

**Synopsis:**
```bash
aws datasync update-location-nfs \
    --location-arn <value> \
    [--subdirectory <value>] \
    [--on-prem-config <value>] \
    [--mount-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the NFS location |
| `--subdirectory` | No | string | None | New export path |
| `--on-prem-config` | No | structure | None | New agent config |
| `--mount-options` | No | structure | None | New NFS mount version |

**Output:** None on success.

---

### 5.8 `update-location-smb`

Updates an SMB location configuration.

**Synopsis:**
```bash
aws datasync update-location-smb \
    --location-arn <value> \
    [--subdirectory <value>] \
    [--user <value>] \
    [--domain <value>] \
    [--password <value>] \
    [--agent-arns <value>] \
    [--mount-options <value>] \
    [--authentication-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the SMB location |
| `--subdirectory` | No | string | None | New share name/path |
| `--user` | No | string | None | New user |
| `--domain` | No | string | None | New domain |
| `--password` | No | string | None | New password |
| `--agent-arns` | No | list(string) | None | New agent ARNs |
| `--mount-options` | No | structure | None | New SMB mount version |
| `--authentication-type` | No | string | None | `NTLM` or `KERBEROS` |

**Output:** None on success.

---

### 5.9 `update-location-hdfs`

Updates an HDFS location configuration.

**Synopsis:**
```bash
aws datasync update-location-hdfs \
    --location-arn <value> \
    [--subdirectory <value>] \
    [--name-nodes <value>] \
    [--block-size <value>] \
    [--replication-factor <value>] \
    [--kms-key-provider-uri <value>] \
    [--qop-configuration <value>] \
    [--authentication-type <value>] \
    [--simple-user <value>] \
    [--kerberos-principal <value>] \
    [--kerberos-keytab <value>] \
    [--kerberos-krb5-conf <value>] \
    [--agent-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the HDFS location |
| `--subdirectory` | No | string | None | New subdirectory |
| `--name-nodes` | No | list | None | New NameNode config |
| `--block-size` | No | integer | None | New block size |
| `--replication-factor` | No | integer | None | New replication factor |
| `--kms-key-provider-uri` | No | string | None | New KMS URI |
| `--qop-configuration` | No | structure | None | New QoP settings |
| `--authentication-type` | No | string | None | New auth type |
| `--simple-user` | No | string | None | New simple user |
| `--kerberos-principal` | No | string | None | New Kerberos principal |
| `--kerberos-keytab` | No | blob | None | New keytab |
| `--kerberos-krb5-conf` | No | blob | None | New Kerberos config |
| `--agent-arns` | No | list(string) | None | New agent ARNs |

**Output:** None on success.
