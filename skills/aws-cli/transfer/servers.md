# Servers

### 1.1 `create-server`

Creates a Transfer Family server supporting SFTP, FTPS, FTP, and/or AS2 protocols.

**Synopsis:**
```bash
aws transfer create-server \
    [--certificate <value>] \
    [--domain <value>] \
    [--endpoint-details <value>] \
    [--endpoint-type <value>] \
    [--host-key <value>] \
    [--identity-provider-details <value>] \
    [--identity-provider-type <value>] \
    [--logging-role <value>] \
    [--post-authentication-login-banner <value>] \
    [--pre-authentication-login-banner <value>] \
    [--protocols <value>] \
    [--protocol-details <value>] \
    [--security-policy-name <value>] \
    [--tags <value>] \
    [--workflow-details <value>] \
    [--structured-log-destinations <value>] \
    [--s3-storage-options <value>] \
    [--ip-address-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate` | No | string | None | ACM certificate ARN (required for FTPS) |
| `--domain` | No | string | `S3` | Storage domain: `S3` or `EFS` |
| `--endpoint-details` | No | structure | None | VPC endpoint configuration |
| `--endpoint-type` | No | string | `PUBLIC` | Endpoint type: `PUBLIC` or `VPC` |
| `--host-key` | No | string | None | RSA/ECDSA/ED25519 private key for SFTP |
| `--identity-provider-details` | No | structure | None | Identity provider configuration |
| `--identity-provider-type` | No | string | `SERVICE_MANAGED` | Auth mode: `SERVICE_MANAGED`, `AWS_DIRECTORY_SERVICE`, `API_GATEWAY`, `AWS_LAMBDA` |
| `--logging-role` | No | string | None | IAM role ARN for CloudWatch logging |
| `--post-authentication-login-banner` | No | string | None | Banner after auth (max 4096 chars) |
| `--pre-authentication-login-banner` | No | string | None | Banner before auth (max 4096 chars) |
| `--protocols` | No | list(string) | `["SFTP"]` | Protocols: `SFTP`, `FTPS`, `FTP`, `AS2` |
| `--protocol-details` | No | structure | None | Protocol settings (PassiveIp, TLS, SetStat) |
| `--security-policy-name` | No | string | None | Security policy name |
| `--tags` | No | list | None | Tags (max 50) |
| `--workflow-details` | No | structure | None | OnUpload/OnPartialUpload workflow config |
| `--structured-log-destinations` | No | list(string) | None | CloudWatch log group ARN |
| `--s3-storage-options` | No | structure | None | S3 directory listing optimization |
| `--ip-address-type` | No | string | `IPV4` | `IPV4` or `DUALSTACK` |

**Endpoint Details Structure (JSON):**
```json
{
    "AddressAllocationIds": ["string"],
    "SubnetIds": ["string"],
    "VpcEndpointId": "string",
    "VpcId": "string",
    "SecurityGroupIds": ["string"]
}
```

**Workflow Details Structure (JSON):**
```json
{
    "OnUpload": [{"WorkflowId": "string", "ExecutionRole": "string"}],
    "OnPartialUpload": [{"WorkflowId": "string", "ExecutionRole": "string"}]
}
```

**Output Schema:**
```json
{
    "ServerId": "string"
}
```

---

### 1.2 `delete-server`

Deletes a server. All users, host keys, and other resources must be removed first.

**Synopsis:**
```bash
aws transfer delete-server \
    --server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID (format: `s-[0-9a-f]{17}`) |

**Output:** None on success.

---

### 1.3 `describe-server`

Gets details about a server.

**Synopsis:**
```bash
aws transfer describe-server \
    --server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |

**Output Schema:**
```json
{
    "Server": {
        "Arn": "string",
        "Certificate": "string",
        "ProtocolDetails": {
            "PassiveIp": "string",
            "TlsSessionResumptionMode": "DISABLED|ENABLED|ENFORCED",
            "SetStatOption": "DEFAULT|ENABLE_NO_OP",
            "As2Transports": ["HTTP"]
        },
        "Domain": "S3|EFS",
        "EndpointDetails": {
            "AddressAllocationIds": ["string"],
            "SubnetIds": ["string"],
            "VpcEndpointId": "string",
            "VpcId": "string",
            "SecurityGroupIds": ["string"]
        },
        "EndpointType": "PUBLIC|VPC",
        "HostKeyFingerprint": "string",
        "IdentityProviderDetails": {
            "Url": "string",
            "InvocationRole": "string",
            "DirectoryId": "string",
            "Function": "string",
            "SftpAuthenticationMethods": "PASSWORD|PUBLIC_KEY|PUBLIC_KEY_OR_PASSWORD|PUBLIC_KEY_AND_PASSWORD"
        },
        "IdentityProviderType": "SERVICE_MANAGED|API_GATEWAY|AWS_DIRECTORY_SERVICE|AWS_LAMBDA",
        "LoggingRole": "string",
        "PostAuthenticationLoginBanner": "string",
        "PreAuthenticationLoginBanner": "string",
        "Protocols": ["SFTP|FTP|FTPS|AS2"],
        "SecurityPolicyName": "string",
        "ServerId": "string",
        "State": "OFFLINE|ONLINE|STARTING|STOPPING|START_FAILED|STOP_FAILED",
        "Tags": [{"Key": "string", "Value": "string"}],
        "UserCount": "integer",
        "WorkflowDetails": {
            "OnUpload": [{"WorkflowId": "string", "ExecutionRole": "string"}],
            "OnPartialUpload": [{"WorkflowId": "string", "ExecutionRole": "string"}]
        },
        "StructuredLogDestinations": ["string"],
        "S3StorageOptions": {"DirectoryListingOptimization": "ENABLED|DISABLED"},
        "IpAddressType": "IPV4|DUALSTACK"
    }
}
```

---

### 1.4 `list-servers`

Lists all servers. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-servers \
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
    "Servers": [
        {
            "Arn": "string",
            "Domain": "S3|EFS",
            "IdentityProviderType": "string",
            "EndpointType": "string",
            "LoggingRole": "string",
            "ServerId": "string",
            "State": "string",
            "UserCount": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-server`

Updates server configuration. The server must be offline for certain changes (protocols, endpoint type).

**Synopsis:**
```bash
aws transfer update-server \
    --server-id <value> \
    [--certificate <value>] \
    [--protocol-details <value>] \
    [--endpoint-details <value>] \
    [--endpoint-type <value>] \
    [--host-key <value>] \
    [--identity-provider-details <value>] \
    [--logging-role <value>] \
    [--post-authentication-login-banner <value>] \
    [--pre-authentication-login-banner <value>] \
    [--protocols <value>] \
    [--security-policy-name <value>] \
    [--workflow-details <value>] \
    [--structured-log-destinations <value>] \
    [--s3-storage-options <value>] \
    [--ip-address-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-server` plus `--server-id` (required).

**Output Schema:**
```json
{
    "ServerId": "string"
}
```

---

### 1.6 `start-server`

Starts a stopped server. Changes state from OFFLINE to ONLINE.

**Synopsis:**
```bash
aws transfer start-server \
    --server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |

**Output:** None on success.

---

### 1.7 `stop-server`

Stops a running server. Changes state from ONLINE to OFFLINE.

**Synopsis:**
```bash
aws transfer stop-server \
    --server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |

**Output:** None on success.

---

### 1.8 `describe-security-policy`

Gets details about a named security policy (supported TLS versions and algorithms).

**Synopsis:**
```bash
aws transfer describe-security-policy \
    --security-policy-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-policy-name` | **Yes** | string | -- | Security policy name |

**Output Schema:**
```json
{
    "SecurityPolicy": {
        "Fips": "boolean",
        "SecurityPolicyName": "string",
        "SshCiphers": ["string"],
        "SshKexs": ["string"],
        "SshMacs": ["string"],
        "TlsCiphers": ["string"],
        "SshHostKeyAlgorithms": ["string"],
        "Type": "SERVER|CONNECTOR",
        "Protocols": ["SFTP|FTPS"]
    }
}
```

---

### 1.9 `list-security-policies`

Lists available security policies. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-security-policies \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "SecurityPolicyNames": ["string"],
    "NextToken": "string"
}
```

---

### 1.10 `test-identity-provider`

Tests identity provider settings for a server by simulating a user login.

**Synopsis:**
```bash
aws transfer test-identity-provider \
    --server-id <value> \
    --user-name <value> \
    [--server-protocol <value>] \
    [--source-ip <value>] \
    [--user-password <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |
| `--user-name` | **Yes** | string | -- | Username to test |
| `--server-protocol` | No | string | None | Protocol: `SFTP`, `FTP`, `FTPS` |
| `--source-ip` | No | string | None | Source IP to simulate |
| `--user-password` | No | string | None | Password to test |

**Output Schema:**
```json
{
    "Response": "string",
    "StatusCode": "integer",
    "Message": "string",
    "Url": "string"
}
```
