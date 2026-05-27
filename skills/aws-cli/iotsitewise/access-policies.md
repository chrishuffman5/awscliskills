# Access Policies

### 8.1 `create-access-policy`

Creates an access policy granting a user or group access to a portal or project.

**Synopsis:**
```bash
aws iotsitewise create-access-policy \
    --access-policy-identity <value> \
    --access-policy-resource <value> \
    --access-policy-permission <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-policy-identity` | **Yes** | structure | -- | Identity (user, group, iamUser, or iamRole) |
| `--access-policy-resource` | **Yes** | structure | -- | Resource (portal or project) |
| `--access-policy-permission` | **Yes** | string | -- | `ADMINISTRATOR` or `VIEWER` |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Identity Structure (choose one):**
```json
{
    "user": {"id": "string"},
    "group": {"id": "string"},
    "iamUser": {"arn": "string"},
    "iamRole": {"arn": "string"}
}
```

**Resource Structure (choose one):**
```json
{
    "portal": {"id": "string"},
    "project": {"id": "string"}
}
```

**Output Schema:**
```json
{
    "accessPolicyId": "string",
    "accessPolicyArn": "string"
}
```

---

### 8.2 `describe-access-policy`

Describes an access policy.

**Synopsis:**
```bash
aws iotsitewise describe-access-policy \
    --access-policy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-policy-id` | **Yes** | string | -- | Access policy ID (UUID) |

**Output Schema:**
```json
{
    "accessPolicyId": "string",
    "accessPolicyArn": "string",
    "accessPolicyIdentity": {
        "user": {"id": "string"},
        "group": {"id": "string"},
        "iamUser": {"arn": "string"},
        "iamRole": {"arn": "string"}
    },
    "accessPolicyResource": {
        "portal": {"id": "string"},
        "project": {"id": "string"}
    },
    "accessPolicyPermission": "ADMINISTRATOR|VIEWER",
    "accessPolicyCreationDate": "timestamp",
    "accessPolicyLastUpdateDate": "timestamp"
}
```

---

### 8.3 `list-access-policies`

Lists access policies. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-access-policies \
    [--identity-type <value>] \
    [--identity-id <value>] \
    [--resource-type <value>] \
    [--resource-id <value>] \
    [--iam-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-type` | No | string | None | `USER`, `GROUP`, `IAM` |
| `--identity-id` | No | string | None | Identity ID |
| `--resource-type` | No | string | None | `PORTAL` or `PROJECT` |
| `--resource-id` | No | string | None | Resource ID |
| `--iam-arn` | No | string | None | IAM ARN filter |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "accessPolicySummaries": [
        {
            "id": "string",
            "identity": {},
            "resource": {},
            "permission": "ADMINISTRATOR|VIEWER",
            "creationDate": "timestamp",
            "lastUpdateDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.4 `update-access-policy`

Updates an access policy.

**Synopsis:**
```bash
aws iotsitewise update-access-policy \
    --access-policy-id <value> \
    --access-policy-identity <value> \
    --access-policy-resource <value> \
    --access-policy-permission <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-policy-id` | **Yes** | string | -- | Access policy ID |
| `--access-policy-identity` | **Yes** | structure | -- | Updated identity |
| `--access-policy-resource` | **Yes** | structure | -- | Updated resource |
| `--access-policy-permission` | **Yes** | string | -- | `ADMINISTRATOR` or `VIEWER` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 8.5 `delete-access-policy`

Deletes an access policy.

**Synopsis:**
```bash
aws iotsitewise delete-access-policy \
    --access-policy-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-policy-id` | **Yes** | string | -- | Access policy ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None
