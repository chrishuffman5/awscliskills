# RDS Proxy

### 9.1 `create-db-proxy`

Creates an RDS Proxy.

**Synopsis:**
```bash
aws rds create-db-proxy \
    --db-proxy-name <value> \
    --engine-family <value> \
    --auth <value> \
    --role-arn <value> \
    --vpc-subnet-ids <value> \
    [--vpc-security-group-ids <value>] \
    [--require-tls | --no-require-tls] \
    [--idle-client-timeout <value>] \
    [--debug-logging | --no-debug-logging] \
    [--tags <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--db-proxy-name` | string | Proxy name (1-63 chars, alphanumeric + hyphens) |
| `--engine-family` | string | `MYSQL`, `POSTGRESQL`, `SQLSERVER` |
| `--role-arn` | string | IAM role ARN for Secrets Manager access |
| `--vpc-subnet-ids` | list | VPC subnet IDs |

**Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--auth` | list | None | Auth config: `AuthScheme=SECRETS,SecretArn=string,IAMAuth=DISABLED\|REQUIRED\|ENABLED` |
| `--vpc-security-group-ids` | list | default | Security groups |
| `--require-tls` / `--no-require-tls` | boolean | false | Require TLS |
| `--idle-client-timeout` | integer | 1800 | Idle timeout in seconds |
| `--debug-logging` / `--no-debug-logging` | boolean | false | Debug logging |
| `--tags` | list | None | Tags |

**Output Schema:**
```json
{
    "DBProxy": {
        "DBProxyName": "string",
        "DBProxyArn": "string",
        "Status": "available|modifying|incompatible-network|insufficient-resource-limits|creating|deleting",
        "EngineFamily": "MYSQL|POSTGRESQL|SQLSERVER",
        "VpcId": "string",
        "VpcSecurityGroupIds": ["string"],
        "VpcSubnetIds": ["string"],
        "Auth": [
            {
                "AuthScheme": "SECRETS",
                "SecretArn": "string",
                "IAMAuth": "DISABLED|REQUIRED|ENABLED",
                "ClientPasswordAuthType": "string"
            }
        ],
        "RoleArn": "string",
        "Endpoint": "string",
        "RequireTLS": "boolean",
        "IdleClientTimeout": "integer",
        "DebugLogging": "boolean",
        "CreatedDate": "timestamp",
        "UpdatedDate": "timestamp"
    }
}
```

---

### 9.2 `delete-db-proxy`

Deletes an RDS Proxy.

```bash
aws rds delete-db-proxy \
    --db-proxy-name <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-proxy-name` | **Yes** | string | Proxy name |

**Output Schema:** Same `DBProxy` structure.

---

### 9.3 `describe-db-proxies`

Describes RDS Proxies. **Paginated.**

```bash
aws rds describe-db-proxies \
    [--db-proxy-name <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-proxy-name` | No | string | all | Specific proxy name |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "DBProxies": [
        { "...same DBProxy structure..." }
    ],
    "Marker": "string"
}
```

---

### 9.4 `modify-db-proxy`

Modifies an RDS Proxy.

```bash
aws rds modify-db-proxy \
    --db-proxy-name <value> \
    [--new-db-proxy-name <value>] \
    [--auth <value>] \
    [--require-tls | --no-require-tls] \
    [--idle-client-timeout <value>] \
    [--debug-logging | --no-debug-logging] \
    [--role-arn <value>] \
    [--security-groups <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-proxy-name` | **Yes** | string | -- | Proxy name |
| `--new-db-proxy-name` | No | string | no change | Rename proxy |
| `--auth` | No | list | no change | Auth config |
| `--require-tls` / `--no-require-tls` | No | boolean | no change | TLS requirement |
| `--idle-client-timeout` | No | integer | no change | Idle timeout |
| `--debug-logging` / `--no-debug-logging` | No | boolean | no change | Debug logging |
| `--role-arn` | No | string | no change | IAM role |
| `--security-groups` | No | list | no change | Security groups |

**Output Schema:** Same `DBProxy` structure.

---

### 9.5 `register-db-proxy-targets`

Registers DB instances or clusters as targets for a proxy.

```bash
aws rds register-db-proxy-targets \
    --db-proxy-name <value> \
    [--target-group-name <value>] \
    [--db-instance-identifiers <value>] \
    [--db-cluster-identifiers <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-proxy-name` | **Yes** | string | -- | Proxy name |
| `--target-group-name` | No | string | `default` | Target group name |
| `--db-instance-identifiers` | No | list | None | DB instance identifiers |
| `--db-cluster-identifiers` | No | list | None | DB cluster identifiers |

**Output Schema:**
```json
{
    "DBProxyTargets": [
        {
            "TargetArn": "string",
            "Endpoint": "string",
            "TrackedClusterId": "string",
            "RdsResourceId": "string",
            "Port": "integer",
            "Type": "RDS_INSTANCE|RDS_SERVERLESS_ENDPOINT|TRACKED_CLUSTER",
            "Role": "READ_WRITE|READ_ONLY|UNKNOWN",
            "TargetHealth": {
                "State": "REGISTERING|AVAILABLE|UNAVAILABLE",
                "Reason": "string",
                "Description": "string"
            }
        }
    ]
}
```

---

### 9.6 `deregister-db-proxy-targets`

Removes targets from a proxy.

```bash
aws rds deregister-db-proxy-targets \
    --db-proxy-name <value> \
    [--target-group-name <value>] \
    [--db-instance-identifiers <value>] \
    [--db-cluster-identifiers <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-proxy-name` | **Yes** | string | -- | Proxy name |
| `--target-group-name` | No | string | `default` | Target group name |
| `--db-instance-identifiers` | No | list | None | Instance identifiers to remove |
| `--db-cluster-identifiers` | No | list | None | Cluster identifiers to remove |

**Output:** None on success.

---

### 9.7 `describe-db-proxy-targets`

Describes proxy targets. **Paginated.**

```bash
aws rds describe-db-proxy-targets \
    --db-proxy-name <value> \
    [--target-group-name <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-proxy-name` | **Yes** | string | -- | Proxy name |
| `--target-group-name` | No | string | all | Target group name |

**Output Schema:**
```json
{
    "Targets": [
        { "...same DBProxyTarget structure..." }
    ],
    "Marker": "string"
}
```

---

### 9.8 `describe-db-proxy-target-groups`

Describes proxy target groups. **Paginated.**

```bash
aws rds describe-db-proxy-target-groups \
    --db-proxy-name <value> \
    [--target-group-name <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-proxy-name` | **Yes** | string | -- | Proxy name |
| `--target-group-name` | No | string | all | Specific target group |

**Output Schema:**
```json
{
    "TargetGroups": [
        {
            "DBProxyName": "string",
            "TargetGroupName": "string",
            "TargetGroupArn": "string",
            "IsDefault": "boolean",
            "Status": "string",
            "ConnectionPoolConfig": {
                "MaxConnectionsPercent": "integer",
                "MaxIdleConnectionsPercent": "integer",
                "ConnectionBorrowTimeout": "integer",
                "SessionPinningFilters": ["string"],
                "InitQuery": "string"
            },
            "CreatedDate": "timestamp",
            "UpdatedDate": "timestamp"
        }
    ],
    "Marker": "string"
}
```

---
